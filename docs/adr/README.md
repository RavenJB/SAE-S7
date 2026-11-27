# Décisions d’architecture

Les ADR documentent les décisions de la maquette Valdoré Services. Les critères pondérés et les notes détaillées figurent dans le [comparatif M3](../../livrables/M3-choix-solutions.md). L’équipe arbitre les propositions dans le cadre de la [mission M3](https://github.com/RavenJB/SAE-S7/issues/3).

| ADR | Proposition | Statut | Date de proposition |
| --- | --- | --- | --- |
| [0001 – Pare-feu](ADR-0001-pare-feu.md) | Évaluer pfSense CE en premier, avec OPNsense en alternative. | Proposé | 2026-11-26 |
| [0002 – Virtualisation](ADR-0002-virtualisation.md) | Proxmox VE si l’école fournit un hôte dédié, VirtualBox en premier essai sur poste. | Proposé | 2026-11-26 |
| [0003 – NAS et sauvegarde](ADR-0003-nas-sauvegarde.md) | OpenMediaVault avec Restic et rest-server en mode append-only. | Proposé | 2026-11-26 |
| [0004 – Supervision](ADR-0004-supervision.md) | Zabbix 8.0 LTS. | Proposé | 2026-11-26 |
| [0005 – Messagerie](ADR-0005-messagerie.md) | Évaluer Modoboa en premier après mise à jour de la comparaison. | Proposé | 2026-11-26 |

Pour proposer une décision, copier le [modèle d’ADR](template.md) dans `ADR-NNNN-sujet.md` avec le prochain numéro disponible, puis ajouter l’ADR à l’index. Après l’arbitrage, reporter le statut dans les deux fichiers. Si une décision acceptée doit être remplacée, rédiger un nouvel ADR, relier les deux et marquer l’ancien **Remplacé**.
