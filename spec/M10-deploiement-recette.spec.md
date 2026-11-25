# M10 – Planifier, déployer et recetter

Compétence : **[BC 4.3 – Déployer une solution informatique.](../docs/bloc-competences.md#bc-43---déployer-une-solution-informatique)** Le référentiel couvre la préparation et l’exécution du déploiement, la documentation des procédures, la gestion des configurations et des versions, ainsi que les vérifications après installation.

## Problématique

La maquette doit servir de référence au déploiement réel. Sans plan, procédures reproductibles et recette, l’équipe ne peut démontrer que l’installation est cohérente ni proposer une transition maîtrisée.

## Solution

Planifier les dépendances, documenter et versionner la configuration, automatiser une partie du travail, dérouler les scénarios de recette et proposer un plan de bascule avec retour arrière.

## Histoires utilisateur

1. En tant qu’équipe de déploiement, nous voulons connaître l’ordre des installations, afin de respecter les dépendances entre réseau, pare-feu, annuaire, DNS et DHCP, services, supervision et sauvegarde.
2. En tant qu’administrateur, je veux connaître les prérequis, durées estimées et points de contrôle, afin de préparer chaque étape.
3. En tant que futur administrateur, je veux une procédure reproductible pour chaque installation, afin de pouvoir reconstruire la solution.
4. En tant que client, je veux que les configurations soient versionnées et que leurs changements soient traçables, afin de comprendre l’évolution et revenir sur une modification.
5. En tant qu’équipe projet, nous voulons automatiser au moins une tâche répétitive, afin de rendre cette partie du déploiement plus cohérente.
6. En tant que jury, je veux un cahier de recette aligné sur les scénarios du paragraphe 4.4, afin de vérifier les besoins annoncés.
7. En tant que client, je veux voir pour chaque scénario les étapes, résultats attendus et obtenus et les preuves, afin d’évaluer objectivement la recette.
8. En tant qu’équipe, nous voulons corriger les écarts constatés avant la soutenance, afin que la démonstration reflète l’état final de la maquette.
9. Souhaitable : en tant que futur administrateur, je peux reconstruire un serveur uniquement avec la documentation et les scripts, puis mesurer le temps nécessaire.
10. En tant que direction, je veux un plan de bascule vers le site réel avec risques et retour arrière, afin de comprendre comment maîtriser la transition.

## Décisions d’implémentation

- Le plan suit les dépendances citées par le brief ; le groupe définit les durées et points de contrôle selon son architecture.
- La documentation permet de reconstruire la maquette avec le schéma, l’adressage, les flux autorisés, les procédures de chaque installation et les comptes (T2).
- Versionner dans Git les configurations des équipements réseau, du pare-feu et des serveurs. Tracer la date, l’auteur et l’objet de chaque modification, et sauvegarder les configurations avant toute intervention (T3).
- Automatiser au moins une partie du déploiement pour M10. T5 reste souhaitable à l’échelle du projet.
- Le cahier de recette reprend tous les [scénarios du §4.4](../docs/SAE_Cyber_Valdore_Services.md#44-critères-de-validation) et conserve les résultats réellement obtenus.
- Pour le scénario Windows et Linux, vérifier l’ouverture de session et les droits d’accès sur les deux postes. L’intégration du poste Linux à l’authentification centralisée reste souhaitable (S4).
- Le plan de bascule comprend les étapes, les risques et la possibilité de retour arrière.

## Décisions de test

- Vérifier que le plan présente ordre, prérequis, durée et points de contrôle des étapes.
- Faire exécuter une procédure à partir de sa documentation et vérifier que les résultats attendus sont obtenus.
- Vérifier que l’automatisation sélectionnée réalise la tâche annoncée et que ses effets sont contrôlables.
- Dérouler tous les scénarios du §4.4 sur la maquette avant la soutenance. Consigner pour chacun les étapes, le résultat attendu, le résultat obtenu et la preuve. Corriger les écarts et vérifier les corrections.
- Examiner le plan de bascule pour confirmer que risques et retour arrière sont décrits.

## Hors périmètre

- Déployer ou basculer effectivement l’infrastructure du site réel.
- Présenter un scénario non exécuté comme une recette réussie.

## Notes complémentaires

Livrables : plan de déploiement, procédures et dépôt des configurations, cahier de recette complété. Plan au début du déploiement ; recette avant la soutenance ; démonstration en soutenance.
