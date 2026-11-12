# M4 – Mesurer et optimiser les performances

Compétence : **BC 3.2 – Assurer et optimiser les performances des systèmes d’information.** Le référentiel vise l’observation des performances, l’identification des limites et l’amélioration mesurée de la solution.

## Problématique

La maquette dispose de ressources limitées, doit représenter jusqu’à 35 télétravailleurs simultanés, terminer les sauvegardes avant 7 h et donner une projection face à une croissance d’effectif de 25 % en trois ans.

## Solution

Définir et superviser des indicateurs, mesurer un état de référence et des charges représentatives, corriger un facteur limitant puis comparer les résultats et projeter l’évolution.

## Histoires utilisateur

1. En tant que direction, je veux connaître l’usage CPU, mémoire, disque et réseau des équipements, afin de repérer les saturations.
2. En tant qu’administrateur, je veux suivre le temps de réponse du webmail et de l’extranet, les sessions VPN et la durée des sauvegardes, afin d’observer les services clés.
3. En tant qu’administrateur, je veux des seuils d’alerte dans la supervision, afin d’être averti d’une dégradation.
4. En tant que lecteur du rapport, je veux disposer d’une mesure de référence de la maquette au repos et connaître les outils employés, afin de contextualiser les résultats.
5. En tant que direction, je veux voir au moins deux tests de charge représentatifs, afin d’évaluer le comportement sous activité.
6. En tant que direction, je veux connaître le facteur limitant observé et la solution proposée, afin de comprendre les actions d’optimisation.
7. En tant que direction, je veux comparer des mesures après optimisation à la référence, afin d’évaluer l’effet des actions.
8. En tant que responsable des sauvegardes, je veux vérifier que la sauvegarde nocturne tient entre 20 h et 7 h, afin de respecter la fenêtre d’exploitation.
9. En tant que direction, je veux une estimation du comportement avec 25 % d’utilisateurs supplémentaires, afin d’éclairer la capacité à trois ans.
10. En tant que jury, je veux voir un tableau de bord en soutenance, afin de relier les mesures aux indicateurs opérationnels.

## Décisions d’implémentation

- Les indicateurs comprennent les ressources de chaque serveur et équipement ainsi que les services explicitement cités.
- Au moins deux charges sont mesurées ; les exemples du brief (VPN, requêtes web, transferts de fichiers, sauvegardes) guident le choix sans imposer un outil particulier.
- Une optimisation est suivie d’une mesure comparable à la référence.
- La projection à trois ans est une estimation explicitée, pas une garantie de capacité en environnement réel.

## Décisions de test

- Vérifier qu’une référence au repos, au moins deux charges, l’identification d’un facteur limitant et une mesure après optimisation sont documentées.
- Vérifier que les outils, conditions de mesure et unités sont indiqués pour rendre la comparaison interprétable.
- Comparer la durée mesurée ou estimée de sauvegarde à la fenêtre 20 h–7 h et expliciter l’hypothèse de croissance.
- Vérifier l’existence d’un tableau de bord présenté en soutenance.

## Hors périmètre

- Garantir les performances du futur déploiement réel à partir d’une maquette limitée.
- Ajouter des composants ou capacités payants, incompatibles avec les contraintes budgétaires.
- Optimiser sans mesure avant/après.

## Notes complémentaires

Livrables : rapport de performance et tableau de bord. Échéance : rapport final et soutenance.
