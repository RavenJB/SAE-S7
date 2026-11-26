# ADR-0005 – Choisir la messagerie de la maquette

**Statut** : proposé · **Date de proposition** : 2026-11-26

## Contexte et critères décisifs

Chaque salarié doit pouvoir échanger du courrier avec une adresse `prenom.nom@valdore-services.fr` via un client ou le webmail, y compris avec un correspondant sur l’Internet simulé (V3). Les critères les plus discriminants sont les ressources, l’exploitation et l’intégration à l’AD. L’authentification via l’annuaire est souhaitable (V10) et les logiciels déployés doivent rester maintenus (Q6).

## Options étudiées

| Option | Atouts | Limites |
| --- | --- | --- |
| Modoboa (4,25/5, notation initiale) | Console d’administration intégrée et authentification LDAP documentée. | La documentation courante indique 4 CPU, 4 Go de RAM et 10 Go de disque. Le cycle de vie des comptes locaux doit être vérifié avec AD. |
| Mailu (4,15/5, note établie sur 2.0) | Suite conteneurisée, bien notée pour les ressources dans M3. La branche stable documentée est 2024.06. | Réévaluer la note de maintenance et confirmer l’intégration AD sur cette branche. |
| mailcow (4,10/5) | Intégration LDAP/AD et sauvegarde documentées. | La configuration par défaut demande au moins 6 Gio de RAM et 1 Gio de swap. |

## Décision proposée et justification

Évaluer **Modoboa** en premier pour son administration intégrée et son authentification LDAP documentée. Son avance initiale est de 0,10 point. Une hausse d’un point de la note de maintenance de Mailu suffirait à l’annuler, à notes égales par ailleurs. Les prérequis révisés de Modoboa peuvent aussi peser sur la note de ressources. L’arbitrage dépend de la mise à jour de ces critères et des essais sur la maquette.

## Conséquences

- Prévoir une procédure de création, modification et désactivation des boîtes. L’authentification LDAP et la synchronisation des comptes sont deux fonctions distinctes. La synchronisation optionnelle est documentée avec OpenLDAP. Son comportement avec Active Directory reste à vérifier.
- Maintenir le courrier dans les réseaux autorisés de la maquette, prévoir TLS et des exports restaurables. Un changement de solution peut imposer une reprise des boîtes et de la configuration de messagerie.

## Validation avant arbitrage

Revoir les notes de ressources et de maintenance avec les versions évaluées. Tester SMTP interne et vers un correspondant externe simulé, IMAP, webmail, TLS et restauration d’une boîte. Pour l’intégration AD, vérifier la connexion LDAP chiffrée et le comportement après modification ou désactivation du compte.

## Références et décisions liées

- [Matrice M3 de messagerie](../missions/M3-choix-solutions.md#choix-5--messagerie--modoboa-mailu-mailcow) et [dossier M2, R23 à R25](../missions/M2-dossier-documentaire.md#messagerie).
- [ADR-0001 – Pare-feu](ADR-0001-pare-feu.md) pour les flux autorisés et [ADR-0003 – Sauvegarde](ADR-0003-nas-sauvegarde.md) pour les exports et la restauration.
- [Prérequis Modoboa](https://modoboa.readthedocs.io/en/latest/installation/requirements.html), [configuration LDAP Modoboa](https://modoboa.readthedocs.io/en/latest/configuration.html#ldap), [version stable Mailu](https://mailu.io/2024.06/setup.html#pick-a-mailu-version) et [prérequis mailcow](https://docs.mailcow.email/getstarted/prerequisite-system/).
