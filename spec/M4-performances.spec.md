# M4 – Mesurer et optimiser les performances

Compétence : **[BC 3.2 – Assurer et optimiser les performances des systèmes d’information.](../docs/bloc-competences.md#bc-32---assurer-et-optimiser-les-performances-des-systèmes-dinformation)** Le référentiel vise l’observation des performances, l’identification des limites et l’amélioration mesurée de la solution.

## Problématique

La maquette dispose de ressources limitées. Le dimensionnement doit tenir compte d’environ 35 télétravailleurs simultanés, d’une fin des sauvegardes avant 7 h et d’une croissance d’effectif estimée à 25 % en trois ans.

## Solution

Définir et superviser des indicateurs, mesurer un état de référence et des charges représentatives, corriger un facteur limitant puis comparer les résultats et projeter l’évolution.

## Histoires utilisateur

1. En tant que direction, je veux connaître l’utilisation du processeur et de la mémoire, l’espace disque et le débit réseau de chaque serveur et équipement, afin de repérer les saturations.
2. En tant qu’administrateur, je veux suivre le temps de réponse du webmail et de l’extranet, le nombre de sessions VPN et la durée des sauvegardes, afin d’observer les services clés.
3. En tant qu’administrateur, je veux des seuils d’alerte dans la supervision, afin d’être averti d’une dégradation.
4. En tant que lecteur du rapport, je veux disposer d’une mesure de référence de la maquette au repos et connaître les outils employés, afin de contextualiser les résultats.
5. En tant que direction, je veux voir au moins deux tests de charge représentatifs, afin d’évaluer le comportement sous activité.
6. En tant que direction, je veux connaître le facteur limitant observé et la solution proposée, afin de comprendre les actions d’optimisation.
7. En tant que direction, je veux comparer des mesures après optimisation à la référence, afin d’évaluer l’effet des actions.
8. En tant que responsable des sauvegardes, je veux vérifier que la sauvegarde nocturne tient entre 20 h et 7 h, afin de respecter la fenêtre d’exploitation.
9. En tant que direction, je veux une estimation du comportement avec 25 % d’utilisateurs supplémentaires, afin d’éclairer la capacité à trois ans.
10. En tant que jury, je veux voir un tableau de bord en soutenance, afin de relier les mesures aux indicateurs opérationnels.

## Décisions d’implémentation

- Intégrer les indicateurs de ressources et de services à la supervision (V9) avec des seuils d’alerte.
- Mesurer au moins deux charges représentatives. Exemples du brief : connexions VPN simultanées avec mesure du débit, requêtes en nombre sur l’extranet, copie de fichiers volumineux sur les partages, sauvegarde complète puis incrémentale. La montée en charge peut être simulée par des scripts.
- Une optimisation est suivie d’une mesure comparable à la référence.
- La projection à trois ans est une estimation explicitée, pas une garantie de capacité en environnement réel.

## Décisions de test

- Vérifier qu’une référence au repos, au moins deux charges, l’identification d’un facteur limitant et une mesure après optimisation sont documentées.
- Vérifier que les outils, conditions de mesure et unités sont indiqués pour rendre la comparaison interprétable.
- Vérifier dans la supervision la présence des indicateurs et des seuils d’alerte.
- Vérifier que la durée mesurée de la sauvegarde nocturne tient dans la fenêtre 20 h–7 h et expliciter les hypothèses de la projection avec 25 % d’utilisateurs supplémentaires.
- Présenter le tableau de bord de supervision en soutenance.

## Hors périmètre

- Garantir les performances du futur déploiement réel à partir d’une maquette limitée.
- Ajouter des composants ou capacités payants, incompatibles avec les contraintes budgétaires.
- Optimiser sans mesure avant/après.

## Notes complémentaires

Le rapport final inclut le rapport de performance avec les indicateurs, les mesures avant et après, les optimisations et la projection à trois ans. Le tableau de bord de supervision est présenté en soutenance.
