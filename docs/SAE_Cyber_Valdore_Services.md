SAE CYBERSÉCURITÉ · SAE 4A

# Valdoré Services

Conception et déploiement d’un système d’information

![INSA Hauts-de-France](insa-hauts-de-france.png)

Maxime FENETRE / Jérôme RIDET · [PDF d’origine](../SAE_Cyber_Valdore_Services.pdf)

<table>
<tr><th scope="row">Public</th><td>Élèves ingénieurs de 4ᵉ année</td></tr>
<tr><th scope="row">Durée</th><td>50 heures par groupe : 25 h encadrées et 25 h en autonomie</td></tr>
<tr><th scope="row">Groupes</th><td>3 ou 4 étudiants</td></tr>
<tr><th scope="row">Thèmes</th><td>Conception d’architecture, déploiement de réseaux et de systèmes, services réseau, sécurité dès la conception</td></tr>
<tr><th scope="row">Environnement</th><td>Machines virtuelles, serveurs de l’école, équipements Cisco (commutateur Catalyst 3750, routeur)</td></tr>
</table>

Les personnes, entreprises, adresses et données mentionnées dans ce document sont fictives.

## Sommaire

1. Présentation du projet
2. Contexte : l’entreprise Valdoré Services
3. Expression des besoins
4. Cahier des charges
5. Missions et évaluation des compétences

## 1. Présentation du projet

### 1.1 Objectifs

Ce projet place les étudiants dans la situation d’une équipe d’ingénieurs à qui une entreprise confie la création de son système d’information. Le client exprime des besoins, pas des solutions : à l’équipe de concevoir l’architecture, de choisir les technologies, de déployer l’ensemble dans une maquette et de démontrer qu’il répond aux besoins.

Compétences mobilisées : conception d’une architecture réseau et système, configuration d’équipements Cisco, administration d’un pare-feu et d’un VPN open source, Active Directory et Windows Server, administration Linux, déploiement de services réseau, sauvegarde, supervision, prise en compte de la sécurité dès la conception. Le projet permet aussi d’évaluer des compétences transverses (recherche documentaire, communication en anglais, choix des solutions, analyse et optimisation des performances, audit et sécurisation, suivi du projet avec le client, déploiement, exploitation, formation des utilisateurs), au travers des missions du chapitre 5.

### 1.2 Organisation

Le projet représente 50 heures de travail par groupe : 25 heures encadrées et 25 heures en autonomie. La répartition des rôles dans le groupe est laissée à l’initiative des étudiants. L’infrastructure comprend des environnements Windows, Windows Server et Linux : chaque étudiant est invité à intervenir sur chacun de ces trois environnements.

Le choix des technologies, de l’architecture et du plan d’adressage appartient au groupe, qui doit justifier ses choix. Sauf contrainte explicite au chapitre 4, aucune solution n’est imposée. Pour toute question sur les besoins, l’équipe enseignante joue le rôle du client.

### 1.3 Règles

#### À respecter pendant tout le projet

- **Environnement isolé.** La maquette est déployée sur des réseaux virtuels isolés. Elle n’est reliée au réseau de l’établissement ou à Internet que sur validation de l’équipe enseignante.

- **Données fictives.** Les comptes, adresses et données de la maquette sont fictifs. Aucun mot de passe réel ne doit être utilisé.

- **Choix justifiés.** Chaque choix structurant (technologie, découpage réseau, regroupement de services) est argumenté par rapport aux besoins et aux contraintes.

## 2. Contexte : l’entreprise Valdoré Services

### 2.1 Fiche d’identité

<table>
<tr><th scope="row">Raison sociale</th><td>Valdoré Services (SAS)</td></tr>
<tr><th scope="row">Création</th><td>2009, à Amiens (Somme)</td></tr>
<tr><th scope="row">Activité</th><td>Conseil et ingénierie de projets pour des collectivités territoriales et des industriels : assistance à maîtrise d’ouvrage, études de mobilité et d’aménagement, suivi de chantiers, conformité réglementaire</td></tr>
<tr><th scope="row">Effectif</th><td>82 salariés</td></tr>
<tr><th scope="row">Implantation</th><td>Un site unique à Amiens, dans de nouveaux locaux. Environ 40 % des salariés travaillent à distance deux à trois jours par semaine.</td></tr>
<tr><th scope="row">Chiffre d’affaires</th><td>9,4 M€</td></tr>
<tr><th scope="row">Clientèle</th><td>Une soixantaine de collectivités et une vingtaine d’industriels de la région Hauts-de-France</td></tr>
<tr><th scope="row">Direction</th><td>Mme Hélène Marchand, présidente ; M. Thomas Girard, directeur administratif et financier, interlocuteur de l’équipe projet<br>M. Justin Case est Américain et postule sur le poste de DSI.</td></tr>
</table>

### 2.2 Organisation et usages

| Service | Effectif | Usages informatiques principaux |
| --- | --- | --- |
| Direction | 4 | Messagerie, dossiers confidentiels, visioconférence |
| Commercial et avant-vente | 14 | Messagerie, relation avec les clients, déplacements fréquents |
| Consultants et ingénieurs | 48 | Dossiers projets volumineux, remise de livrables aux clients, télétravail pour environ 35 d’entre eux |
| Administration, RH, finance | 11 | Données RH et paie, logiciel de comptabilité, échanges avec l’expert-comptable et les banques |
| Communication | 4 | Site web vitrine, supports volumineux |
| Informatique | 1 | Poste à créer ; l’équipe projet intervient en prestation |

