# Proxmox

## Migration d'une infrastructure physique en infrastructure virtualisée

### Etape 1 - installation de l'hyperviseur
Installation en barre metal de proxmox sur un PC portable
utilisation du Disque Dur en entier
IP en DHCP de la seule carte reseau reconnue

### Etape 2 - Configuration du reseau de l'hyperviseur

> vmbr0 est créé automatiquement à l'installation et lié à la carte réseau physique pour l'interface d administration

création de deux vSwitch supplémentaires pour isoler les reseaux : 

- vmbr1 pour le serveur de données et les deux machines Ubuntu et Zorin
- vmbr2 pour le serveur de backup et les deux machines Ubuntu et Zorin

<p align="center">
<img src="/Images/Shema reseaux 1.jpg">
</p>

### Etape 3 - Creation des VMs

1. Creation du serveur de Données sous l'OS Open Media Vault
    1. Configuaration materielle
       - 2 vCPU
       - 2 Go de vRAM
       - 8 Go de vDisk System
       - 130 Go de vDisk de Stockage
       - 1 carte reseau sur vmbr1
    2. Installation de l'OS Open Media Vault
       - montage de l'ISO téléchargé
       - installation sur le disque de 8 Go
       - ajout du disque de 130Go pour le stockage
2. Creation du serveur de Backup sous l'OS Proxmox Backup Serveur
   1. Configuration materielle
       - 2 vCPU
       - 2 Go de vRAM
       - 16 Go de vDisk System
       - 32 Go de vDisk de Stockage
       - 1 carte reseau sur vmbr2
       - 1 carte reseau sur vmbr0
    1. Installation de l'OS Proxmox Backup Server
       - montage de l'ISO téléchargé
       - installation sur le disque de 16 Go
       - ajout du disque de 32Go pour le stockage
3. Creation de la VM Ubuntu
   1. Configuraion materielle
      - 1 vCPU
      - 1 Go de vRAM
      - 16 Go de vDisk System
      - 1 carte reseau sur vmbr2
      - 1 carte reseau sur vmbr1
    1. Installation de l'OS Ubuntu 22.04
      - montage de l'ISO téléchargé
      - installation sur le disque de 16 Go
4. Creation de la VM Zorin
   1. Configuraion materielle
      - 1 vCPU
      - 1 Go de vRAM
      - 32 Go de vDisk System
      - 1 carte reseau sur vmbr2
      - 1 carte reseau sur vmbr1
    1. Installation de l'OS Zorin 16.0
      - montage de l'ISO téléchargé
      - installation sur le disque de 16 Go

### Creatiion des backups
    1. Configuration du serveur de Backups
   > source d'information : chaine youtube tonton Jo, Vidéo Les Tutos - Proxmox No 7: PBS - Proxmox Backup Server
   > https://youtu.be/Vv_Co_P7c9E

   
  fin

   