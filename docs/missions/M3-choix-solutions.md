# M3 – Comparer et sélectionner les solutions

État : proposition initiale à valider avec l’équipe et l’équipe enseignante.
Date de recherche : 26 novembre 2026.
Périmètre : choix de solutions pour la maquette Valdoré Services, en tenant compte du brief SAE et de ses exigences R, S, V, Q et T.

## Contexte et hypothèses

Valdoré Services compte 82 salariés, dont environ 35 télétravailleurs simultanés, et prévoit une croissance de 25 %. La maquette doit rester isolée, intégrer les équipements Cisco Catalyst 3750 et routeur fournis, publier seulement les services requis et ne nécessiter aucun achat. Les solutions retenues doivent être libres ou utiliser une licence déjà détenue. Le pare-feu doit fournir OpenVPN. Le domaine interne, les machines, leur mémoire, le stockage et le matériel réellement prêté ne sont pas encore confirmés.

Les notes ci-dessous sont une première appréciation de l’équipe, fondée sur la documentation éditeur consultée à la date indiquée. Elles ne remplacent pas une validation sur le matériel prêté. Les besoins de mémoire annoncés par les éditeurs ne sont pas directement comparables lorsque l’un indique un minimum et l’autre un minimum pour un jeu de fonctions complet.

## Méthode

Échelle : 1 = faible adéquation, 2 = limitée, 3 = acceptable, 4 = bonne, 5 = très bonne. Pour chaque critère, la note est multipliée par son poids. Le total est la somme pondérée divisée par 100, sur 5. Les critères et leurs poids sont fixés avant les notes.

Les critères couvrent l’adéquation aux besoins, les contraintes de licence et de budget, la sécurité et le support, l’intégration aux systèmes et au Cisco, les ressources, l’exploitation par un administrateur unique et la documentation. Les matrices propres à chaque choix ajustent le poids de ces critères.

## Choix 1 – Pare-feu : OPNsense ou pfSense CE

Exigences principalement concernées : R4, R5, R6, Q1, Q2, Q3, Q4, Q7, T1.

Critères et poids : couverture du besoin pare-feu/OpenVPN/NAT/filtrage 30 ; coût et respect des contraintes 15 ; sécurité et maintenance 15 ; VLAN et compatibilité Cisco 10 ; ressources nécessaires 10 ; facilité d’exploitation 10 ; documentation 10.

| Critère | Poids | OPNsense | pfSense CE |
|---|---:|---:|---:|
| Couverture pare-feu, OpenVPN, NAT, filtrage | 30 | 5 | 5 |
| Coût et contraintes | 15 | 5 | 5 |
| Sécurité et maintenance | 15 | 5 | 4 |
| VLAN et compatibilité Cisco | 10 | 5 | 5 |
| Ressources | 10 | 3 | 4 |
| Exploitation par un administrateur | 10 | 4 | 4 |
| Documentation | 10 | 4 | 5 |
| Total pondéré / 5 | 100 | 4,60 | 4,65 |

Décision proposée : évaluer pfSense CE en premier, sous réserve de confirmer l’image disponible. Les deux options couvrent OpenVPN, NAT, filtrage stateful, VLAN et journaux. pfSense CE a 0,05 point d’avance grâce aux notes de documentation et de ressources. Le gain de ressources reste à mesurer à périmètre égal sur la VM de pare-feu. OPNsense reste l’alternative à évaluer si pfSense CE échoue à l’essai.

Solutions écartées : aucune des deux solutions autorisées par le brief n’est écartée à ce stade. Les offres payantes et les VPN tiers sont hors périmètre.

À vérifier : mémoire réellement allouable ; version CE exacte ; support des interfaces virtuelles et du trunk VLAN ; fonctionnement d’OpenVPN avec le plan d’adressage et les règles de moindre privilège ; collecte et export des journaux.

## Choix 2 – Virtualisation : Proxmox VE, VirtualBox, VMware Workstation Pro

Exigences principalement concernées : R1–R4, S5, T1, T2. Le brief autorise explicitement ces trois plateformes et demande des réseaux virtuels isolés.

Critères et poids : adéquation à une maquette multi-VM 20 ; isolation et flexibilité VLAN 25 ; coût/licence 10 ; ressources/hôte 15 ; simplicité pour un administrateur 10 ; documentation et maintenance 10 ; adéquation au matériel scolaire qui reste à confirmer 10.