### 2.3 Données et enjeux

- Données clients : documents contractuels, plans, données territoriales parfois sensibles, confiées par les collectivités.

- Données personnelles : dossiers RH et paie, soumis au RGPD.

- Propriété intellectuelle : études et méthodes de l’entreprise.

- Disponibilité : les délais de livraison sont contractuels et assortis de pénalités.

- Confiance des clients : plusieurs marchés publics comportent des clauses de sécurité du système d’information.

### 2.4 Le projet

Jusqu’à présent, Valdoré Services s’est contentée d’un équipement minimal : un accès Internet grand public, des postes autonomes, des outils en ligne et un partage de fichiers rudimentaire. Pour le SAE 2026, il vous est demandé de revoir l’architecture. L’entreprise compte 82 salariés, elle emménage dans de nouveaux locaux à Amiens, et ses clients lui demandent des garanties.

La Communauté d’agglomération Somme-Littoral, qui représente près de 30 % du chiffre d’affaires, renouvelle son marché de trois ans et attend de son prestataire un système d’information maîtrisé : zones cloisonnées, accès distant contrôlé, données sauvegardées, activité traçable. La direction a décidé de construire un système d’information complet et sécurisé, hébergé dans ses locaux, avant l’emménagement.

### 2.5 Votre mission

La direction mandate votre équipe (SAE) pour concevoir cette infrastructure, la déployer dans une maquette de démonstration, et prouver qu’elle répond aux besoins exprimés au chapitre 3. La maquette doit être suffisamment aboutie pour servir de référence lors du déploiement réel.

Conditions fixées par la direction : aucun achat supplémentaire n’est possible. Les solutions retenues sont open source ou reposent sur des licences déjà détenues (Windows Server, postes Windows, équipements Cisco existants).

## 3. Expression des besoins

Ce chapitre décrit ce que l’entreprise attend de son système d’information, avec ses mots. Il ne dit pas comment y parvenir.

### 3.1 Besoins par domaine

| Domaine | Besoin exprimé |
| --- | --- |
| Identité et postes | « Chaque salarié dispose d’un compte unique.Il peut travailler sur n’importe quel poste de l’entreprise, Windows ou Linux, et retrouver ses ressources. Les postes sont configurés de façon homogène et centralisée. L’arrivée d’un nouveau salarié doit pouvoir être traitée en quelques minutes. » |
| Réseau local | « Les postes obtiennent automatiquement leur configuration réseau, sans intervention. Les ressources internes sont joignables par leur nom. Les noms publics de l’entreprise (site web, messagerie) sont également résolus. » |
| Documents | « Les salariés disposent d’espaces de stockage et peuvent partager leurs fichiers, accessibles depuis un poste Windows comme depuis un poste Linux, dont l’accès respecte les règles du paragraphe 3.2. » |
| Messagerie | « Chaque salarié dispose d’une adresse prenom.nom@valdore-services.fr. Il envoie et reçoit des courriels depuis son poste ou depuis un navigateur, y compris en télétravail. Le courrier circule avec l’extérieur. » |
| Présence sur Internet | « L’entreprise publie un site vitrine public et un extranet réservé à ses clients. Les clients s’y authentifient pour consulter leurs dossiers, qui sont stockés dans une base de données. » |
| Échange de documents avec les clients | « Les clients peuvent déposer et récupérer des documents volumineux de manière contrôlée, sans passer par la messagerie. » |
| Données applicatives | « Le logiciel de comptabilité et l’extranet reposent sur des bases de données hébergées en interne. Seuls les applications et les administrateurs concernés y accèdent. » |
| Accès à Internet | « Les salariés naviguent sur Internet depuis leur poste. La direction souhaite pouvoir contrôler et tracer ces accès. » |
| Télétravail | « Environ 35 salariés travaillent à distance. Ils accèdent aux dossiers et à la messagerie comme au bureau. L’accès est individuel et se limite à ce dont chacun a besoin. » |
| Sauvegarde | « Les données critiques (annuaire, dossiers, bases de données, messagerie) sont sauvegardées chaque nuit sur un équipement de stockage dédié de type NAS. La direction veut avoir la preuve qu’une restauration fonctionne. » |
| Supervision | « L’équipe informatique suit l’état des équipements et des services et est alertée en cas d’indisponibilité. » |
| Sécurité générale | « Les différentes zones de l’entreprise sont cloisonnées. Seul ce qui doit être accessible depuis Internet l’est. L’administration est réservée à l’équipe informatique, et l’activité laisse des traces exploitables. » |

### 3.2 Règles d’accès aux données

