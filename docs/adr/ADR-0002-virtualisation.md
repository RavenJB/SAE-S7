# ADR-0002 – Plateforme de virtualisation

Statut : proposé sous condition de disponibilité d’un serveur scolaire dédié.
Date : 2026-11-26.

## Contexte

La maquette comporte de nombreuses zones virtuelles raccordées à un pare-feu et, si possible, au Catalyst 3750. Le brief autorise VirtualBox, VMware ou Proxmox VE et indique que des serveurs de l’école peuvent héberger une partie des machines. Ce matériel n’est pas encore attribué.

## Décision proposée

Retenir Proxmox VE si un hôte dédié et son accès d’administration sont fournis. Ses bridges, VLAN 802.1Q, pare-feu et fonctions de sauvegarde sont adaptés à une maquette multi-VM raccordée à des équipements réels.

## Alternatives

VirtualBox est le choix de repli sur poste de travail : libre, facile d’accès, et doté de réseaux internes, Host-only, NAT et bridged. Le passage de trunks VLAN vers une carte physique reste à valider.

VMware Workstation Pro est gratuit pour les usages commerciaux, éducatifs et personnels depuis l’annonce officielle de novembre 2024. Il fonctionne sur poste de travail, mais ne propose pas ici un avantage décisif par rapport aux deux autres candidats.

## Conséquences

Le choix n’est pas définitif tant que l’hôte scolaire n’est pas confirmé. Avant le déploiement, mesurer les ressources disponibles et tester l’isolation des réseaux. En l’absence de serveur, rouvrir cet ADR et la matrice M3, et choisir un hyperviseur de poste de travail.

## Sources

https://pve.proxmox.com/pve-docs/pve-admin-guide.pdf
https://download.virtualbox.org/virtualbox/7.2.10/UserManual.pdf
https://blogs.vmware.com/cloud-foundation/2024/11/11/vmware-fusion-and-workstation-are-now-free-for-all-users/