| Critère | Poids | Proxmox VE | VirtualBox | VMware Workstation Pro |
|---|---:|---:|---:|---:|
| Maquette multi-VM | 20 | 5 | 4 | 4 |
| Réseaux isolés, ponts, VLAN | 25 | 5 | 3 | 4 |
| Coût/licence dans le cadre SAE | 10 | 5 | 5 | 5 |
| Ressources et utilisation de l’hôte | 15 | 4 | 5 | 4 |
| Simplicité pour l’administrateur | 10 | 3 | 5 | 4 |
| Documentation et maintenance | 10 | 5 | 4 | 4 |
| Compatibilité avec un serveur dédié d’école | 10 | 5 | 2 | 2 |
| Total pondéré / 5 | 100 | 4,65 | 3,90 | 3,90 |

Décision proposée : Proxmox VE si l’équipe enseignante fournit un serveur dédié et autorise son administration. Ses ponts Linux, VLAN 802.1Q et sauvegardes conviennent à une maquette avec plusieurs zones et des équipements physiques. Sur poste de travail, VirtualBox et VMware Workstation Pro sont à égalité. Évaluer VirtualBox en premier pour ses notes de ressources et de simplicité, puis vérifier le passage du trunk jusqu’au Catalyst. VMware obtient une meilleure note d’isolation et de VLAN et reste candidat si le raccordement impose de revoir le choix.

Solutions écartées : aucune exclusion définitive ; le score Proxmox dépend de la disponibilité de l’hôte. Cette décision est donc conditionnelle et ne doit pas être présentée comme confirmée tant que l’affectation des ressources scolaires n’est pas connue.

À vérifier : compatibilité du serveur fourni, accès console, nombre de NIC physiques, mode de passage des VLAN, capacité RAM/CPU/disque et possibilité de relier un bridge à l’infrastructure Cisco sans connecter la maquette à un réseau non autorisé.

## Choix 3 – NAS et sauvegarde : TrueNAS CE, OpenMediaVault avec Restic, Debian avec Restic

Exigences principalement concernées : V2, V8, Q1, Q7, Q8, T1, T2. La restauration doit être démontrée. La protection contre l’effacement ne peut pas reposer uniquement sur un instantané accessible au même compte administrateur.

Critères et poids : adéquation NAS et sauvegarde/restauration 20 ; protection contre effacement/chiffrement 20 ; chiffrement et contrôle d’accès 15 ; ressources 15 ; simplicité d’exploitation 10 ; intégration Windows/Linux 10 ; documentation et maintenance 10.

| Critère | Poids | TrueNAS CE | OpenMediaVault + Restic/rest-server | Debian + Restic/rest-server |
|---|---:|---:|---:|---:|
| NAS et sauvegarde/restauration | 20 | 5 | 4 | 3 |
| Résistance à l’effacement ou au chiffrement par un tiers | 20 | 4 | 5 | 5 |
| Chiffrement des données et contrôle d’accès | 15 | 5 | 5 | 5 |
| Ressources | 15 | 2 | 4 | 5 |
| Simplicité d’exploitation | 10 | 4 | 4 | 2 |
| Windows/Linux | 10 | 5 | 5 | 4 |
| Documentation/maintenance | 10 | 5 | 4 | 4 |
| Total pondéré / 5 | 100 | 4,25 | 4,45 | 4,10 |

Décision proposée : OpenMediaVault pour le service NAS, avec Restic sur Windows/Linux et rest-server en mode append-only pour le dépôt de sauvegarde. Le service Rest Server sera isolé dans un conteneur ou une VM Linux dédiée et écrira dans un espace NAS limité ; on évite ainsi d’ajouter ses dépendances directement au système administré par OpenMediaVault. Restic chiffre les dépôts, déduplique les données et peut utiliser les instantanés VSS de Windows. Rest-server en mode append-only interdit à un client de supprimer ou modifier les sauvegardes existantes. La maintenance avec droits de suppression doit utiliser un compte distinct, réservé à l’administrateur.

Solutions écartées : TrueNAS CE reste une bonne option si l’école fournit au moins 8 Go de RAM et un stockage convenable ; la configuration ZFS et les instantanés sont utiles, mais son minimum matériel documenté est plus lourd pour la maquette. Debian + Restic est économe en ressources, mais demande davantage d’administration manuelle qu’OpenMediaVault. Aucune des options ne remplace une copie isolée ou hors ligne si le matériel est disponible.

