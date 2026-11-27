# M2 – Constituer un dossier documentaire

Première version du 26 novembre 2026, mise à jour le 27 novembre 2026 à partir de la [fiche du premier test M10](M10-premier-test-maquette.md).

Ce dossier rassemble les sources utilisées pour le [comparatif M3](M3-choix-solutions.md) et la préparation de la maquette.

## Méthode de recherche

Les recherches ont privilégié les documentations des éditeurs/projets, les standards et les publications de l’ANSSI. Les documents sont classés par domaine et les exigences concernées sont notées pour faciliter leur réutilisation dans M3, l’architecture et les procédures. La date d’accès sert de repère, car plusieurs documentations sont mises à jour en continu.

| Domaine | Requêtes en français | Requêtes en anglais |
| --- | --- | --- |
| Réseau et virtualisation | `pare-feu OPNsense pfSense OpenVPN ressources` · `virtualisation Proxmox VirtualBox VLAN réseaux isolés` · `Netgate pfSense DHCPv4 passerelle serveur DNS interface administration règle anti-verrouillage` | `OPNsense pfSense OpenVPN hardware requirements` · `Proxmox VirtualBox VMware virtual networking VLAN` · `Netgate pfSense DHCPv4 DNS servers gateway admin access anti-lockout` |
| Annuaire | `Microsoft Active Directory ports pare-feu joindre un ordinateur au domaine Windows 11 Resolve-DnsName` | `Microsoft learn configure firewall Active Directory join computer domain Resolve-DnsName Windows lifecycle` |
| Messagerie | `messagerie open source IMAP SMTP webmail LDAP` | `Modoboa LDAP requirements` · `Mailu mailcow resource requirements` |
| Sauvegarde | `NAS TrueNAS OpenMediaVault sauvegarde chiffrée append-only` | `NAS immutable snapshots backup` · `restic Windows VSS append-only REST server` |
| Supervision | `supervision Zabbix SNMP alertes Windows Linux` | `Zabbix LTS lifecycle SNMP` · `Prometheus alerting` |
| Sécurité | `sécurisation Active Directory ANSSI hygiène informatique` | `ANSSI Active Directory security guide` |

## Réseau, pare-feu et virtualisation

R01. OPNsense, documentation officielle, page d’introduction, version courante consultée le 26 novembre 2026. Lien : https://docs.opnsense.org/intro.html. Fiabilité : source primaire du projet. Apport : décrit le pare-feu stateful, les VLAN, OpenVPN, DHCP/DNS, journaux et sauvegardes de configuration ; utile pour évaluer R4, R5, R6, Q7 et T1.

R02. OPNsense, documentation VPN, version courante consultée le 26 novembre 2026. Lien : https://docs.opnsense.org/manual/vpnet.html. Fiabilité : documentation officielle. Apport : décrit OpenVPN road-warrior, les règles explicites et l’usage des instances ; guide les critères de VPN, filtrage et administration dans R5/Q1/Q3/Q4.

R03. Netgate, pfSense Software Documentation, exigences matérielles minimales et guide de dimensionnement, consultés le 26 novembre 2026. Liens : https://docs.netgate.com/pfsense/en/latest/hardware/minimum-requirements.html et https://docs.netgate.com/pfsense/en/latest/hardware/size.html. Fiabilité : source officielle de pfSense. Apport : permet de comparer les minimums et de ne pas confondre un minimum d’installation avec le dimensionnement de charge ; exigences R4/R5 et critères de M3.

R04. Cisco, Catalyst 3750 Switch Software Configuration Guide, IOS Release 15.0(1)SE, chapitre VLAN, documentation constructeur consultée le 26 novembre 2026. Lien : https://www.cisco.com/c/en/us/td/docs/switches/lan/catalyst3750/software/release/15-0_1_se/configuration/guide/scg_3750/swvlan.html. Fiabilité : source primaire ciblée sur l’équipement imposé, malgré l’âge de la version IOS. Apport : ports access, trunks 802.1Q, VLAN autorisés et VLAN natif ; exigences R1/R2 et T2.