| Ressource | Qui y accède |
| --- | --- |
| Dossier commun de l’entreprise | Tous les salariés, en lecture et en écriture |
| Dossier personnel | Le salarié concerné uniquement |
| Dossier d’un service (commercial, conseil, communication) | Les membres du service uniquement |
| Dossiers de la direction | La direction uniquement |
| Dossiers RH et paie | L’équipe administration, RH et finance en lecture et en écriture, la direction en lecture seule, personne d’autre |
| Dossiers projets | Les consultants affectés au projet en lecture et en écriture ; les commerciaux en lecture sur les projets de leurs clients |
| Sauvegardes | L’équipe informatique uniquement |
| Outils d’administration (équipements, serveurs, pare-feu) | L’équipe informatique uniquement |

### 3.3 Volumétrie et niveau de service

| Critère | Attente |
| --- | --- |
| Population | 82 salariés aujourd’hui, avec une croissance de l’ordre de 25 % sur trois ans |
| Télétravail | Environ 35 salariés connectés simultanément à distance |
| Plages d’utilisation | De 7 h à 20 h, du lundi au vendredi |
| Perte de données tolérée | Au plus la journée de travail précédente |
| Délai de reprise tolérable | Quelques heures pour la messagerie, les dossiers et l’annuaire ; une journée pour le reste |

## 4. Cahier des charges

Le cahier des charges fixe les contraintes à respecter, le périmètre de la maquette, les exigences à satisfaire et les critères de validation. Chaque exigence porte un identifiant. La priorité est O (obligatoire) ou S (souhaitable, pour les groupes en avance).

### 4.1 Contraintes imposées

| Élément | Contrainte |
| --- | --- |
| Équipements réseau | Un commutateur Cisco Catalyst 3750 et un routeur Cisco, mis à disposition par l’équipe enseignante |
| Pare-feu et VPN | Pare-feu OPNsense ou pfSense CE. L’accès distant des télétravailleurs repose sur OpenVPN, fourni par ce pare-feu. |
| Annuaire | Active Directory sur Windows Server (version d’évaluation, version au choix) |
| Postes | Au moins un poste Windows 11 et un poste Linux avec interface graphique |
| Serveurs de services | Linux, distribution et logiciels open source au choix du groupe |
| Virtualisation | VirtualBox, VMware ou Proxmox, avec réseaux virtuels isolés. Des serveurs de l’école peuvent accueillir une partie des machines. |
| Internet simulé | Le routeur joue le rôle de l’opérateur. Le site dispose du bloc d’adresses publiques 203.0.113.0/29. Un réseau 198.51.100.0/24 simule Internet et accueille le poste du télétravailleur et un éventuel client externe. |
| Noms de domaine | Le domaine public de l’entreprise est valdore-services.fr (résolution à simuler). Le nom du domaine interne est au choix du groupe. |
| Adressage | Adresses privées (RFC 1918) pour le réseau interne, plan à concevoir par le groupe |
| Budget et licences | Solutions open source ou licences déjà détenues, aucun achat |

### 4.2 Périmètre de la maquette

- La maquette représente le site d’Amiens et couvre l’ensemble des besoins du chapitre 3.

- Elle n’a pas à reproduire les 82 postes : un échantillon représentatif suffit (au moins un poste Windows, un poste Linux, un poste de télétravailleur sur l’Internet simulé et, si possible, un poste de client externe).

- L’annuaire contient au moins 20 comptes fictifs répartis dans les cinq services de l’entreprise, avec les groupes nécessaires aux règles du paragraphe 3.2.

- Les ressources de la maquette sont limitées. Le groupe dimensionne ses machines et peut regrouper plusieurs services sur une même machine, à condition de justifier ce choix au regard de la sécurité et de la disponibilité. L’équipe enseignante précise les ressources disponibles et le raccordement aux équipements Cisco lors de la première séance.

### 4.3 Exigences

#### Réseau

| Réf. | Exigence | Priorité |
| --- | --- | --- |
| R1 | Concevoir et justifier un plan d’adressage IP et un découpage du réseau en zones (VLAN), dimensionnés pour au moins 120 équipements utilisateurs et distinguant au minimum les postes, les serveurs internes, les serveurs exposés sur Internet et l’administration. | O |
| R2 | Configurer le commutateur Catalyst 3750 : VLAN, liaisons avec les autres équipements, accès d’administration, et routage entre VLAN si l’architecture retenue le prévoit (choix à justifier). | O |
| R3 | Configurer le routeur : accès à l’Internet simulé, adressage public, routage. | O |
| R4 | Déployer le pare-feu : interfaces et zones, translation d’adresses, publication des seuls services devant être joignables depuis Internet, politique de filtrage cohérente avec le cloisonnement. | O |
| R5 | Déployer le VPN OpenVPN pour les télétravailleurs : accès individuel, limité aux ressources nécessaires. | O |
| R6 | Permettre aux postes d’accéder à Internet en respectant le besoin de contrôle et de traçabilité du chapitre 3. | O |

#### Systèmes

| Réf. | Exigence | Priorité |
| --- | --- | --- |
| S1 | Déployer l’annuaire Active Directory : domaine, structure reflétant l’organisation de l’entreprise, comptes, groupes, stratégies de configuration des postes. | O |
| S2 | Intégrer les postes Windows au domaine et leur appliquer une configuration centralisée. | O |
| S3 | Permettre à un poste Linux d’accéder aux ressources de l’entreprise avec le compte du salarié. | O |
| S4 | Intégrer le poste Linux à l’authentification centralisée de l’annuaire. | S |
| S5 | Déployer les serveurs Linux nécessaires aux services du chapitre 3, avec système et dimensionnement justifiés. | O |
| S6 | Mettre en œuvre les règles d’accès aux données du paragraphe 3.2. | O |

