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

### Etape 3 - Creation des VMs

1. Creation du serveur de Données sous l'OS Open Media Vault
    1. Configuaration materiel
       - 2 vCPU
       - 2 Go de vRAM
       - 8 Go de vDisk System
       - 130 Go de vDisk de Stockage
       - 1 carte reseau sur vmbr1
    2. Installation de l'OS Open Media Vault
       - montage de l'ISO téléchargé
       - installation sur le disque de 8 Go
       - ajout du disque de 130Go pour le stockage
2. Creation du serveur de Backup sous Proxmox Backup Serveur
   1. 

fin

   