# ADR-0003 – Choisir le NAS et la solution de sauvegarde

**Statut** : proposé · **Date de proposition** : 2026-11-26

## Contexte et critères décisifs

Sauvegarder chaque nuit l’annuaire, les dossiers, les bases et la messagerie sur un NAS dédié (V8). La perte admissible est limitée à la journée de travail précédente (§3.3). La protection des copies contre l’effacement ou le chiffrement (Q8), la restauration et le budget de ressources guident le choix.

## Options étudiées

| Option | Atouts | Limites |
| --- | --- | --- |
| OpenMediaVault + Restic/rest-server (4,45/5) | Administration du NAS par interface, sauvegarde chiffrée Windows/Linux et accès en ajout seul au dépôt. | Le dépôt, ses accès et sa maintenance sont à exploiter séparément du NAS. |
| TrueNAS CE (4,25/5) | SMB, intégration AD, instantanés ZFS et réplication. | Le guide demande au moins 8 Go de RAM et des supports distincts pour démarrer et stocker les données. La protection des copies dépend des droits sur les instantanés et les répliques. |
| Debian + Restic/rest-server (4,10/5) | Même protection de dépôt dans la matrice et meilleure note de ressources. | Plus de configuration et d’exploitation manuelles pour l’administrateur. |

## Décision proposée et justification

Proposer **OpenMediaVault** comme NAS et **Restic avec rest-server en mode append-only** pour le dépôt chiffré. Cette combinaison obtient la meilleure note pondérée en conciliant protection, ressources et simplicité. Le service rest-server tournerait dans un conteneur ou une VM Linux dédiée avec un espace limité sur le NAS. BorgBackup a aussi été documenté en M2 (R18). Restic est privilégié pour ses clients Windows et Linux et son usage de VSS sous Windows.

## Conséquences

- Le compte de dépôt peut ajouter des copies. La maintenance exige un accès distinct réservé à l’administration. Prévoir des quotas, une alerte d’espace, une copie de récupération de la clé et des contrôles d’intégrité. La panne du NAS et la compromission de son administrateur restent des risques. Ajouter une copie hors ligne si le matériel le permet.
- Sauvegarder l’état système du contrôleur de domaine avec Windows Server Backup et protéger cet export sur le NAS avec des droits séparés. Préparer des exports cohérents des bases et de la messagerie et les inclure aux sauvegardes nocturnes.

## Validation avant arbitrage

Confirmer le stockage disponible, le temps de sauvegarde sur la plage 20 h–7 h et le refus de suppression via le compte de dépôt. En recette, restaurer un dossier et un compte AD (§4.4). Chronométrer aussi la restauration complète d’un serveur en M8 et la comparer au délai de reprise du §3.3.

## Références et décisions liées

- [Matrice M3 du NAS et des sauvegardes](../missions/M3-choix-solutions.md#choix-3--nas-et-sauvegarde--truenas-ce-openmediavault-avec-restic-debian-avec-restic) et [dossier M2, R13 à R19](../missions/M2-dossier-documentaire.md#stockage-et-sauvegardes).
- [ADR-0002 – Virtualisation](ADR-0002-virtualisation.md) pour le stockage et [ADR-0005 – Messagerie](ADR-0005-messagerie.md) pour les boîtes à restaurer.
- [Maintenance Restic en mode append-only](https://restic.readthedocs.io/en/stable/060_forget.html#security-considerations-in-append-only-mode) et [sauvegarde de l’état système AD](https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-backing-up-system-state).