R05. Proxmox Server Solutions, « Proxmox VE Administration Guide », chapitres d’introduction et de configuration réseau, relus le 27 novembre 2026 sur le miroir officiel. Ils décrivent les ponts, les VLAN, le stockage et les machines virtuelles, utiles à la conception de la maquette et au choix de virtualisation (R1, R4, T2). [Introduction](https://github.com/proxmox/pve-docs/blob/master/pve-intro.adoc) · [Configuration réseau](https://github.com/proxmox/pve-docs/blob/master/pve-network.adoc)

R06. Oracle, Oracle VirtualBox User Manual 7.2, chapitre 9 « Virtual Networking », consulté le 26 novembre 2026. Lien : https://download.virtualbox.org/virtualbox/7.2.10/UserManual.pdf. Fiabilité : documentation officielle. Apport : réseaux internes, Host-only, NAT et interfaces virtuelles ; renseigne les limites et possibilités d’une maquette sur un poste de travail, exigences R1 et T2.

R07. Broadcom/VMware, « VMware Fusion and Workstation are Now Free for All Users », annonce du 11 novembre 2024, consultée le 26 novembre 2026. Lien : https://blogs.vmware.com/cloud-foundation/2024/11/11/vmware-fusion-and-workstation-are-now-free-for-all-users/. Fiabilité : annonce officielle de l’éditeur. Apport : confirme l’absence de coût de licence pour les usages commerciaux, éducatifs et personnels ; à compléter par la documentation technique de la version si cette solution est retenue, exigence T1.

R26. Netgate, « DHCPv4 Server », documentation officielle de pfSense consultée le 27 novembre 2026. Elle décrit la configuration par interface de la plage de baux, de la passerelle et du DNS transmis au poste du VLAN utilisateurs (V1). [Documentation Netgate](https://docs.netgate.com/pfsense/en/latest/services/dhcp/ipv4.html)

R27. Netgate, « Admin Access », section « Anti-lockout », documentation officielle de pfSense consultée le 27 novembre 2026. Elle précise sur quelle interface la règle anti-verrouillage s’applique et permet de vérifier que l’accès d’administration reste réservé à la zone prévue (R4, Q1, Q3). [Documentation Netgate](https://docs.netgate.com/pfsense/en/latest/config/advanced-admin.html#anti-lockout)

R28. Netgate, « Releases », liste officielle des versions de pfSense, consultée le 27 novembre 2026. La liste distingue les versions CE prises en charge ou à venir des versions en fin de support et sert à contrôler la version retenue au moment de l’installation (Q6). [Versions de pfSense](https://docs.netgate.com/pfsense/en/latest/releases/)

## Identité et Active Directory

R08. Microsoft Learn, « Active Directory Domain Services overview », documentation pour Windows Server 2016 à 2025, consultée le 26 novembre 2026. Lien : https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/active-directory-domain-services. Fiabilité : documentation éditeur du produit imposé. Apport : rôle de l’annuaire, données et services ; base pour S1/S2 et la structure des objets.

R09. Microsoft Learn, « Restore user accounts and groups in AD », documentation pour versions Windows Server supportées, consultée le 26 novembre 2026. Lien : https://learn.microsoft.com/en-us/troubleshoot/windows-server/active-directory/retore-deleted-accounts-and-groups-in-ad. Fiabilité : procédure éditeur. Apport : décrit la corbeille AD et les scénarios de restauration d’objets et de groupes ; exigences S1/V8 et scénario de validation du brief.

R29. Microsoft, « How to configure a firewall for Active Directory domains and trusts », documentation officielle pour les versions de Windows Server prises en charge, consultée le 27 novembre 2026. Elle recense les flux par service et permet de sélectionner ceux dont le poste Windows a besoin pour contacter le contrôleur de domaine (R4, S1, S2, Q1). [Documentation Microsoft](https://learn.microsoft.com/en-us/troubleshoot/windows-server/active-directory/config-firewall-for-ad-domains-and-trusts)

R30. Microsoft, « Joindre un ordinateur à un domaine », procédure officielle consultée le 27 novembre 2026. Elle précise les éditions compatibles, les droits requis et le redémarrage nécessaire pour joindre le poste Windows 11 Pro au domaine (S2, T2). [Procédure Microsoft](https://learn.microsoft.com/fr-fr/windows-server/identity/ad-ds/manage/join-computer-to-domain)

R31. Microsoft, « Resolve-DnsName », référence officielle du module PowerShell DnsClient, consultée le 27 novembre 2026. Elle décrit la requête utilisée depuis le poste client pour vérifier la résolution DNS du nom interne du contrôleur de domaine (V1, T2). [Référence PowerShell](https://learn.microsoft.com/en-us/powershell/module/dnsclient/resolve-dnsname)

R32. Microsoft, « Windows Server release information », calendrier officiel consulté le 27 novembre 2026. Il donne les échéances de support des versions LTSC, dont Windows Server 2022 et 2025, pour vérifier la version qui sera installée sur le contrôleur de domaine (Q6). [Calendrier Microsoft](https://learn.microsoft.com/en-us/windows/release-health/windows-server-release-info)

## Sécurité

R10. Microsoft Learn, « Best practices for securing Active Directory », applicable aux Windows Server 2016, 2019, 2022 et 2025, consultée le 26 novembre 2026. Lien : https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/plan/security-best-practices/best-practices-for-securing-active-directory. Fiabilité : recommandation primaire du fournisseur. Apport : moindre privilège, comptes privilégiés, hôtes d’administration, mises à jour et surveillance ; exigences Q1/Q3/Q5/Q6/Q7 et T4.

R11. ANSSI, « Recommandations pour l’administration sécurisée des SI reposant sur AD », publié le 18 octobre 2023, consulté le 26 novembre 2026. Lien : https://messervices.cyber.gouv.fr/guides/recommandations-pour-ladministration-securisee-des-si-reposant-sur-ad. Fiabilité : recommandation de l’autorité nationale française. Apport : cloisonnement et administration sécurisée des environnements Active Directory ; référence centrale pour R1/Q1/Q3/T4.

R12. ANSSI, « Guide d’hygiène informatique – renforcer la sécurité de son SI en 42 mesures », publié en 2017, consulté le 26 novembre 2026. Lien : https://messervices.cyber.gouv.fr/guides/guide-dhygiene-informatique. Fiabilité : référentiel public reconnu, à lire en tenant compte de sa date et des versions actuelles des produits. Apport : socle de mesures de sécurité pour postes, comptes, mises à jour, sauvegardes, journaux et réseaux ; T4 et exigences Q1 à Q8.

## Stockage et sauvegardes

R13. TrueNAS, TrueNAS Community Edition et guide matériel, versions courantes consultées le 26 novembre 2026. Liens : https://www.truenas.com/truenas-community-edition/ et https://www.truenas.com/docs/scale/gettingstarted/tnhardwareguide/. Fiabilité : documentation officielle. Apport : SMB, intégration Active Directory, ZFS, instantanés et réplication ; minimum recommandé de 8 Go de mémoire ; exigences V2/V8/Q8 et comparaison M3.

R14. openmediavault, documentation stable 8.x, prérequis et fonctionnalités, consultée le 26 novembre 2026. Liens : https://docs.openmediavault.org/en/stable/prerequisites.html et https://docs.openmediavault.org/en/stable/features.html. Fiabilité : documentation officielle du projet. Apport : s’appuie sur Debian, partage SMB/Samba, journaux et ressources minimales ; base pour V2/V8 et la comparaison M3.

R15. Restic, documentation stable 0.20, « Backing up » et installation, consultée le 26 novembre 2026. Liens : https://restic.readthedocs.io/en/stable/040_backup.html et https://restic.readthedocs.io/en/stable/020_installation.html. Fiabilité : documentation officielle du projet. Apport : sauvegardes Windows/Linux, VSS sur Windows, déduplication et planification via le système ; exigences V8/Q8/T5 et procédure de test de restauration.

R16. Restic, documentation stable, préparation d’un dépôt SFTP, consultée le 26 novembre 2026. Lien : https://restic.readthedocs.io/en/stable/030_preparing_a_new_repo.html. Fiabilité : documentation officielle. Apport : dépôt distant par SSH, compte distinct et clé d’authentification ; utile pour cloisonner le serveur de sauvegarde, exigences Q3/Q8.

R17. Restic, projet rest-server, README et changelog 0.14.0, consultés le 26 novembre 2026. Liens : https://github.com/restic/rest-server et https://github.com/restic/rest-server/releases. Fiabilité : dépôt officiel du projet. Apport : mode append-only, authentification et TLS ; limite la suppression de sauvegardes par un client compromis. Ce mode ne remplace pas une copie hors ligne et exige des identifiants distincts pour la maintenance ; exigences Q8/V8.

R18. BorgBackup, documentation stable 1.4.5, initialisation et modes de chiffrement, consultée le 26 novembre 2026. Lien : https://borgbackup.readthedocs.io/en/stable/usage/init.html. Fiabilité : documentation officielle. Apport : dépôt chiffré/authentifié, gestion des clés et append-only ; option alternative pour les clients Linux et les essais de sécurité, exigences V8/Q8.

R19. Microsoft Learn, « Active Directory Forest Recovery – Back up the System State data », applicable aux Windows Server 2016 à 2025, consulté le 26 novembre 2026. Lien : https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-backing-up-system-state. Fiabilité : procédure éditeur. Apport : Windows Server Backup ou `wbadmin` pour sauvegarder l’état système d’un contrôleur de domaine ; évite de confondre sauvegarde de fichiers et sauvegarde AD cohérente, exigences V8/Q8.

## Supervision

R20. Zabbix, documentation 8.0, introduction, support SNMP et cycle de vie, consultée le 26 novembre 2026. Liens : https://www.zabbix.com/documentation/8.0/en/manual/introduction, https://www.zabbix.com/documentation/8.0/en/manual/config/items/itemtypes/snmp et https://www.zabbix.com/life_cycle_and_release_policy. Fiabilité : documentation et politique officielles. Apport : agent Windows/Linux, SNMP, seuils et alertes ; cycle annoncé de Zabbix 8.0 LTS jusqu’en 2031 ; exigences V9/Q7/T1.

R21. Prometheus, documentation officielle, aperçu et alerting, version stable consultée le 26 novembre 2026. Liens : https://prometheus.io/docs/introduction/overview/ et https://prometheus.io/docs/alerting/latest/overview/. Fiabilité : documentation du projet CNCF. Apport : modèle de métriques et alertes via Alertmanager ; option modulaire et légère, mais nécessite exporters et tableau de bord complémentaire pour les besoins de la maquette, V9/M3.

R22. Nagios Enterprises, Nagios Core 4.x, documentation et dépôt officiel, consultés le 26 novembre 2026. Lien : https://github.com/NagiosEnterprises/nagioscore. Fiabilité : source officielle du projet. Apport : hôtes/services, plugins, notifications et interface Web facultative ; candidat alternatif pour V9 et limites d’assemblage/exploitation étudiées en M3.

## Messagerie

R23. Modoboa, documentation officielle des prérequis et de LDAP, vérifiée le 26 novembre 2026. Les [prérequis courants](https://modoboa.readthedocs.io/en/latest/installation/requirements.html) indiquent 4 CPU et 4 Go de RAM. La [documentation 2.4.2](https://modoboa.readthedocs.io/en/2.4.2/installation.html#requirements) indiquait 2 CPU et 2 Go de RAM. La [configuration LDAP](https://modoboa.readthedocs.io/en/latest/configuration.html#ldap) décrit l’authentification et une synchronisation optionnelle testée avec OpenLDAP. Apport pour M3 et V3/Q4/Q6/V10 : dimensionner la version évaluée et vérifier le comportement des comptes avec Active Directory.

R24. Mailu, documentation officielle et versions publiées, vérifiées le 26 novembre 2026. Le [guide d’installation](https://mailu.io/2024.06/setup.html#pick-a-mailu-version) indique 2024.06 comme branche stable, avec des correctifs publiés dans les [versions officielles](https://github.com/Mailu/Mailu/releases). Apport pour M3 et V3/Q4/Q6 : réévaluer la maintenance du candidat sur cette branche et vérifier ses besoins avec ou sans antivirus ainsi que son intégration à l’annuaire.

R25. mailcow: dockerized, documentation officielle, prérequis, installation et fonctions, consultés le 26 novembre 2026. Liens : https://docs.mailcow.email/getstarted/prerequisite-system/, https://docs.mailcow.email/getstarted/install/ et https://docs.mailcow.email/. Fiabilité : documentation officielle. Apport : stack mail, webmail, LDAP/AD, TLS et stratégie de sauvegarde des volumes, mais minimum de ressources élevé ; exigences V3/V8/Q4/Q6 et comparaison M3.

## Application au premier test de la maquette M10

R05 et R06 documentent les réseaux virtuels isolés selon l’hyperviseur utilisé. R04 décrit les VLAN du Catalyst 3750 pour la reprise du scénario sur le matériel Cisco.

| Contrôle prévu dans M10 | Références | Exigences abordées | Preuve attendue |
| --- | --- | --- | --- |
| Ouvrir l’interface HTTPS du pare-feu depuis le VLAN 40 (administration). | R27, R12 | R4, Q3 | Capture de l’interface après connexion. |
| Obtenir la configuration réseau de `PC-01` par DHCP dans le VLAN 10 (utilisateurs). | R26 | V1 | Sortie `ipconfig /all` avec le bail, la passerelle et le DNS attendus. |
| Résoudre le nom interne de `DC-01` depuis `PC-01`. | R08, R29, R31 | V1 | Sortie `Resolve-DnsName` avec l’adresse attendue. |
| Joindre `PC-01` au domaine et ouvrir une session avec le compte fictif standard. | R08, R29, R30 | S1, S2 | Sortie `whoami` avec le compte du domaine. |
| Vérifier le blocage de l’interface d’administration depuis le VLAN 10. | R27, R12 | R4, Q1, Q3, Q7 | Échec de `Test-NetConnection` sur le port HTTPS et entrée correspondante dans le journal du pare-feu. |

Le guide d’hygiène de l’ANSSI (R12) sert de référentiel pour le cloisonnement et la restriction des accès d’administration (T4). Les calendriers R28 et R32 serviront à vérifier le support des versions effectivement installées (Q6).

La fiche M10 décrit des résultats attendus. La [recette du §4.4](../docs/SAE_Cyber_Valdore_Services.md#44-critères-de-validation) inclut aussi la résolution d’un nom public, les accès depuis un poste Linux et le cloisonnement des bases de données et des équipements réseau. Les résultats observés et leurs preuves seront consignés dans le cahier de recette après les essais.

## Recherches écartées ou à compléter

Les billets de blog non éditeurs et les tutoriels non datés ne sont pas utilisés comme preuve de compatibilité ou de support ; ils pourront servir à comprendre un incident, pas à justifier un choix. Les anciennes documentations VirtualBox 6.x, Proxmox 7.4, Modoboa 1.x et les anciens guides ANSSI restent écartés lorsqu’une version actuelle est disponible. Le guide ANSSI 2017 est toutefois conservé comme référentiel général, avec sa date clairement indiquée.

La fiche Microsoft sur l’erreur `0xa8b` a été écartée du scénario nominal, car elle traite d’un échec précis de résolution DNS lors de la jonction au domaine. La procédure R30 couvre la jonction prévue dans M10. [Fiche de dépannage Microsoft](https://learn.microsoft.com/en-us/troubleshoot/windows-server/active-directory/error-0xa8b-resolve-dns-fail)

Au déploiement, relever les versions installées et leurs dates de fin de support. Vérifier le firmware du Catalyst et la version du routeur, puis consigner les références des versions retenues pour Linux, OpenVPN et le transfert de documents. Compléter le dossier avec la politique TLS et les certificats une fois les choix validés.
