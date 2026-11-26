# ADR-0005 – Messagerie de la maquette

Statut : proposé, sous réserve de test d’intégration AD/LDAP.
Date : 2026-11-26.

## Contexte

Chaque salarié a une adresse `prenom.nom@valdore-services.fr` et doit pouvoir envoyer/recevoir des courriels depuis un client ou un webmail. La maquette simule les échanges externes et ne doit pas se connecter à Internet sans validation. Aucun achat n’est possible.

## Décision proposée

Retenir Modoboa pour l’évaluation initiale. La documentation 2.4.9 donne une base de 2 CPU, 2 Go de RAM et 10 Go de disque, ou 4 Go de RAM si l’antivirus est activé. La documentation décrit l’authentification LDAP. Il faut tester le bind LDAP chiffré vers l’AD et prévoir un processus explicite pour les changements et suppressions de comptes, car Modoboa ne synchronise pas automatiquement ces changements.

## Alternatives

Mailu 2.0 : stack complète, libre, légère selon la configuration antivirus ; la documentation précise que les versions stables anciennes ne reçoivent plus les correctifs et préconise de ne pas rester sur une branche ancienne.

mailcow : stack complète, webmail, fonctions de sécurité, LDAP/AD et procédures de sauvegarde ; plus riche, mais 6 Gio de RAM et 1 Gio de swap minimum dans la configuration par défaut.

## Conséquences

La décision reste conditionnelle à un test LDAP, au dimensionnement réel et à la validation de l’équipe enseignante. La recette couvrira SMTP interne, envoi vers un serveur externe simulé, IMAP/Webmail, TLS et restauration de boîtes. Le DNS de laboratoire, les certificats et les ports seront simulés/isolés ; aucun trafic de courrier réel ne doit partir vers Internet.

## Sources

https://modoboa.readthedocs.io/en/latest/installation/requirements.html
https://modoboa.readthedocs.io/en/2.4.2/configuration.html
https://mailu.io/2.0/setup.html
https://docs.mailcow.email/getstarted/prerequisite-system/
