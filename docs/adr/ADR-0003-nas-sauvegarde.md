# ADR-0003 – NAS et logiciel de sauvegarde

Statut : proposé, à confirmer selon l’espace de stockage disponible.
Date : 2026-11-26.

## Contexte

Les données critiques doivent être sauvegardées chaque nuit sur un NAS et une restauration de fichiers et de compte Active Directory doit être démontrée. Le RPO maximal est la journée de travail précédente. Les sauvegardes doivent résister à la suppression ou au chiffrement par un compte compromis.

## Décision proposée

Utiliser OpenMediaVault comme cible NAS et Restic pour créer des dépôts chiffrés depuis les postes/serveurs Linux et Windows. Héberger rest-server en mode append-only dans un conteneur ou une VM Linux dédiée qui écrit dans un espace NAS limité ; utiliser un compte de sauvegarde restreint, réserver les opérations de suppression/maintenance à un autre compte et surveiller les quotas. Pour Active Directory, utiliser Windows Server Backup pour le backup cohérent de l’état du système, puis protéger sa destination sur le NAS par des droits séparés. Les services de base de données et de messagerie devront exporter leurs données de façon cohérente avant la sauvegarde des fichiers.

## Alternatives

TrueNAS Community Edition fournit SMB, intégration AD, ZFS, snapshots et réplication, mais son guide de matériel demande au moins 8 Go de RAM et un support de démarrage et stockage dédiés.

Debian avec Restic/rest-server est plus minimal et peu consommateur, mais demande davantage de configuration manuelle qu’un NAS administré par interface.

BorgBackup offre également chiffrement et append-only, mais le scénario retenu utilise Restic pour sauvegarder directement Windows et exploiter VSS.

## Conséquences

Append-only empêche la suppression/modification à travers le compte de dépôt, mais ne protège pas contre le remplissage du stockage, la compromission de l’administration du NAS, la panne du support ou la perte de la clé. Quotas, séparation d’identifiants, sauvegarde de la clé, contrôle d’intégrité et exercices de restauration sont obligatoires. Une copie hors ligne sera ajoutée si le matériel fourni le permet. Restic ne remplace pas Windows Server Backup pour restaurer l’état système du contrôleur de domaine.

## Sources

https://docs.openmediavault.org/en/stable/prerequisites.html
https://restic.readthedocs.io/en/stable/040_backup.html
https://github.com/restic/rest-server
https://www.truenas.com/docs/scale/gettingstarted/tnhardwareguide/
https://borgbackup.readthedocs.io/en/stable/usage/init.html
https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-backing-up-system-state