#### Services

| Réf. | Exigence | Priorité |
| --- | --- | --- |
| V1 | Fournir aux postes leur configuration réseau automatiquement, et la résolution des noms internes et des noms publics de l’entreprise. | O |
| V2 | Fournir les espaces de stockage partagés, accessibles depuis Windows et Linux. | O |
| V3 | Fournir la messagerie des salariés avec accès par webmail, pour le courrier interne et externe. | O |
| V4 | Publier le site vitrine et l’extranet clients, qui s’appuie sur une base de données (application web au choix du groupe, à faire valider par l’équipe enseignante). | O |
| V5 | Fournir un service d’échange de documents avec les clients (protocole au choix, justifié). | O |
| V6 | Héberger les bases de données internes (extranet, comptabilité) et en restreindre l’accès. | O |
| V7 | Fournir un accès à Internet contrôlé et tracé pour les postes (proxy ou solution équivalente). | O |
| V8 | Planifier les sauvegardes nocturnes sur le NAS des données listées au chapitre 3. | O |
| V9 | Superviser les équipements et les services, avec alertes en cas d’indisponibilité. | O |
| V10 | Utiliser l’annuaire pour authentifier les utilisateurs d’au moins un service hébergé sur serveur Linux. | S |

#### Sécurité dès la conception

| Réf. | Exigence | Priorité |
| --- | --- | --- |
| Q1 | Appliquer le principe du moindre privilège dans les règles de filtrage, les droits d’accès et les comptes. | O |
| Q2 | Limiter strictement les services exposés sur Internet et les isoler du réseau interne. | O |
| Q3 | Réserver l’administration à l’équipe informatique, avec des comptes nominatifs, des accès chiffrés et une séparation entre comptes d’administration et comptes d’usage courant. | O |
| Q4 | Protéger par chiffrement les échanges d’authentification, les données des clients et les accès distants. | O |
| Q5 | Définir et appliquer une politique de mots de passe adaptée. Aucun mot de passe par défaut ni partagé entre plusieurs personnes ou systèmes. | O |
| Q6 | Installer des versions de systèmes et de logiciels encore supportées, et définir la manière dont elles sont maintenues à jour. | O |
| Q7 | Disposer d’une source de temps commune et conserver les journaux des équipements et des services clés. | O |
| Q8 | Protéger les sauvegardes contre l’effacement ou le chiffrement par un tiers malveillant. | O |
| Q9 | Centraliser les journaux sur un serveur dédié. | S |
| Q10 | Mettre en place une authentification à deux facteurs sur l’accès VPN. | S |

#### Qualité et exploitation

| Réf. | Exigence | Priorité |
| --- | --- | --- |
| T1 | Justifier chaque choix structurant par rapport aux besoins, aux contraintes et aux solutions écartées. | O |
| T2 | Documenter l’infrastructure (schéma, adressage, flux autorisés, procédures d’installation, comptes) de façon à pouvoir la reconstruire. | O |
| T3 | Tracer les modifications (date, auteur, objet) et sauvegarder les configurations avant toute intervention. | O |
| T4 | S’appuyer sur au moins un référentiel reconnu pour les choix de sécurité (par exemple le guide d’hygiène informatique de l’ANSSI ou les benchmarks CIS). | O |
| T5 | Automatiser les tâches répétitives (création de comptes en masse, déploiement de configuration) par des scripts. | S |

### 4.4 Critères de validation

L’infrastructure est validée par la démonstration des scénarios suivants, sur la maquette :

- Un nouvel utilisateur est créé, ouvre une session sur un poste Windows puis sur un poste Linux, et n’accède qu’aux ressources autorisées par le paragraphe 3.2.

- Un poste raccordé au réseau reçoit automatiquement sa configuration, et résout un nom interne et un nom public.

- Un salarié de l’équipe RH accède aux dossiers RH, alors qu’un consultant n’y accède pas.

- Deux salariés échangent des courriels, puis l’un d’eux écrit à un correspondant externe simulé. Un salarié consulte sa messagerie par webmail.

- Un client externe, depuis l’Internet simulé, consulte le site vitrine, s’authentifie sur l’extranet et dépose un document.

- Un télétravailleur se connecte depuis l’Internet simulé et accède à ses dossiers et à sa messagerie, mais pas aux outils d’administration.

- Un poste utilisateur ne peut joindre ni les bases de données, ni l’interface d’administration du pare-feu, ni les équipements réseau.

- Un poste navigue sur Internet et les traces de cet accès sont consultables.

- L’arrêt volontaire d’un service déclenche une alerte visible dans la supervision.

- Un dossier est supprimé puis restauré depuis la sauvegarde, et un compte de l’annuaire est restauré.

### 4.5 Références utiles

- Guide d’hygiène informatique de l’ANSSI et recommandations de l’ANSSI sur la sécurisation de l’annuaire Active Directory.

