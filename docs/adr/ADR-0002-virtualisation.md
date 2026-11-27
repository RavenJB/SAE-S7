# ADR-0002 – Choisir la plateforme de virtualisation

**Statut** : proposé · **Date de proposition** : 2026-11-26

## Contexte et critères décisifs

La maquette doit héberger plusieurs VM, isoler leurs réseaux et se raccorder aux équipements Cisco (R1–R4, S5). L’isolation et la souplesse des VLAN pèsent le plus dans M3. Le choix dépend aussi des ressources et des droits d’administration que l’école fournira.

## Options étudiées

| Option | Atouts | Limites |
| --- | --- | --- |
| Proxmox VE (4,65/5) | Ponts Linux, VLAN 802.1Q et gestion centralisée des VM et de leurs sauvegardes. | Hôte dédié et accès d’administration nécessaires pour ce scénario. Prise en main plus exigeante. |
| VirtualBox (3,90/5) | Exploitation plus simple sur un poste selon M3, réseaux internes et ponts. | Passage du trunk VLAN jusqu’au Catalyst à vérifier avec la carte réseau et l’OS hôte. |
| VMware Workstation Pro (3,90/5) | Hyperviseur de poste de travail sans coût de licence, mieux noté que VirtualBox pour l’isolation et les VLAN. | Moins bien noté que VirtualBox pour les ressources et la simplicité sur poste dans le scénario étudié. |

## Décision proposée et justification

Proposer **Proxmox VE** si l’école fournit un hôte dédié administrable. La matrice privilégie ses ponts, le raccordement VLAN et la gestion de plusieurs VM. Si l’hôte manque, évaluer **VirtualBox** en premier sur poste pour sa simplicité et sa note de ressources. Les deux candidats de repli sont à égalité au score global et le raccordement au Catalyst peut les départager.

## Conséquences

- L’hôte dédié centralise les VM et leurs réseaux. Une panne de cet hôte peut arrêter plusieurs services à la fois.
- Un repli sur poste change le câblage virtuel et les procédures de déploiement. Versionner ces procédures et les configurations pour rejouer la recette après une migration.

## Validation avant arbitrage

Confirmer l’accès à la console, le budget CPU/RAM/disque et les interfaces physiques. Tester le trunk jusqu’au Catalyst et l’isolement entre zones et vis-à-vis des réseaux externes à la maquette. Sans hôte dédié, réexaminer la matrice avec les contraintes du poste réellement disponible.

## Références et décisions liées

- [Matrice M3 de virtualisation](../../livrables/M3-choix-solutions.md#choix-2--virtualisation--proxmox-ve-virtualbox-vmware-workstation-pro).
- [ADR-0001 – Pare-feu](ADR-0001-pare-feu.md) pour les interfaces et VLAN et [ADR-0003 – Sauvegarde](ADR-0003-nas-sauvegarde.md) pour le stockage dédié.
- [Guide Proxmox VE](https://pve.proxmox.com/pve-docs/pve-admin-guide.pdf), [manuel VirtualBox](https://download.virtualbox.org/virtualbox/7.2.10/UserManual.pdf) et [licence de VMware Workstation Pro](https://blogs.vmware.com/cloud-foundation/2024/11/11/vmware-fusion-and-workstation-are-now-free-for-all-users/).
