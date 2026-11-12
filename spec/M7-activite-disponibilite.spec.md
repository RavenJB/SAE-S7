# M7 – Analyser l’activité et la disponibilité du SI

Compétence : **BC 3.1 – Analyser une solution informatique et en mesurer les performances avec des outils et métriques adaptés.** Le référentiel associe l’analyse à des indicateurs couvrant notamment réseaux, systèmes, données et sécurité, ainsi qu’à l’interprétation des observations.

## Problématique

La direction souhaite des éléments factuels sur l’usage des services, leur disponibilité, les accès et les événements de sécurité. Ces mesures alimentent l’optimisation M4 et l’audit M8.

## Solution

Recenser les sources, choisir une dizaine de métriques, collecter des mesures pendant une séance représentative, analyser une capture réseau et présenter les résultats avec leur interprétation.

## Histoires utilisateur

1. En tant que direction, je veux savoir quelles sources de mesure existent, afin de comprendre d’où viennent les constats.
2. En tant qu’administrateur, je veux exploiter la supervision et les journaux pertinents, afin d’observer l’activité des services.
3. En tant que direction, je veux une dizaine de métriques réparties entre réseau, systèmes, données et sécurité, afin d’avoir une vue équilibrée.
4. En tant qu’administrateur, je veux mesurer la disponibilité et les temps de réponse, afin d’identifier les interruptions et lenteurs.
5. En tant que responsable sécurité, je veux suivre les sessions VPN, échecs d’authentification et flux refusés, afin de repérer des événements inhabituels.
6. En tant que responsable réseau, je veux mesurer latence, débit et volumes d’échange, afin d’observer l’usage entre zones et des partages.
7. En tant que lecteur, je veux connaître les conditions et la période de collecte, afin de juger si les données sont représentatives.
8. En tant que lecteur, je veux voir l’analyse commentée d’une capture d’un échange choisi, afin de vérifier les protocoles et le chiffrement.
9. En tant que direction, je veux une interprétation des anomalies et tendances, afin de décider des améliorations utiles.
10. En tant que responsable de M4, je veux recevoir les premières pistes de performance, afin de les reprendre dans l’étude d’optimisation.

## Décisions d’implémentation

- Les sources à considérer incluent la supervision, les journaux du pare-feu, proxy et VPN, les événements de connexion AD et les journaux web, extranet et messagerie.
- Une dizaine de métriques est choisie parmi les domaines indiqués dans le brief ; la liste finale reste à adapter à la maquette réellement déployée.
- Une activité représentative est générée et collectée pendant au moins une séance.
- La capture est limitée à un échange choisi sur la maquette et sert à vérifier protocoles et chiffrement, pas à capturer des données personnelles réelles.

## Décisions de test

- Vérifier que les métriques couvrent réseau, systèmes, accès aux données et sécurité, et que leur source est identifiée.
- Refaire une collecte représentative et vérifier que les valeurs présentées proviennent des sources nommées.
- Contrôler que la capture commentée identifie l’échange, les protocoles observés et le constat relatif au chiffrement.
- Vérifier que le rapport présente valeurs, tendances, anomalies, interprétation et pistes transmises à M4.

## Hors périmètre

- Surveillance continue au-delà de la période de projet.
- Collecte de trafic hors de la maquette autorisée.
- Remplacer l’optimisation de M4 ou l’audit de sécurité de M8.

## Notes complémentaires

Livrables : rapport d’activité et de disponibilité avec métriques, capture commentée et interprétation ; point oral sur les premières mesures. Échéance : premières mesures en cours de projet, rapport final et soutenance.