Limites et précautions : append-only n’est pas une sauvegarde hors ligne ni une immutabilité absolue. Un client compromis pourrait remplir le stockage de données inutiles ; il faut fixer un quota, surveiller la capacité, séparer la clé d’administration de maintenance, conserver une copie de récupération de la clé Restic et programmer `check`/tests de restauration. Pour Active Directory, Restic ne remplace pas une sauvegarde cohérente de l’état du système : la proposition utilise Windows Server Backup pour l’état du système du contrôleur de domaine et prévoit de protéger sa destination par les droits du NAS, puis d’exercer une restauration conforme à la procédure Microsoft. Les bases applicatives et la messagerie devront aussi être exportées avec leurs outils cohérents avant le transfert des fichiers ; une simple copie à chaud ne suffit pas à démontrer leur restaurabilité.

## Choix 4 – Supervision : Zabbix, Prometheus avec Grafana, Nagios Core

Exigences principalement concernées : V9, Q7, Q9, T1. Les besoins incluent la disponibilité, les métriques système, SNMP pour les équipements, les seuils et les alertes.

Critères et poids : couverture équipement/service/alertes 25 ; SNMP et systèmes Windows/Linux 20 ; ressources et architecture 10 ; simplicité pour un administrateur 15 ; sécurité, support et maintenance 10 ; coût/licence 10 ; documentation 10.

| Critère | Poids | Zabbix 8.0 LTS | Prometheus + Grafana | Nagios Core 4.x |
|---|---:|---:|---:|---:|
| Couverture et alertes | 25 | 5 | 4 | 4 |
| SNMP, Windows, Linux | 20 | 5 | 3 | 4 |
| Ressources/architecture | 10 | 3 | 5 | 4 |
| Exploitation par un administrateur | 15 | 5 | 3 | 2 |
| Sécurité, support, maintenance | 10 | 5 | 4 | 3 |
| Coût/licence | 10 | 5 | 5 | 5 |
| Documentation | 10 | 5 | 5 | 4 |
| Total pondéré / 5 | 100 | 4,80 | 3,95 | 3,70 |

Décision proposée : Zabbix 8.0 LTS. Il regroupe agents Windows/Linux, collecte SNMP du Catalyst et du routeur, seuils, déclencheurs, tableaux et notifications dans une même solution. La politique publiée indique un support complet jusqu’au 30 novembre 2029 et un support limité jusqu’au 30 novembre 2031 pour Zabbix 8.0 LTS, sorti le 5 novembre 2026. Ce cycle est adapté à la durée du projet ; la version retenue au déploiement devra être revérifiée.

Solutions écartées : Prometheus avec Grafana est puissant et peu dépendant, mais l’assemblage des exporters, des règles, d’Alertmanager et de Grafana demande plus d’intégration pour un seul administrateur et pour un parc mixte. Nagios Core est léger et extensible, mais les seuils, plugins, vues et configuration nécessitent davantage d’assemblage. Les deux restent possibles si les ressources ou la familiarité de l’équipe changent l’évaluation.

## Choix 5 – Messagerie : Modoboa, Mailu, mailcow

Exigences principalement concernées : V3, Q4, Q5, Q6, Q7, V8. Le courrier doit être accessible par client et webmail, et les échanges de maquette doivent simuler l’extérieur sans ouvrir le réseau isolé vers Internet.

Critères et poids : SMTP/IMAP/webmail/TLS 20 ; compatibilité avec l’annuaire 15 ; ressources 25 ; simplicité d’exploitation 15 ; maintenance/version documentée 10 ; coût/licence 5 ; documentation et sauvegarde 10. La mémoire reçoit le poids principal parce que les ressources de la maquette sont limitées.

| Critère | Poids | Modoboa | Mailu 2.0 (notation initiale) | mailcow |
|---|---:|---:|---:|---:|
| SMTP, IMAP, webmail, TLS | 20 | 5 | 5 | 5 |
| AD/LDAP | 15 | 4 | 3 | 5 |
| Ressources | 25 | 4 | 5 | 2 |
| Exploitation | 15 | 4 | 4 | 4 |
| Maintenance/version | 10 | 4 | 2 | 5 |
| Coût/licence | 5 | 5 | 5 | 5 |
| Documentation/sauvegarde | 10 | 4 | 4 | 5 |
| Total pondéré / 5 | 100 | 4,25 | 4,15 | 4,10 |