- Documentations officielles d’OPNsense ou pfSense, d’OpenVPN, de Microsoft et des logiciels libres retenus.

- Benchmarks CIS pour les systèmes et équipements retenus.

- NMAP, Wireshark,etc.

## 5. Missions et évaluation des compétences

En complément des exigences techniques du chapitre 4, l’équipe réalise dix missions qui permettent d’évaluer les compétences du référentiel visées par la SAE. Chaque mission précise le travail attendu, les livrables, l’échéance et les observables utilisés pour l’évaluation. Plusieurs missions s’appuient sur des exigences existantes (T1, T2, T4, V9…) : elles en précisent la forme et ne demandent pas de travail en double.

Observables : SA, suivi d’activité ; PEI, production d’écrit intermédiaire ; PEF, production d’écrit final ; POI, production orale intermédiaire ; POF, production orale finale.

Les compétences sont évaluées pour chaque étudiant à l’aide de la grille d’évaluation de la SAE, sur quatre niveaux (1 Notion, 2 Application, 3 Maîtrise, 4 Expertise). Les critères des niveaux 1 et 2 sont rappelés pour chaque mission. Le niveau attendu est le niveau 1. Les compétences BC 2.2, BC 3.1, BC 3.2, BC 4.1, BC 4.3, BC 4.4 et BC 4.5 sont essentielles : le niveau attendu doit être atteint pour valider la SAE.

### 5.1 Vue d’ensemble

| Mission | BC | Livrables | Échéance |
| --- | --- | --- | --- |
| M1 – Présenter une partie du projet en anglais (1slide) | BC 1.7 | Executive summary en anglais (annexe du rapport final) | Soutenance finale |
| M2 – Constituer un dossier documentaire | BC 1.8 | Dossier documentaire commenté (annexe du rapport final) | Première version à la fin de la 2ᵉ séance encadrée ; version finale avec le rapport |
| M3 – Comparer et sélectionner les solutions | BC 2.2 | Matrices de choix (document intermédiaire),<br>Explication de choix (ex : structure de la maquette, des choix d’outils,etc.) | Mi-projet, avant le déploiement des services |
| M4 – Mesurer et optimiser les performances | BC 3.2 | Rapport de performance : indicateurs, mesures avant et après, optimisations, projection à trois ans ; tableau de bord de supervision présenté en soutenance | Rapport final et soutenance |
| M5 – Administrer et exploiter l’infrastructure | BC 4.4 | Cahier d’exploitation ; registre des interventions et des incidents (cyber) | Procédures au fil du projet ; incidents lors de la dernière séance encadrée |
| M6 – Former les utilisateurs | BC 4.5 | Guide salariés, fiche clients, fiche de passation (annexes du rapport final) ; session de formation | Rapport final et soutenance |
| M7 – Analyser l’activité et la disponibilité du SI | BC 3.1 | Rapport d’activité et de disponibilité (métriques, capture commentée, interprétation) ; point oral sur les premières mesures | Premières mesures en cours de projet ; rapport final et soutenance |
| M8 – Auditer, fiabiliser et sécuriser | BC 3.5 | Rapport d’audit : analyse de risques, résultats avant et après correction, test de restauration, plan d’action | Fin de projet, après le déploiement des services principaux ; synthèse présentée en soutenance |
| M9 – Suivre le projet et rendre compte au client | BC 4.1 | README de séance ; tableau de suivi des exigences ; registre des échanges avec le client | À chaque séance, tout au long du projet |
| M10 – Planifier, déployer et recetter | BC 4.3 | Plan de déploiement ; procédures et dépôt des configurations ; cahier de recette complété | Plan au début du déploiement ; recette avant la soutenance ; démonstration en soutenance |

### 5.2 Mission M1 – Présenter le projet

Compétence évaluée. BC 1.7 : Soutenir un échange courant et/ou technique dans un contexte international et multiculturel.

Contexte. La société a invité le futur DSI, anglophone, à votre soutenance . Valdoré Services doit pouvoir lui présenter son système d’information.

#### Travail demandé

- Rédiger en anglais une synthèse (executive summary) d’une à deux pages : contexte, architecture retenue, principales mesures de sécurité, limites de la maquette et prochaines étapes.

- Présenter en anglais, pendant la soutenance, une slide au choix.

- Souhaitable : établir un glossaire technique français-anglais des termes employés dans le projet.

#### Livrables et évaluation

<table>
<tr><th scope="row">Livrables</th><td>Executive summary en anglais (annexe du rapport final) ; intervention orale en anglais</td></tr>
<tr><th scope="row">Échéance</th><td>Soutenance finale</td></tr>
</table>

### 5.3 Mission M2 – Constituer un dossier documentaire (BC 1.8)

Compétence évaluée. BC 1.8 : Effectuer une recherche documentaire.

Contexte. La direction veut pouvoir vérifier que les choix techniques reposent sur des références reconnues et à jour, et non sur des tutoriels pris au hasard. Le futur administrateur doit aussi savoir où trouver l’information de référence.

#### Travail demandé

- Définir, pour chaque domaine (réseau, annuaire, messagerie, sauvegarde, supervision, sécurité), les mots- clés et les requêtes utilisés, en français et en anglais.

