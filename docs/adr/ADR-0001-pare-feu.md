# ADR-0001 – Pare-feu de la maquette

Statut : proposé, à confirmer sur les ressources de la maquette.
Date : 2026-11-26.

## Contexte

Le cahier des charges impose OPNsense ou pfSense CE et exige OpenVPN, le cloisonnement en zones, NAT, journalisation et publication limitée des services. Aucun achat n’est autorisé. Les ressources de l’hôte ne sont pas encore connues.

## Décision proposée

Évaluer pfSense CE en premier sur la maquette, avec OPNsense comme alternative de secours. Le comparatif M3 donne un léger avantage provisoire à pfSense CE pour le dimensionnement initial et la documentation. Les deux solutions satisfont le besoin fonctionnel attendu.

## Alternatives

OPNsense : solution libre avec filtrage stateful, VLAN, OpenVPN, proxy et sauvegardes de configuration documentés. Son guide indique 4 Go comme configuration raisonnable pour toutes les fonctions standard.

pfSense CE : solution imposée comme choix permis par le brief, avec OpenVPN, VLAN, NAT, filtrage stateful et documentation détaillée. Le minimum publié de 1 Go/8 Go disque n’est pas considéré comme une taille recommandée pour la charge.

Solutions payantes ou VPN externes : rejetées car hors contraintes explicites du brief.

## Conséquences

Créer des règles par zone, appliquer le refus par défaut, documenter les flux autorisés, utiliser des comptes d’administration nominatifs, exporter les journaux et sauvegarder la configuration. Tester le débit OpenVPN et les ressources avant de figer le choix. Si l’image CE ou les ressources disponibles ne conviennent pas, remplacer la décision par OPNsense et consigner l’écart.

## Sources

https://docs.netgate.com/pfsense/en/latest/hardware/minimum-requirements.html
https://docs.netgate.com/pfsense/en/latest/hardware/size.html
https://docs.opnsense.org/manual/hardware.html
https://docs.opnsense.org/manual/vpnet.html