Décision proposée : évaluer Modoboa en premier pour l’administration intégrée et l’authentification LDAP documentée. Tester l’intégration à Active Directory et documenter la procédure de gestion des comptes. La documentation courante indique 4 CPU, 4 Go de RAM et 10 Go de disque, contre 2 CPU et 2 Go de RAM dans la documentation consultée pour la notation initiale (voir R23). La synchronisation LDAP est optionnelle et documentée avec OpenLDAP. La note de ressources de Modoboa doit être revue avec la version évaluée.

Alternatives : la branche stable documentée de Mailu est 2024.06 (R24). Vérifier les ressources et l’intégration AD sur cette branche et réévaluer la note de maintenance qui portait sur 2.0. À notes égales par ailleurs, un point de plus sur ce critère mettrait Mailu à égalité avec Modoboa. mailcow prend en charge LDAP/AD et propose des fonctions de sécurité et de sauvegarde. Sa configuration par défaut demande au moins 6 Gio de RAM, 1 Gio de swap et 20 Gio de disque hors messages.

Limite : aucun de ces logiciels ne garantit la remise de courrier vers les grands fournisseurs depuis le réseau simulé. La recette doit prouver la livraison entre comptes internes et vers un correspondant externe simulé. Elle ne doit pas supposer une connectivité SMTP réelle à Internet.

## Proposition d’architecture réseau liée à ces choix

Le plan proposé utilise des plages RFC1918 et réserve une plage /24 aux postes, capable d’accueillir au moins 120 équipements. Les zones proposées sont : utilisateurs `10.20.10.0/24`, serveurs internes `10.20.20.0/24`, DMZ `10.20.30.0/27`, administration `10.20.40.0/27`, sauvegarde/NAS `10.20.50.0/27`, réseau de gestion des équipements `10.20.60.0/27`. Ces adresses sont des propositions et devront être vérifiées contre les contraintes de l’environnement de séance.

Le Catalyst 3750 transporte les VLAN en niveau 2. Le pare-feu assure le routage entre zones et applique la politique inter-VLAN, afin que les flux passent par un point de filtrage unique. L’administration du commutateur et des serveurs est réservée au VLAN de gestion. Les serveurs exposés sont isolés dans la DMZ. Si la maquette impose le routage L3 sur le Catalyst, ses ACL doivent être documentées et les flux vers la DMZ et les zones sensibles doivent rester filtrés par le pare-feu ; ne pas activer le routage inter-VLAN sans justification et scénario de validation.

Ce schéma est une proposition d’étude, pas un plan de configuration : les interfaces, passerelles, ports de trunk, plages publiques et règles détaillées restent à confirmer en fonction du routeur et de l’équipement prêtés.

## Résumé des choix proposés

- [Pare-feu](../adr/ADR-0001-pare-feu.md) — Évaluer pfSense CE en premier, puis OPNsense si besoin.
- [Virtualisation](../adr/ADR-0002-virtualisation.md) — Proxmox VE si l’école fournit un hôte dédié, VirtualBox en premier essai sur poste.
- [NAS et sauvegarde](../adr/ADR-0003-nas-sauvegarde.md) — OpenMediaVault avec Restic et rest-server en mode append-only.
- [Supervision](../adr/ADR-0004-supervision.md) — Zabbix 8.0 LTS.
- [Messagerie](../adr/ADR-0005-messagerie.md) — Évaluer Modoboa en premier, puis arbitrer après mise à jour de la comparaison et essai LDAP.

## Présentation au client

La revue intermédiaire de dix minutes pourra suivre cet ordre : contexte et critères pondérés ; cinq décisions avec leur alternative principale ; coûts et ressources ; plan VLAN ; hypothèses à confirmer et décisions demandées à l’équipe enseignante. Les validations encore nécessaires sont les ressources CPU/RAM/disque, l’hôte de virtualisation, l’affectation des interfaces réseau, le système de fichiers ou NAS disponible, et le choix de messagerie accepté pour la maquette.

## Sources de cette première analyse

Les métadonnées et apports commentés sont consignés dans [le dossier M2](M2-dossier-documentaire.md). Principales sources consultées : documentations officielles OPNsense et Netgate ; guides Proxmox, Oracle VirtualBox et Broadcom VMware ; documentations TrueNAS, OpenMediaVault, Restic et rest-server ; politiques de version Zabbix, documentation Prometheus et Nagios ; documentation Modoboa, Mailu et mailcow ; guide Catalyst 3750 de Cisco ; recommandations ANSSI et Microsoft pour Active Directory.
