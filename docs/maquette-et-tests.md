# Maquette commune et plan de test

**Statut** · Proposition à valider en équipe avant de commencer le développement.

## Maquette commune

Utiliser une seule maquette d’intégration pour assembler les services et exécuter la recette. L’option privilégiée est un serveur de l’école raccordable au Catalyst 3750 et au routeur Cisco. À défaut, évaluer un PC x86-64 disponible ou prêté, dédié à l’équipe. Proxmox VE reste le candidat sur hôte dédié administrable. Sur un poste de travail, évaluer VirtualBox en premier, puis VMware Workstation Pro si le passage du trunk VLAN pose problème. Consigner le choix et les résultats de l’essai dans l’[ADR de virtualisation](adr/ADR-0002-virtualisation.md).

La maquette regroupe le pare-feu et OpenVPN, Windows Server avec Active Directory et DNS, les postes Windows 11 et Linux, les services Linux et le NAS. Le Catalyst porte les VLAN et le routeur Cisco représente l’opérateur du réseau Internet simulé. Les tests du télétravailleur et du client externe partent de ce réseau. Utiliser des comptes et des données fictifs. Tout raccordement au réseau de l’école ou à Internet requiert la validation de l’équipe enseignante. [Contraintes et périmètre du sujet](SAE_Cyber_Valdore_Services.md#41-contraintes-imposées)

Privilégier les ressources disponibles sur place. Réexaminer EC2 ou un VPS si un besoin de travail distant reste sans solution, sous réserve d’un hébergement sans achat et autorisé par l’équipe enseignante. La recette réseau se joue sur les équipements Cisco prêtés.

## Tests à faire en local

| Environnement | Tests adaptés |
| --- | --- |
| VM sur un poste de l’équipe | Lancer les rôles nécessaires au test sur un réseau virtuel interne. Par exemple, tester la jonction au domaine et l’ouverture de session avec Windows Server et Windows 11, ou vérifier la distribution DHCP et la résolution DNS depuis un poste de test. |
| Docker Compose, si le service s’y prête | Démarrer un service Linux et ses dépendances, par exemple l’extranet et sa base. Vérifier le démarrage, la connexion à la base et un parcours utilisateur avec des données fictives. |

Réutiliser les mêmes versions, procédures et données de test que sur la maquette quand c’est possible. Rejouer sur la maquette les scénarios qui traversent plusieurs zones ou dépendent du matériel, notamment le trunk Cisco, les droits d’accès, OpenVPN depuis l’Internet simulé, les alertes et les restaurations. Pour chaque scénario du §4.4, noter les étapes, le résultat attendu, le résultat observé et la preuve dans le cahier de recette M10. [Scénarios de validation](SAE_Cyber_Valdore_Services.md#44-critères-de-validation) · [Spécification M10](../spec/M10-deploiement-recette.spec.md)

## Premier scénario à reproduire

**Prérequis** · Sur un réseau isolé, démarrer le [pare-feu candidat](adr/ADR-0001-pare-feu.md), Windows Server avec AD/DNS dans la zone serveurs et un client Windows 11. Activer le DHCP prévu pour la zone utilisateurs avec le DNS de l’annuaire. Vérifier que l’interface d’administration du pare-feu répond depuis la zone administration. Le même client peut servir à cette vérification avant d’être raccordé à la zone utilisateurs pour le scénario.

| Étape | Résultat attendu | Preuve à garder |
| --- | --- | --- |
| Démarrer le client en DHCP. | Il reçoit une adresse du réseau utilisateurs, la passerelle et le DNS attendus. | Sortie `ipconfig /all`. |
| Résoudre le nom du contrôleur de domaine depuis le client. | Le nom renvoie l’adresse prévue. | Sortie de `Resolve-DnsName` pour le nom du contrôleur. |
| Joindre le poste au domaine et ouvrir une session avec un compte fictif standard. | La session s’ouvre avec le compte du domaine. | Sortie `whoami`. |
| Depuis ce même poste, tenter d’ouvrir l’interface d’administration du pare-feu. | L’accès est bloqué depuis la zone utilisateurs. | Échec de connexion depuis le poste et accès confirmé depuis la zone administration. |

Une deuxième personne reproduit le scénario à partir des procédures et des configurations du dépôt. Elle note le commit testé, les preuves et les écarts rencontrés. Ce premier essai couvre une partie des scénarios du §4.4.

## Points à valider avant de commencer le développement

- [ ] **Hébergement** · Confirmer l’hôte disponible, ses ressources CPU/RAM/disque, l’accès à sa console et les modalités d’accès de l’équipe.
- [ ] **Raccordement** · Faire confirmer les interfaces et ports attribués, puis vérifier le passage des VLAN jusqu’au Catalyst et l’isolement vis-à-vis des réseaux externes à la maquette.
- [ ] **Configuration commune** · Fixer les noms de machines, le domaine AD, les VLAN et sous-réseaux du premier scénario, les flux autorisés, les rôles DHCP/DNS et les versions à utiliser.
- [ ] **Travail dans Git** · Versionner les procédures, scripts, configurations sans secrets et données fictives. Pour chaque service, indiquer les dépendances, le test à lancer et le résultat attendu.
- [ ] **Reproductibilité** · Faire passer le premier scénario à deux membres de l’équipe et consigner les écarts à corriger avant d’intégrer les services.
