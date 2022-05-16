## Migration d'une infrastructure physique en infrastructure virtualisée

### Etape 1 - installation de l'hyperviseur
Installation en barre metal de proxmox sur un PC portable
utilisation du Disque Dur en entier
IP en DHCP de la seule carte reseau reconnue

### Etape 2 - Configuration du reseau de l'hyperviseur

> vmbr0 est créé automatiquement à l'installation et lié à la carte réseau physique pour l'interface d administration

création de deux vSwitch supplémentaires : 

- vmbr1 pour le serveur de données et les deux machines Ubuntu et Zorin
- vmbr2 pour le serveur de backup et les deux machines Ubuntu et Zorin




