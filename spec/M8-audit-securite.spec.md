# M8 – Auditer, fiabiliser et sécuriser

Compétence : **BC 3.5 – Fiabiliser et sécuriser.** Le référentiel couvre l’identification et l’évaluation des vulnérabilités, les mesures d’atténuation, la protection des actifs et la vérification de la résilience.

## Problématique

Avant la présentation au client, l’équipe doit connaître les risques restants, vérifier la sécurité de la maquette et démontrer qu’un service peut être restauré après incident.

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

- L’analyse s’inspire de la démarche EBIOS Risk Manager sans prétendre à une analyse exhaustive ou certifiante.
- Les tests d’exposition et d’audit se limitent à la maquette, avec les familles d’outils citées dans le brief ou leurs équivalents open source retenus.
- Les corrections prioritaires s’appuient sur des recommandations ANSSI ou benchmarks CIS et sont suivies d’un nouvel audit.
- Le test de restauration mesure la durée et la compare au délai de reprise du paragraphe 3.3 ; la protection des sauvegardes est examinée au regard de Q8.

## Décisions de test

- Vérifier que l’analyse relie biens, menaces et mesures de sécurité du cahier des charges.
- Confirmer que les scans ont comme cible uniquement les systèmes de la maquette et que les résultats sont classés par gravité.
- Comparer les constats avant/après et vérifier les éléments de preuve des corrections.
- Réaliser une restauration complète observée, mesurer sa durée et la comparer explicitement au délai toléré.
- Vérifier que le plan d’action couvre les vulnérabilités restantes avec les champs requis.

## Hors périmètre

- Scanner des systèmes réels ou des adresses hors maquette.
- Affirmer l’absence absolue de vulnérabilités après audit.
- Produire une certification ou un audit réglementaire formel.

## Notes complémentaires

Livrable : rapport d’audit avec analyse de risques, résultats avant/après, test de restauration et plan d’action. Échéance : fin de projet après déploiement des services principaux ; synthèse en soutenance.
