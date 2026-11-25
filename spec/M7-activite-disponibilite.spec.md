# M7 – Analyser l’activité et la disponibilité du SI

Compétence : **[BC 3.1 – Analyser une solution informatique et en mesurer les performances avec des outils et métriques adaptés.](../docs/bloc-competences.md#bc-31---analyser-une-solution-informatique-et-en-mesurer-les-performances-en-utilisant-les-outils-et-métriques-adaptés-réseaux-systèmes-accès-aux-données-sécurité-etc)** Le référentiel associe l’analyse à des indicateurs couvrant notamment réseaux, systèmes, données et sécurité, ainsi qu’à l’interprétation des observations.

## Problématique

La direction souhaite savoir quels services sont utilisés, par qui et d’où, avec quelle disponibilité, et quels événements de sécurité surviennent. Ces mesures alimentent l’optimisation M4 et l’audit M8.

## Solution

Recenser les sources, choisir une dizaine de métriques, collecter des mesures pendant une séance représentative, analyser une capture réseau et présenter les résultats avec leur interprétation.

## Histoires utilisateur

1. En tant que direction, je veux savoir quelles sources de mesure existent, afin de comprendre d’où viennent les constats.
2. En tant qu’administrateur, je veux exploiter la supervision et les journaux pertinents, afin d’observer l’activité des services.
3. En tant que direction, je veux une dizaine de métriques réparties entre réseau, systèmes, données et sécurité, afin d’avoir une vue équilibrée.
4. En tant qu’administrateur, je veux suivre la disponibilité et l’activité des services à l’aide des métriques retenues, afin d’identifier les interruptions et lenteurs.
5. En tant que responsable sécurité, je veux observer les événements de sécurité, afin de repérer une activité inhabituelle.
6. En tant que responsable réseau, je veux comprendre les usages du réseau et des partages, afin d’interpréter l’activité entre zones et l’accès aux données.
7. En tant que lecteur, je veux connaître les conditions et la période de collecte, afin de juger si les données sont représentatives.
8. En tant que lecteur, je veux voir l’analyse commentée d’une capture d’un échange choisi, afin de vérifier les protocoles et le chiffrement.
9. En tant que direction, je veux une interprétation des anomalies et tendances, afin de décider des améliorations utiles.
10. En tant que responsable de M4, je veux recevoir les premières pistes de performance, afin de les reprendre dans l’étude d’optimisation.

## Décisions d’implémentation

- Recenser les sources disponibles : supervision (V9), journaux du pare-feu, du proxy et du VPN, événements de connexion des contrôleurs de domaine et journaux du serveur web, de l’extranet et de la messagerie.
- Choisir une dizaine de métriques adaptées à la maquette. Exemples : taux de disponibilité par service, temps de réponse, latence et débit entre zones, sessions VPN simultanées, volume des échanges sur les partages, sites les plus consultés et requêtes bloquées par le proxy, échecs d’authentification et flux refusés par le pare-feu.
- Générer une activité représentative sur la maquette et collecter les métriques pendant au moins une séance.
- Analyser avec Wireshark ou tcpdump la capture d’un échange de la maquette, par exemple une ouverture de session sur le domaine ou une connexion VPN, pour en vérifier les protocoles et le chiffrement (Q4). Utiliser les données fictives de la maquette.
- Présenter les résultats dans un tableau de bord ou dans le rapport d’activité et de disponibilité à remettre.

## Décisions de test

- Vérifier que les métriques couvrent réseau, systèmes, accès aux données et sécurité, et que leur source est identifiée.
- Vérifier que les valeurs présentées proviennent des sources indiquées et couvrent au moins une séance d’activité représentative sur la maquette.
- Pour observer V7 et V9, s’appuyer sur les scénarios de recette du §4.4 : navigation d’un poste avec traces consultables et arrêt volontaire d’un service avec alerte visible dans la supervision.
- Contrôler que la capture commentée identifie l’échange, les protocoles observés et le constat relatif au chiffrement.
- Vérifier que la présentation des résultats inclut valeurs mesurées, tendances, anomalies et interprétation, et que les pistes d’amélioration ont été transmises à M4.

## Hors périmètre

- Surveillance continue au-delà de la période de projet.
- Collecte de trafic hors de la maquette autorisée.
- Remplacer l’optimisation de M4 ou l’audit de sécurité de M8.

## Notes complémentaires

Livrables : rapport d’activité et de disponibilité avec métriques, capture commentée et interprétation ; point oral sur les premières mesures. Échéance : premières mesures en cours de projet, rapport final et soutenance.
