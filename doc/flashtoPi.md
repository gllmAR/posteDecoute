# Formater une carte microSD depuis une image disque version terminal

source :  
[raspberrypi.org](https://www.raspberrypi.org/documentation/installation/installing-images/mac.md)

télécharger raspbian frais chez raspberrypi.org


dans le terminal

trouver le bon périphérique (qui a la bonne capacité)
```
diskutil list
```

Éjecter le périphérique depuis la ligne de commande 

```
diskutil unmountDisk /dev/disk2
```

Copier le fichier image vers le périférique 

ctrl+t pour voir le progrès

```
sudo dd bs=1m if=/Users/gllm/Downloads/2016-03-18-raspbian-jessie-lite.img  of=/dev/rdisk2
```

Éjecter le périférique en toute sécurité
```
diskutil unmountDisk /dev/disk2
```


