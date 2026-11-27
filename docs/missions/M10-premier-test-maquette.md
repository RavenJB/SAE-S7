# M10 – Fiche du premier test de la maquette

Configuration proposée pour le [premier scénario](../maquette-et-tests.md#premier-scénario-à-reproduire). Utiliser trois réseaux virtuels isolés et des comptes fictifs. Le pare-feu sert de passerelle entre les VLAN.

## Adressage et rôles

Domaine AD proposé `ad.valdore-services.fr` (NetBIOS `VALDORE`). `DC-01` héberge AD DS et le DNS de la zone. Son client DNS pointe vers sa propre adresse.

| VLAN | Sous-réseau | Pare-feu | Machine et configuration |
| --- | --- | --- | --- |
| 10 · Utilisateurs | `10.20.10.0/24` | `10.20.10.1` | `PC-01` (Windows 11 Pro) reçoit un bail du pare-feu dans la plage `10.20.10.50` à `10.20.10.199`, avec `10.20.10.1` comme passerelle et `10.20.20.10` comme DNS. |
| 20 · Serveurs | `10.20.20.0/24` | `10.20.20.1` | `DC-01` (Windows Server) utilise l’adresse fixe `10.20.20.10` et la passerelle `10.20.20.1`. |
| 40 · Administration | `10.20.40.0/27` | `10.20.40.1` | Pour le contrôle d’administration, raccorder temporairement `PC-01` à ce VLAN et lui attribuer `10.20.40.10/27`. |

## Flux autorisés

- `PC-01` → pare-feu sur le VLAN 10 pour DHCP (UDP client `68`, serveur `67`, avec réponse en sens inverse).
- VLAN 10 → `DC-01` uniquement pour DNS et AD. Autoriser `53`, `88`, `389` et `464` en TCP/UDP, `123` en UDP, `135`, `445` et `49152–65535` en TCP pour la jonction et l’ouverture de session sur des versions Windows récentes. [Ports AD selon Microsoft](https://learn.microsoft.com/en-us/troubleshoot/windows-server/active-directory/config-firewall-for-ad-domains-and-trusts)
- VLAN 40 → `10.20.40.1` en HTTPS (`443/TCP`), avec un compte d’administration nominatif. Refuser et journaliser l’accès à l’administration du pare-feu depuis le VLAN 10. Bloquer les autres flux par défaut. Avec pfSense CE, affecter `LAN` à l’administration et remplacer les règles permissives par défaut. [Règle anti-verrouillage pfSense](https://docs.netgate.com/pfsense/en/latest/config/advanced-admin.html#anti-lockout)

## Résultats attendus et preuves

| Action | Résultat attendu et preuve à conserver |
| --- | --- |
| Ouvrir `https://10.20.40.1` depuis le VLAN 40. | Interface accessible. Conserver une capture après connexion. |
| Rebrancher `PC-01` sur le VLAN 10 et réactiver le DHCP. | `ipconfig /all` montre un bail dans la plage prévue, la passerelle et le DNS attendus. |
| Exécuter `Resolve-DnsName dc-01.ad.valdore-services.fr`. | Le nom renvoie `10.20.20.10`. Conserver la sortie. |
| Créer le compte standard `test.m10` dans AD. Joindre le poste au domaine avec un compte autorisé, redémarrer et ouvrir une session avec `test.m10`. | `whoami` affiche `valdore\test.m10`. Conserver la sortie. |
| Tester `Test-NetConnection 10.20.40.1 -Port 443` depuis le VLAN 10. | `TcpTestSucceeded` vaut `False`. Conserver la sortie et le blocage dans le journal du pare-feu. |

Source dans le sujet · [§5.11 — Plan de déploiement et cahier de recette](../SAE_Cyber_Valdore_Services.md#511-mission-m10--planifier-déployer-et-recetter-bc-43) et [§4.4 — Critères de validation](../SAE_Cyber_Valdore_Services.md#44-critères-de-validation).
