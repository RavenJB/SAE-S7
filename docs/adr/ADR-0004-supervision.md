# ADR-0004 – Choisir la solution de supervision

**Statut** : proposé · **Date de proposition** : 2026-11-26

## Contexte et critères décisifs

Un seul administrateur doit suivre la disponibilité des équipements Cisco, du pare-feu, des serveurs Windows/Linux et des services, avec alertes (V9). L’intégration SNMP et agents, la charge d’exploitation et le support de la version (Q6) départagent les options.

## Options étudiées

| Option | Atouts | Limites |
| --- | --- | --- |
| Zabbix 8.0 LTS (4,80/5) | SNMP, agents, sondes, seuils, tableaux de bord et alertes dans le même outil. | Serveur et base de données à dimensionner et maintenir. |
| Prometheus + Grafana (3,95/5) | Collecte de métriques modulable et meilleure note de ressources dans M3. | Exporters et Alertmanager à intégrer avec Grafana pour couvrir le périmètre. |
| Nagios Core (3,70/5) | Contrôles de disponibilité extensibles par plugins. | Plugins, seuils et vues demandent davantage de configuration manuelle. |

## Décision proposée et justification

Proposer **Zabbix 8.0 LTS**. La couverture du parc et l’exploitation par une seule personne compensent la charge du serveur et de sa base. L’éditeur indique un support complet jusqu’au 30 novembre 2029 et un support limité jusqu’au 30 novembre 2031.

## Conséquences

- Prévoir les agents Windows/Linux, le suivi SNMPv3 sur les équipements compatibles et des sondes pour les services. Restreindre les flux de collecte aux sources et destinations nécessaires.
- Sauvegarder la base et la configuration. Dimensionner la rétention des métriques pour M4 et M7. La conservation des journaux (Q7) reste à traiter dans l’exploitation, avec centralisation souhaitable (Q9).

## Validation avant arbitrage

Vérifier la collecte sur les équipements prêtés et les serveurs représentatifs, les ressources de la VM et la version maintenue disponible. Provoquer l’arrêt contrôlé d’un service de la maquette et vérifier l’alerte et le retour à l’état normal.

## Références et décisions liées

- [Matrice M3 de supervision](../../livrables/M3-choix-solutions.md#choix-4--supervision--zabbix-prometheus-avec-grafana-nagios-core) et [dossier M2, R20 à R22](../../livrables/M2-dossier-documentaire.md#supervision).
- [ADR-0001 – Pare-feu](ADR-0001-pare-feu.md) pour les flux de collecte et [ADR-0003 – Sauvegarde](ADR-0003-nas-sauvegarde.md) pour la base et la configuration.
- [Politique de support Zabbix](https://www.zabbix.com/life_cycle_and_release_policy) et [documentation SNMP](https://www.zabbix.com/documentation/8.0/en/manual/config/items/itemtypes/snmp).