- Privilégier les sources adaptées : documentations officielles des éditeurs et des projets, publications de l’ANSSI et du CERT-FR, benchmarks CIS, RFC, bases de vulnérabilités (CVE), calendriers de fin de support des logiciels retenus (exigence Q6).

- Constituer un dossier d’au moins 15 références classées par domaine. Pour chacune : référence complète (titre, auteur ou éditeur, date ou version, lien), fiabilité de la source, apport au projet en une ou deux phrases, exigences concernées.

- Indiquer les sources consultées puis écartées (obsolètes, non officielles, version différente) et la raison.

- Citer ces références dans la documentation de l’infrastructure et dans les matrices de choix.

#### Livrables et évaluation

<table>
<tr><th scope="row">Livrables</th><td>Dossier documentaire commenté (annexe du rapport final)</td></tr>
<tr><th scope="row">Échéance</th><td>Première version à la fin de la 2ᵉ séance encadrée ; version finale avec le rapport</td></tr>
</table>

### 5.4 Mission M3 – Comparer et sélectionner les solutions (BC 2.2)

Compétence évaluée. BC 2.2 : Étudier, comparer et sélectionner les outils et méthodes nécessaires à la conception, au développement et au test d’une solution informatique.

Contexte. En dehors des contraintes du paragraphe 4.1, aucune solution n’est imposée. Avant de déployer les services, l’équipe présente au client une étude comparative qui justifie ses choix (exigence T1).

#### Travail demandé

- Pour au moins cinq choix structurants, identifier deux ou trois solutions candidates. Choix à traiter obligatoirement : pare-feu (OPNsense ou pfSense CE), plateforme de virtualisation, solution de sauvegardes et NAS, solution de supervision. Au moins un choix supplémentaire parmi : messagerie, échange de documents avec les clients (V5), proxy (V7), application d’extranet (V4), distribution Linux des serveurs.

- Définir et pondérer les critères avant de comparer : adéquation aux besoins du chapitre 3, respect des contraintes du paragraphe 4.1 (open source, aucun achat), sécurité (chiffrement, historique de vulnérabilités, intégration à l’annuaire), durée de support, compatibilité avec l’existant (Active Directory, Cisco), ressources consommées dans la maquette, facilité d’exploitation par un administrateur unique, qualité de la documentation.

- Présenter chaque comparaison sous forme de matrice de choix (critères, poids, notes, total) et conclure : solution retenue, solutions écartées et raisons.

- Souhaitable : Il sera possible présenter et discuter des choix avec Maxime ou Jérôme lors des séances tuteurées.

#### Livrables et évaluation

<table>
<tr><th scope="row">Livrables</th><td>Matrices de choix (document intermédiaire) ; revue orale de 10 minutes</td></tr>
<tr><th scope="row">Échéance</th><td>Mi-projet, avant le déploiement des services</td></tr>
</table>

### 5.5 Mission M4 – Mesurer et optimiser les performances (BC 3.2)

Compétence évaluée. BC 3.2 : Assurer et optimiser les performances des systèmes d’information.

Contexte. Les ressources de la maquette sont limitées, 35 télétravailleurs se connectent simultanément, les sauvegardes doivent s’achever avant 7 h et l’effectif augmentera d’environ 25 % en trois ans. La direction veut s’assurer que l’infrastructure tiendra la charge.

#### Travail demandé

- Définir les indicateurs à suivre : processeur, mémoire, espace disque et débit réseau de chaque serveur et équipement, ainsi que des indicateurs de service (temps de réponse du webmail et de l’extranet, nombre de sessions VPN, durée des sauvegardes). Les intégrer à la supervision (V9) avec des seuils d’alerte.

- Relever une mesure de référence, maquette au repos (précisez les outils).

- Réaliser au moins deux tests de charge représentatifs, par exemple : plusieurs connexions VPN simultanées avec mesure du débit (iperf3), requêtes en nombre sur l’extranet (ab, wrk ou siege), copie de fichiers volumineux sur les partages, durée d’une sauvegarde complète puis incrémentale. (Cette montée en charge peut être simulée par des scripts batch, powershell, bash...)

- Identifier le facteur limitant et proposer une solution.

- Mesurer de nouveau après optimisation et comparer avec la référence.

- Vérifier que la sauvegarde nocturne tient dans la plage de 20 h à 7 h et estimer le comportement de l’infrastructure avec 25 % d’utilisateurs en plus.

#### Livrables et évaluation

<table>
<tr><th scope="row">Livrables</th><td>Rapport de performance : indicateurs, mesures avant et après, optimisations, projection à trois ans ; tableau de bord de supervision présenté en soutenance</td></tr>
<tr><th scope="row">Échéance</th><td>Rapport final et soutenance</td></tr>
</table>

### 5.6 Mission M5 – Administrer et exploiter l’infrastructure (BC 4.4)

Compétence évaluée. BC 4.4 : Administrer une solution informatique.

Contexte. Valdoré Services ne dispose que d’un poste informatique, encore à pourvoir. L’infrastructure doit pouvoir être administrée au quotidien, et les incidents détectés et corrigés rapidement.

#### Travail demandé

