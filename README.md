# poste D'écoute

Lecteur sonore sensible disséminé dans l'espace publique.
Spécilament conçu pour l'artiste Julie Faubert.  


ecouteur.actif = 0
detecte.actif = 0
synchrone.actif = 0

ecouteur : 
	actif si senseur écouteur = actif + smooth
	inactif si senseur écouteur = inactif + smooth
	

detecte : 
	actif si senseur détecte = actif + smooth
	inactif si senseur détecte = inactif.smooth
	
synchrone :
	actif si deux poste ont ecouteur actif activé
	inactif si pas deux poste ont écouteur actif activé


ambiance.veille.timer : 

if STATE == ambiance.actif && ecouteur.inactif 
	ambiance.veille.timer --
	if ambiance.veille.timer == 0 
		STATE => ambiance.veille
else 
	ambiance.veille.timer == ambiance.veille.timer.init		



**Variables**

ambiance.veille.timer.time ; temps en seconde pour la mise en veille sonore


**Fonctions**


Fonctionne avec les états suivants

##### state : AMBIANCE.VEILLE :
joue ambiance à volume bas
* si ecouteur = 0 & ambiance.veille.timer. = 0 -> ambiance.player.fadeout
* si ecouteur = 1 -> ambiance.actif  

##### state : AMBIANCE.ACTIF :
joue ambiance à volume normale

* si ecouteur = 1 & circonstance.new.timer = 0 & circonstance.flag = 0 -> CIRCONSTANCE.NEW
* si ecouteur = 1 & circonstance.old.timer = 0 & circonstance.flag = 1 -> CIRCONSTANCE.OLD
* si ecouteur = 1 & detecte = 1 & detection.player.ended & detection.timer.ended &  = 1 & detection.timer.ended = 1 -> DETECTION
* si ecouteur = 1 & sychrone = 1 & synchronie.player.ended = 1 & synchronie.timer.ended = 1 -> SYNCRHONIE


##### state : CIRCONSTANCE.NEW :
Joue un fichier aléatoire depuis le dossier circonstance lorsque ECOUTE  est activé pour la première fois après avoir attendu un  temps relativement aléatoire à la fin,  retour à ambiance

* si ecouteur = 0 & circonstance.new.veille.timer.ended = 1 => ambiance.actif & circonstance.new.player.fade
* si ecouteur = 1 & circonstance.new.player.ended => ambiance.actif & circonstance.flag=1
* si ecouteur = 1 & sychrone.actif & synchronie.player.ended & synchronie.timer = 0 -> SYNCHRONIE





##### state : CIRCONSTANCE.OLD :
- joue un fichier aléatoire depuis le dossier circonstance lorsque ECOUTE est activé suite à la première fois après avoir attendu un  temps relativement aléatoire, à la fin,  retour à ambiance


* si ecouteur = 0 & circonstance.new.veille.timer.ended = 1 => AMBIANCE.ACTIF & circonstance.flag=0
* si ecouteur = 1 & circonstance.old.ended => AMBIANCE.ACTIF
* si ecouteur = 1 & sychrone = 1 & synchronie.player.ended  & synchronie.timer = 0 -> SYNCHRONIE



##### function : SYNCHRONIE :
- joue un fichier pigé depuis le dossier Synchrome en addition avec AMBIANCE et CIRCONSTANCE lorsque 2 écouteurs sont actifs.
- Un délai aléatoire  entre les lectures de fichiers

* si ecouteur = 1 & synchrone = 1 & synchrone.timer = 0 => syncronie.play

* syncronie.rnd.timer



##### function : DÉTECTION
- joue un fichier pigé depuis le dossier Détecte en addition avec AMBIANCE lorsqu'un senseur est déclenché.
* detectione.rnd.timer


### commande utiles

* pour déployer sur le raspberry-pi (installer depuis git)
```
cd ~/src
git clone --recursive https://github.com/gllmAR/posteDecoute.git
```
* pour aller chercher la dernière version
```
cd ~/posteDecoute
git pull
```
* pour lancer la commande de senseur en local sur la broche 18 sans le mode de débug
```
python /home/pi/posteDecoute/rpi-gpioOsc/rpi-gpioOs.py -i 18 -o /ecoute.senseur.raw -d 127.0.0.1 -p 8000 -r 2 -D 0
```
* pour lancer pure data sans interface sur une carte audio externe avec une configuration de lieu
```
/home/pi/pd-0.46-7/bin/pd -nogui -listdev -audiooutdev "3,1" -nogui -send "lieu.read /home/pi/situations/lieux/lieux_1.txt" /home/pi/posteDecoute/pd/_main.pd
```

### Service au boot

Pour automatiser le départ des application,  nous utilisons le principe de Services dans systemD

voir

https://www.digitalocean.com/community/tutorials/how-to-use-journalctl-to-view-and-manipulate-systemd-logs




### Dépendences :

pd-Vanilla 0.46.7
* disponible ici :  http://msp.ucsd.edu/software.html




#### to do

##### prog Pd
* changer fadeout pour inactif
* changer cut pour muted


##### modifier readGpioOSC.py
* [X] implémenter le mode read (actif par default)
* [ ] implémenter un change.

##### Script d'initialisation

* trouver c'est quoi le plus logique avec systemD
	* https://blog.sleeplessbeastie.eu/2015/04/27/how-to-manage-system-services-on-debian-jessie/
* Documenter afin que ce soit simple pour un utilisateur à changer
* http://www.pihomeserver.fr/en/2013/05/27/raspberry-pi-home-server-lancer-un-programme-automatiquement-au-demarrage/
*

##### Connexion wireless on boot :

* [ ] hidden SSID
* [ ] Password sur le ssid
* investiguer et mieux documenter :

http://elinux.org/RPI-Wireless-Hotspot

http://www.novitiate.co.uk/?p=183

http://spin.atomicobject.com/2013/04/22/raspberry-pi-wireless-communication/

fonctionne,  mais n'as pas le bon dhcp serveur

http://www.ronnutter.com/raspberry-pi-installing-dhcp-server/

http://spin.atomicobject.com/2013/04/22/raspberry-pi-wireless-communication/

http://lcdev.dk/2012/11/18/raspberry-pi-tutorial-connect-to-wifi-or-create-an-encrypted-dhcp-enabled-ad-hoc-network-as-fallback/



#### notes supplémentaires

##### notes sur les cartes de sons
noter qu'il faut spécifiquement des carte n'ayant pas le même nom pour que PD soit capable de choisir la bonne carte au démarrage en command line.

Setup Fonctionnel de deux carte
```
aplay -l
```
card 0: ALSA [bcm2835 ALSA], device 1: bcm2835 ALSA [bcm2835 IEC958/HDMI] Subdevices: 1/1 Subdevice #0: subdevice #0
card 1: Set [C-Media USB Headphone Set], device 0: USB Audio [USB Audio] Subdevices: 1/1 Subdevice #0: subdevice #0
card 2: Device [USB Audio Device], device 0: USB Audio [USB Audio] Subdevices: 1/1 Subdevice #0: subdevice #0

Lancer deux instances de pd avec deux cartes audio différtentes
```
pd-0.46-7/bin/pd -nogui -listdev -audiooutdev "3,1" ~/prog/test1.pd
pd-0.46-7/bin/pd -nogui -listdev -audiooutdev "5,1" ~/prog/test2.pd
```

##### carte de son I2S
à investiguer
https://www.adafruit.com/products/3016


##### gestion des sous-modules

lire documentation utile ici :
https://chrisjean.com/git-submodules-adding-using-removing-and-updating/
