# M9 – Suivre le projet et rendre compte au client

Compétence : **[BC 4.1 – Mettre en œuvre des outils d’analyse de la solution et des moyens de communication avec le client pour suivre les évolutions.](../docs/bloc-competences.md#bc-41---mettre-en-œuvre-des-outils-danalyse-de-la-solution-informatique-et-des-solutions-de-communication-avec-le-client-pour-suivre-les-évolutions)** Le référentiel met l’accent sur le suivi régulier, la collecte des retours et leur prise en compte.

## Problématique

Thomas Girard, directeur administratif et financier et interlocuteur de l’équipe projet, et Justin Case veulent suivre l’avancement pendant le projet, faire remonter leurs demandes et comprendre l’état de l’infrastructure avant la soutenance.

## Solution

Mettre à jour les outils de suivi à chaque séance, tracer l’état des exigences et les demandes client, puis appuyer les échanges sur les données de supervision et le rapport M7.

## Histoires utilisateur

1. En tant que client, je veux un compte rendu de chaque séance, afin de connaître les travaux réalisés et leur responsable.
2. En tant que client, je veux connaître les difficultés et prochaines étapes, afin d’anticiper les décisions nécessaires.
3. En tant que client, je veux suivre l’état des exigences du chapitre 4, afin de savoir ce qui reste à faire.
4. En tant que client, je veux voir une preuve associée à chaque exigence validée, afin de distinguer une déclaration d’une validation démontrée.
5. En tant qu’équipe, nous voulons utiliser un outil de suivi partagé, afin de répartir les tâches et tracer les demandes.
6. En tant que client, je veux faire un point d’avancement de cinq minutes à chaque séance encadrée, afin d’échanger régulièrement avec l’équipe.
7. En tant que client, je veux que mes demandes et retours soient enregistrés avec une décision et leur prise en compte, afin d’en suivre le traitement.
8. En tant que client, je veux voir l’état mesuré de l’infrastructure, afin que le suivi reflète son fonctionnement réel.
9. En tant qu’équipe projet, nous voulons utiliser le rapport M7 et la supervision pour le point client, afin de présenter des éléments observables.

## Décisions d’implémentation

- Le README du dépôt Git est mis à jour à la fin de chaque séance et précise les travaux et leurs auteurs, l’état des exigences, les difficultés rencontrées et les prochaines étapes.
- Le tableau suit les exigences du chapitre 4 avec les états non commencée, en cours, réalisée ou validée. Une preuve (capture, test ou journal, par exemple) accompagne chaque validation.
- L’équipe choisit et utilise un outil partagé, par exemple un tableau Kanban, les tickets d’un dépôt Git ou GLPI, pour planifier les tâches et tracer les demandes.
- Un registre des échanges conserve date, demande, décision et prise en compte.
- Présenter au client l’état de l’infrastructure à partir de la supervision (V9) et du rapport d’activité M7 dès qu’il est disponible.

## Décisions de test

- Examiner les comptes rendus des séances pour vérifier la présence des informations demandées et leur actualisation.
- Vérifier que chaque exigence validée dispose d’une preuve identifiable et que les états utilisent les catégories définies. Réutiliser les preuves des scénarios de recette du §4.4 lorsqu’elles s’appliquent.
- Vérifier que les tâches sont planifiées dans l’outil partagé et que les demandes y sont traçables.
- Vérifier que demandes client, décisions et état de prise en compte sont traçables.
- Vérifier que le point de cinq minutes a lieu à chaque séance encadrée et que l’état technique présenté s’appuie sur la supervision et le rapport M7 dès qu’il est disponible.

## Hors périmètre

- Imposer un outil de suivi particulier parmi ceux laissés au choix.
- Présenter comme validée une exigence sans preuve.
- Remplacer le dialogue régulier par un unique bilan final.

## Notes complémentaires

Livrables : README de séance, tableau de suivi des exigences et registre des échanges avec le client. Échéance : à chaque séance, tout au long du projet.
