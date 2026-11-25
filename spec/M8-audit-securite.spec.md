# M8 – Auditer, fiabiliser et sécuriser

Compétence : **[BC 3.5 – Fiabiliser et sécuriser.](../docs/bloc-competences.md#bc-35---fiabiliser-et-sécuriser)** Le référentiel couvre l’identification et l’évaluation des vulnérabilités, les mesures d’atténuation, la protection des actifs et la vérification de la résilience.

## Problématique

Le marché de la Communauté d’agglomération Somme-Littoral comporte des clauses de sécurité. Avant la présentation au client, la direction demande un audit interne des vulnérabilités restantes, des mesures prises et de la capacité à reprendre après un incident.

## Solution

Réaliser une analyse de risques simplifiée, auditer uniquement la maquette, corriger les vulnérabilités prioritaires, recontrôler les corrections et tester une restauration complète.

## Histoires utilisateur

1. En tant que direction, je veux identifier les biens essentiels, afin de savoir ce que la sécurité doit protéger.
2. En tant que direction, je veux comprendre les scénarios de menace et les mesures associées, afin de relier les risques aux protections prévues.
3. En tant qu’équipe projet, nous voulons limiter les audits à la maquette, afin de rester dans le périmètre autorisé.
4. En tant que responsable sécurité, je veux connaître les services visibles depuis l’Internet simulé et le réseau utilisateur, afin de repérer les expositions inattendues.
5. En tant que responsable sécurité, je veux rechercher et classer les vulnérabilités des composants concernés, afin de traiter les risques selon leur gravité.
6. En tant que direction, je veux voir les résultats avant et après correction, afin d’évaluer l’effet des mesures.
7. En tant qu’administrateur, je veux restaurer intégralement au moins un serveur depuis les sauvegardes, afin de vérifier la capacité de reprise.
8. En tant que direction, je veux comparer la durée de restauration au délai de reprise attendu, afin d’identifier les écarts.
9. En tant que responsable sécurité, je veux vérifier que les sauvegardes résistent à l’effacement ou au chiffrement malveillant, afin de préserver une voie de récupération.
10. En tant que direction, je veux un plan pour les vulnérabilités non corrigées, avec risque, action, priorité et effort, afin de décider de leur traitement ultérieur.

## Décisions d’implémentation

- L’analyse simplifiée s’inspire d’EBIOS Risk Manager (ANSSI). Elle couvre les données clients, les données RH et la disponibilité des services. Pour chaque scénario de menace, elle indique les mesures correspondantes du cahier des charges. Le brief cite le rançongiciel, le hameçonnage, la compromission d’un compte VPN, la fuite de données et la panne d’un serveur.
- L’audit open source couvre les ports et services exposés depuis l’Internet simulé et le réseau des postes, la recherche de vulnérabilités, l’annuaire et les serveurs Linux. Le brief cite respectivement Nmap, Greenbone OpenVAS, PingCastle et Lynis. Le périmètre se limite à la maquette.
- Les corrections prioritaires s’appuient sur des recommandations ANSSI ou benchmarks CIS et sont suivies d’un nouvel audit.
- Le test de restauration compare la durée mesurée au [délai de reprise du §3.3](../docs/SAE_Cyber_Valdore_Services.md#33-volumétrie-et-niveau-de-service) : quelques heures pour la messagerie, les dossiers et l’annuaire, une journée pour le reste. Vérifier la protection des sauvegardes contre l’effacement et le chiffrement selon Q8.

## Décisions de test

- Vérifier que l’analyse relie biens, menaces et mesures de sécurité du cahier des charges.
- Vérifier que les quatre volets de l’audit couvrent uniquement la maquette et que les vulnérabilités sont classées par gravité.
- Comparer les constats avant/après et vérifier les éléments de preuve des corrections.
- Restaurer intégralement au moins un serveur à partir des sauvegardes et consigner sa durée, la comparaison avec le délai toléré et le résultat de la vérification Q8. Pour la recette M10, vérifier aussi la restauration d’un dossier et d’un compte de l’annuaire prévue au §4.4.
- Vérifier que le plan d’action couvre les vulnérabilités restantes avec les champs requis.

## Hors périmètre

- Scanner des systèmes réels ou des adresses hors maquette.
- Affirmer l’absence absolue de vulnérabilités après audit.
- Produire une certification ou un audit réglementaire formel.

## Notes complémentaires

Livrable : rapport d’audit avec analyse de risques, résultats avant/après, test de restauration et plan d’action. Échéance : fin de projet après déploiement des services principaux ; synthèse en soutenance.
