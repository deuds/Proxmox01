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

2. Creation de la zone de stockage des backups
        - Sur Le serveur PBS, création dans Administration/storage d'un nouveau dossier qu'on appelle BKP
        - il s'ajoute automatiquement au Datastore si on laisse la case cochée
    ##### => cela crée l'espace de stockage pour les sauvegardes
3. Création des taches de Backup sur PVE
        - Sur le serveur Proxmox, dans Datacenter/storage on ajoute un nouveau stockage avec comme type "Proxmox Backup server"
        - dans Datacenter/Backup on crée la tache de sauvegarde
        - Choisir le nouveau stockage précédemment créé.
        - Choisir la fréquence de sauvegarde
        - Selectionner les VMs à sauvegarder 

> reste a surveiller le bon déroulement des sauvegardes.

Un double clic sur les taches du serveur permet de connaitre le detail du déroulement de celles ci.

That's all Folks

<p align="center">
<img src="/Images/thats-all-folks.webp">
</p>




  fin

   