- Rédiger un cahier d’exploitation : inventaire des composants, comptes d’administration (sans mot de passe en clair), tâches périodiques (quotidiennes, hebdomadaires, mensuelles) et procédures courantes.

- Rédiger puis exécuter sur la maquette les procédures courantes : arrivée et départ d’un salarié (compte, groupes, boîte aux lettres, accès VPN, désactivation puis suppression), changement de service, réinitialisation d’un mot de passe, sauvegarde et restauration de la configuration d’un équipement Cisco ou du pare-feu (T3), contrôle des sauvegardes de la nuit.

- **Séance d’incidents :** lors de la dernière séance encadrée, l’équipe enseignante provoque trois à cinq incidents sur la maquette sans en révéler la nature (*par exemple service arrêté, disque plein, étendue DHCP épuisée, certificat expiré, compte verrouillé, règle de pare-feu modifiée*). L’équipe les détecte grâce à la supervision et aux journaux, pose le diagnostique et corrige.

- Consigner chaque intervention dans un registre : date, auteur, symptôme, cause, action, vérification.

#### Livrables et évaluation

<table>
<tr><th scope="row">Livrables</th><td>Cahier d’exploitation ; registre des interventions et des incidents</td></tr>
<tr><th scope="row">Échéance</th><td>Procédures au fil du projet ; incidents lors de la dernière séance encadrée</td></tr>
</table>

### 5.7 Mission M6 – Former les utilisateurs (BC 4.5)

Compétence évaluée. BC 4.5 : Former l’utilisateur à l’usage de la solution informatique.

Contexte. Le nouveau système d’information change les habitudes des salariés : compte unique, droits d’accès, nouvelle messagerie, VPN pour le télétravail. Sa réussite dépend de leur adhésion. Les clients doivent aussi savoir utiliser l’extranet, et le futur administrateur reprendre l’infrastructure.

#### Travail demandé

- Rédiger un guide de démarrage rapide pour les salariés (2 à 4 pages, illustré de captures de la maquette) : première connexion et changement de mot de passe, règles de mots de passe (Q5), accès aux dossiers selon les droits, messagerie et webmail, connexion en télétravail par VPN, bons réflexes (verrouillage du poste, courriels suspects), interlocuteur en cas de problème.

- Rédiger une fiche pour les clients externes : accès à l’extranet, dépôt et récupération de documents.

- Porposer un support pour l’animation d’une session de formation de 10 minutes.

- Souhaitable : réaliser une courte vidéo de démonstration (3 minutes au plus) ou une foire aux questions.

#### Livrables et évaluation

<table>
<tr><th scope="row">Livrables</th><td>Guide salariés, fiche clients, fiche de passation (annexes du rapport final) ; session de formation</td></tr>
<tr><th scope="row">Échéance</th><td>Rapport final et soutenance</td></tr>
</table>

### 5.8 Mission M7 – Analyser l’activité et la disponibilité du SI (BC 3.1)

Compétence évaluée. BC 3.1 : Analyser une solution informatique et en mesurer les performances en utilisant les outils et métriques adaptés (réseaux, systèmes, accès aux données, sécurité, etc.).

Contexte. La direction veut des éléments factuels sur l’usage et l’état de son système d’information : quels services sont utilisés, par qui et d’où, avec quelle disponibilité, et quels événements de sécurité surviennent. Ces mesures servent de point de départ aux optimisations de la mission M4 et au suivi de sécurité de la mission M8.

#### Travail demandé

- Recenser les sources de mesure disponibles : supervision, journaux du pare-feu, du proxy et du VPN, événements de connexion des contrôleurs de domaine, journaux du serveur web, de l’extranet et de la messagerie.

- Définir une dizaine de métriques couvrant le réseau, les systèmes, l’accès aux données et la sécurité, par exemple : taux de disponibilité de chaque service, temps de réponse, latence et débit entre les zones, nombre de sessions VPN simultanées, volume d’échanges sur les partages, sites les plus consultés et requêtes bloquées par le proxy, échecs d’authentification, flux refusés par le pare-feu.

- Générer une activité représentative sur la maquette et collecter ces métriques pendant au moins une séance.

- Analyser une capture de trafic (Wireshark ou tcpdump) d’un échange choisi, par exemple une ouverture de session sur le domaine ou une connexion VPN, pour vérifier les protocoles utilisés et le chiffrement des échanges (Q4).

- Présenter les résultats dans un tableau de bord ou un rapport d’activité : valeurs mesurées, tendances, anomalies, interprétation, et pistes d’amélioration transmises à la mission M4.

#### Livrables et évaluation

<table>
<tr><th scope="row">Livrables</th><td>Rapport d’activité et de disponibilité (métriques, capture commentée, interprétation) ; point oral sur les premières mesures</td></tr>
<tr><th scope="row">Échéance</th><td>Premières mesures en cours de projet ; rapport final et soutenance</td></tr>
</table>

### 5.9 Mission M8 – Auditer, fiabiliser et sécuriser (BC 3.5)

Compétence évaluée. BC 3.5 : Fiabiliser et sécuriser.

Contexte. Le marché de la Communauté d’agglomération Somme-Littoral comporte des clauses de sécurité. Avant de présenter l’infrastructure à son client, la direction demande un audit interne : vulnérabilités restantes, mesures prises, capacité à redémarrer après un incident.

