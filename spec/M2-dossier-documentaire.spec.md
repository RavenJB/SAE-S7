# M2 – Constituer un dossier documentaire

Compétence : **[BC 1.8 – Effectuer une recherche documentaire.](../docs/bloc-competences.md#bc-18---effectuer-une-recherche-documentaire)** Le référentiel couvre l’identification et l’utilisation d’outils de recherche pertinents, la sélection rapide des documents utiles, leur synthèse et, selon le niveau, leur critique.

## Problématique

La direction doit pouvoir vérifier que les choix techniques reposent sur des références reconnues et actuelles. Le futur administrateur doit également savoir retrouver les informations de référence.

## Solution

Constituer un dossier commenté d’au moins quinze références, organisé par domaine, retraçant la recherche et justifiant la fiabilité et l’utilité des sources retenues ou écartées.

## Histoires utilisateur

1. En tant que direction, je veux consulter des références fiables, afin de vérifier les choix techniques du projet.
2. En tant que futur administrateur, je veux retrouver la documentation officielle des composants retenus, afin de maintenir l’infrastructure.
3. En tant que membre de l’équipe, je veux connaître, pour chaque domaine, les mots-clés et requêtes employés en français et en anglais, afin de rendre la recherche reproductible.
4. En tant que lecteur, je veux que les références soient classées par domaine, afin de trouver rapidement un sujet réseau, annuaire, messagerie, sauvegarde, supervision ou sécurité.
5. En tant que lecteur, je veux connaître pour chaque référence son titre, son auteur ou éditeur, sa date ou version et son lien, afin de la retrouver sans ambiguïté.
6. En tant que lecteur, je veux comprendre la fiabilité et l’apport de chaque source, afin d’évaluer son utilité pour le projet.
7. En tant que responsable des exigences, je veux voir les exigences concernées par chaque référence, afin de relier la recherche aux besoins de la maquette.
8. En tant que futur administrateur, je veux connaître les sources écartées et les raisons, afin d’éviter les documents obsolètes, non officiels ou hors version.
9. En tant qu’équipe projet, nous voulons citer les références dans la documentation d’infrastructure et les matrices de choix, afin de garder les décisions traçables.

## Décisions d’implémentation

- Le dossier compte au moins quinze références et couvre les six domaines explicitement cités.
- Les sources privilégiées sont les documentations officielles, publications ANSSI/CERT-FR, benchmarks CIS, RFC, bases CVE et calendriers de fin de support des logiciels retenus (Q6).
- Au moins un référentiel reconnu, par exemple le guide d’hygiène informatique de l’ANSSI ou les benchmarks CIS, est utilisé pour les choix de sécurité (T4).
- Chaque entrée comporte les métadonnées, une appréciation de fiabilité, un apport en une ou deux phrases et les exigences concernées.
- Les recherches sont documentées dans les deux langues ; les sources rejetées et leur motif sont conservés.

## Décisions de test

- Contrôler qu’il y a au moins quinze références et que chaque domaine demandé comporte des références, des mots-clés et des requêtes en français et en anglais.
- Vérifier la présence de tous les champs requis par référence et la validité des liens.
- Repérer les sources retenues pour vérifier la durée de support des logiciels (Q6) et le référentiel utilisé pour justifier les choix de sécurité (T4).
- Vérifier que les exigences citées existent au chapitre 4 et que les références sont reprises dans les documents de choix et d’infrastructure pertinents.
- La revue porte sur le dossier livré, pas sur un outil logiciel.

## Hors périmètre

- Produire une revue exhaustive de toute la littérature cybersécurité.
- Garantir la pérennité des liens au-delà du projet.
- Remplacer l’analyse des choix de la mission M3.

## Notes complémentaires

Livrable : dossier documentaire commenté en annexe du rapport final. Première version à la fin de la deuxième séance encadrée ; version finale avec le rapport.
