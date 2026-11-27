# ADR-0001 – Choisir le pare-feu de la maquette

**Statut** : proposé · **Date de proposition** : 2026-11-26

## Contexte et critères décisifs

Le cahier des charges limite le choix à OPNsense et pfSense CE, sans achat. Le pare-feu doit cloisonner les VLAN avec le Catalyst 3750, publier les seuls services prévus, journaliser les accès et fournir OpenVPN aux télétravailleurs (R4–R6, Q1–Q4, Q7). Les ressources allouables restent à confirmer.

## Options étudiées

| Option | Atouts | Limites |
| --- | --- | --- |
| pfSense CE (4,65/5) | Filtrage, NAT, OpenVPN, VLAN et documentation d’exploitation détaillée. | Disponibilité de l’image CE et dimensionnement à vérifier. Netgate publie un minimum d’installation de 1 Go de RAM et 8 Go de disque. |
| OPNsense (4,60/5) | Même couverture fonctionnelle attendue, historique des changements et meilleure note de sécurité et maintenance dans M3. | Les 4 Go de RAM indiqués par OPNsense correspondent au profil raisonnable pour l’ensemble des fonctions standard. |

## Décision proposée et justification

Évaluer **pfSense CE** en premier. La matrice lui donne 0,05 point d’avance grâce aux notes de documentation et de ressources, malgré la meilleure note de maintenance d’OPNsense. Les chiffres éditeurs portent sur des périmètres différents. Le gain de ressources reste une hypothèse à vérifier à périmètre égal.

## Conséquences

- Dans l’architecture proposée, centraliser le filtrage entre zones sur le pare-feu et documenter les flux autorisés. Prévoir l’administration nominative, la conservation des journaux et la sauvegarde de la configuration.
- Un seul pare-feu porte le routage inter-VLAN et le VPN dans la maquette. Son indisponibilité coupe ces accès et un changement de produit impose de transposer les règles et de rejouer la recette.

## Validation avant arbitrage

Vérifier l’image CE, le trunk VLAN, l’isolation des zones, l’export des journaux et les droits du télétravailleur. Tester le VPN avec les ressources disponibles, puis mesurer son débit en charge dans M4. Si pfSense CE échoue à l’essai, évaluer OPNsense sur les mêmes critères avant de proposer la bascule.

## Références et décisions liées

- [Matrice M3 du pare-feu](../../livrables/M3-choix-solutions.md#choix-1--pare-feu--opnsense-ou-pfsense-ce) et [architecture réseau proposée](../../livrables/M3-choix-solutions.md#proposition-darchitecture-réseau-liée-à-ces-choix).
- [ADR-0002 – Virtualisation](ADR-0002-virtualisation.md) pour le raccordement des VLAN et [ADR-0004 – Supervision](ADR-0004-supervision.md) pour le suivi du pare-feu.
- [Dimensionnement pfSense](https://docs.netgate.com/pfsense/en/latest/hardware/size.html), [minimums pfSense](https://docs.netgate.com/pfsense/en/latest/hardware/minimum-requirements.html), [dimensionnement OPNsense](https://docs.opnsense.org/manual/hardware.html) et [VPN OPNsense](https://docs.opnsense.org/manual/vpnet.html).