#### Travail demandé

- Mener une analyse de risques simplifiée, en s’inspirant de la méthode EBIOS Risk Manager de l’ANSSI : biens essentiels (données clients, données RH, disponibilité des services), scénarios de menace (rançongiciel, hameçonnage, compromission d’un compte VPN, fuite de données, panne d’un serveur) et, pour chacun, les mesures du cahier des charges qui y répondent.

- Auditer la maquette, et uniquement la maquette, avec des outils open source : recensement des ports et services exposés depuis l’Internet simulé et depuis le réseau des postes (nmap), recherche de vulnérabilités (Greenbone OpenVAS), audit de l’annuaire (PingCastle), audit des serveurs Linux (Lynis).

- Classer les vulnérabilités par gravité, corriger les plus critiques en s’appuyant sur les guides de l’ANSSI ou les benchmarks CIS, puis vérifier les corrections par un nouvel audit.

- Fiabiliser : restaurer intégralement au moins un serveur à partir des sauvegardes, mesurer la durée de la restauration et la comparer au délai de reprise du paragraphe 3.3 ; vérifier la protection des sauvegardes contre l’effacement ou le chiffrement (Q8).

- Rédiger un plan d’action pour les vulnérabilités non corrigées : risque, mesure proposée, priorité, effort estimé.

#### Livrables et évaluation

<table>
<tr><th scope="row">Livrables</th><td>Rapport d’audit : analyse de risques, résultats avant et après correction, test de restauration, plan d’action</td></tr>
<tr><th scope="row">Échéance</th><td>Fin de projet, après le déploiement des services principaux ; synthèse présentée en soutenance</td></tr>
</table>

### 5.10 Mission M9 – Suivre le projet et rendre compte au client (BC 4.1)

Compétence évaluée. BC 4.1 : Mettre en œuvre des outils d’analyse de la solution informatique et des solutions de communication avec le client pour suivre les évolutions.

Contexte. M. Thomas Girard, interlocuteur de l’équipe projet, et M. Justin Case, DSI, veulent suivre l’avancement sans attendre la soutenance et pouvoir faire remonter leurs demandes. L’équipe met en place des outils de suivi et rend compte régulièrement.

#### Travail demandé

- Tenir dans le dépôt Git du projet un fichier README mis à jour à la fin de chaque séance : travail réalisé et par qui, état des exigences, difficultés rencontrées, prochaines étapes.

- Maintenir un tableau de suivi des exigences du chapitre 4 (non commencée, en cours, réalisée, validée), avec pour chaque exigence validée la preuve correspondante (capture, test, journal).

- Choisir et utiliser un outil de suivi partagé (tableau Kanban, tickets d’un dépôt Git, GLPI…) pour planifier les tâches et tracer les demandes.

- Faire un point d’avancement de 5 minutes avec le client à chaque séance encadrée, et consigner ses demandes et retours dans un registre : date, demande, décision, prise en compte.

- S’appuyer sur la supervision (V9) et sur le rapport d’activité de la mission M7 pour montrer au client l’état de l’infrastructure.

#### Livrables et évaluation

<table>
<tr><th scope="row">Livrables</th><td>README de séance ; tableau de suivi des exigences ; registre des échanges avec le client</td></tr>
<tr><th scope="row">Échéance</th><td>À chaque séance, tout au long du projet</td></tr>
</table>

### 5.11 Mission M10 – Planifier, déployer et recetter (BC 4.3)

Compétence évaluée. BC 4.3 : Déployer une solution informatique.

Contexte. La maquette doit servir de référence pour le déploiement réel. Le déploiement doit donc être planifié, reproductible et validé par une recette avant d’être présenté à la direction.

#### Travail demandé

- Établir un plan de déploiement : ordre d’installation selon les dépendances (réseau, pare-feu, annuaire, DNS et DHCP, services, supervision, sauvegarde), prérequis, durée estimée et points de contrôle.

- Documenter chaque installation sous forme de procédure reproductible (T2) et versionner les configurations dans un dépôt Git (équipements réseau, pare-feu, fichiers de configuration des serveurs), avec l’historique des modifications (T3).

- Automatiser au moins une partie du déploiement, par exemple la création des comptes en masse (PowerShell), la configuration d’un serveur Linux (script shell ou Ansible) ou l’application des stratégies de groupe (T5).

- Rédiger un cahier de recette reprenant les scénarios du paragraphe 4.4 : pour chacun, étapes, résultat attendu, résultat obtenu, preuve. Dérouler la recette avant la soutenance et corriger les écarts.

- Souhaitable : reconstruire un serveur uniquement à partir de la documentation et des scripts, et mesurer le temps nécessaire.

- Proposer un plan de bascule de la maquette vers le site réel : étapes, risques, possibilité de retour arrière.

#### Livrables et évaluation

<table>
<tr><th scope="row">Livrables</th><td>Plan de déploiement ; procédures et dépôt des configurations ; cahier de recette complété</td></tr>
<tr><th scope="row">Échéance</th><td>Plan au début du déploiement ; recette avant la soutenance ; démonstration en soutenance</td></tr>
</table>
