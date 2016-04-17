# Configuration du raspberrypi "from scratch"

Télécharger l'IMG  de [RASPBIAN JESSIE LITE](https://www.raspberrypi.org/downloads/raspbian/)

Installer sur la carte en suivant ces [instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md)

Brancher le pi sur un réseau filaire muni de DHCP

Pénétrer le pi avec le mot de pass "raspberry"

```
ssh pi@raspberrypi.local
```

mettre à jour les paquets du raspberry
```
sudo apt-get update && sudo apt-get upgrade
```

configurer le pi avec l'utilitaire
```
sudo raspi-config
```

changer :
* hostname : psis0X
* Password : changer pour un password logique
* resize la partition : prendre le 8 giga total

reboot / ressh ?
```
ssh pi@psis01.local
```

Télécharger et installer les dépendances

```
sudo apt-get install netatalk git python-rpi.gpio python-setuptools &&
sudo easy_install pip &&
sudo pip install pyOSC
```

configurer le protocole de partage reseau [afp](afp.md)

configurer dac+[dac+](dac+.md)

configurer ip manuel [ip_manuel](im_manuel.md)

installer pd [pd](pd.md)

brancher en suivant le [pinout](pinOut.md)

Distribuer les pi selon l'[allocation](allocation.md)

```
sudo reboot
```

Configurer le volume de la carte piDac+ dans [alsa](alsa.md)

baisser le son à 35 sur alsamixer

installer et clonner le Github du projet


```

cd ~
mkdir src
cd src
git clone --recursive https://github.com/gllmAR/posteDecoute.git
```

Creer des services SystemD pour les composantes

```
sudo nano /etc/systemd/system/psis-gpioDetecte.service

sudo nano /etc/systemd/system/psis-gpioEcouteur.service

sudo nano /etc/systemd/system/psis-pd.service
```

Copier les services dans le dossier fonctionne
```
sudo cp ~/src/posteDecoute/services/* /etc/systemd/system/
```

recharger la liste des services
```
sudo systemctl daemon-reload
```

activer les services

```
sudo systemctl enable psis-pd.service
sudo systemctl enable psis-gpioEcouteur.service
sudo systemctl enable psis-gpioDetecte.service
sudo systemctl start psis-gpioEcouteur.service

```


reboot



