# M3 – Comparer et sélectionner les solutions

Compétence : **BC 2.2 – Étudier, comparer et sélectionner les outils et méthodes nécessaires à la conception, au développement et au test d’une solution informatique.** Le référentiel demande d’identifier des options, de comparer leurs avantages et limites selon des critères liés au projet, puis de justifier la sélection.

## Problématique

Le brief laisse plusieurs choix techniques ouverts. Avant le déploiement, le client a besoin de comprendre pourquoi les solutions retenues répondent aux besoins, contraintes et ressources disponibles.

## Solution

Réaliser des comparaisons structurées d’au moins cinq choix importants, présenter les matrices de décision et défendre les conclusions lors d’une revue orale de dix minutes.

## Histoires utilisateur

1. En tant que client, je veux voir plusieurs candidats pour chaque choix structurant, afin de comprendre les alternatives considérées.
2. En tant que client, je veux que le pare-feu soit comparé entre OPNsense et pfSense CE, afin de justifier le choix imposé par le cahier des charges.
3. En tant que client, je veux comparer des plateformes de virtualisation, afin de comprendre leur adéquation aux ressources de la maquette.
4. En tant que client, je veux comparer les solutions de sauvegarde et NAS, afin de comprendre comment les données critiques seront protégées.
5. En tant que client, je veux comparer les solutions de supervision, afin de comprendre comment les équipements et services seront suivis.
6. En tant que client, je veux qu’au moins un choix supplémentaire porte sur un domaine autorisé, afin que l’étude couvre un autre service important.
7. En tant que lecteur, je veux que les critères et leurs poids soient définis avant la notation, afin que la comparaison soit explicite.
8. En tant que client, je veux que les critères tiennent compte des besoins, contraintes, sécurité, support, compatibilité, ressources, exploitation et documentation, afin que la décision soit adaptée au contexte réel.
9. En tant que client, je veux voir notes, poids et total dans une matrice, afin de comparer les candidats de façon cohérente.
10. En tant que client, je veux connaître la solution retenue et les raisons d’écarter les autres, afin de valider les choix avant le déploiement.
11. En tant qu’équipe projet, nous voulons présenter et défendre les résultats en dix minutes, afin de recueillir un retour avant de construire les services.

## Décisions d’implémentation

- L’étude couvre au moins cinq choix, avec les quatre domaines obligatoires du brief et au moins un domaine supplémentaire sélectionné dans la liste proposée.
- Chaque comparaison utilise une matrice avec critères, poids, notes et total ; les pondérations sont explicitées avant l’évaluation des candidats.
- Les décisions respectent les contraintes du chapitre 4.1 et se rattachent aux besoins du chapitre 3.
- Aucun candidat ni résultat de comparaison n’est préjugé par cette spécification.

## Décisions de test

- Vérifier le nombre et la couverture obligatoire des comparaisons.
- Pour chaque matrice, contrôler que les poids, notes et totaux sont cohérents et que la conclusion découle des critères exposés.
- Vérifier que les solutions écartées ont une raison documentée et que les contraintes de budget, licences et compatibilité sont traitées.
- La revue orale de dix minutes constitue la validation de communication de cette étude.

## Hors périmètre

- Déployer ou benchmarker en production tous les candidats.
- Retenir automatiquement le candidat ayant la meilleure note sans analyse des contraintes.
- Présenter les choix comme imposés lorsqu’ils sont laissés au groupe.

## Notes complémentaires

Livrables : matrices de choix et revue orale de dix minutes. Échéance : mi-projet, avant le déploiement des services.
