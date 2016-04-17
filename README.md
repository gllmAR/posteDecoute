# poste D'écoute

Lecteur sonore sensible pour situations dans l'espace publique.
Concu pour fonctionner avec des raspberry pi,  avoir une programmation unique et un fichier de configuration propre à chaque situation.

Conçu pour l'artiste Julie Faubert.  

fonctionne grace à : 

 
* Raspbian Jessy lite
* Pure Data vanilla
* Systemed
* Python
* pi-dac+ (carte audio i2s)

Fonctionne en respectant la [logique](/doc/logique.md) suivante : 



### [Documentation](/doc)




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

### Service au boot

Pour automatiser le départ des application,  nous utilisons le principe de Services dans systemD

informations ici : 

[systemd](/doc/systemD.md)




### Dépendences :

pd-Vanilla 0.46.7
* disponible ici :  [http://msp.ucsd.edu/software.html](http://msp.ucsd.edu/software.html)

pd-osc
rpi-gpioOsc


