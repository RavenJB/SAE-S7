# ADR-0004 – Supervision

Statut : proposé.
Date : 2026-11-26.

## Contexte

La maquette doit superviser équipements Cisco, pare-feu, serveurs Windows/Linux et services, conserver des journaux exploitables et produire des alertes en cas d’indisponibilité. L’administration est assurée par une seule personne dans le contexte fictif.

## Décision proposée

Retenir Zabbix 8.0 LTS avec SNMP pour le réseau, agent pour les serveurs, sondes de service et seuils adaptés à la maquette. Le cycle de vie officiel annonce une prise en charge limitée jusqu’au 30 novembre 2031.

## Alternatives

Prometheus avec Grafana : robuste et léger, avec modèle de métriques et alertes composables, mais les exporters et l’assemblage des composants demandent du temps supplémentaire.

Nagios Core : solution libre et extensible par plugins, mais la configuration des plugins, des vues et des alertes est davantage manuelle.

## Conséquences

Installer le serveur sur un Linux maintenu et sauvegarder sa base de données et sa configuration. Restreindre SNMPv3 et les flux d’agents au VLAN de supervision. Revoir la version au moment du déploiement si le calendrier change.

## Sources

https://www.zabbix.com/documentation/8.0/en/manual/introduction
https://www.zabbix.com/documentation/8.0/en/manual/config/items/itemtypes/snmp
https://www.zabbix.com/life_cycle_and_release_policy
https://prometheus.io/docs/introduction/overview/
https://github.com/NagiosEnterprises/nagioscore
