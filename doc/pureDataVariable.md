Config : path du lieu dasn lieu.path

#### ÉCOUTEUR

ecouteur.raw = nom du send

+ ecouteur.actif.timer = temps en ms ou le senseur ecouteur est actif afin de  valider un 1 sur ecouteur

+ ecouteur.inactif.timer = temps en ms ou le senseur ecouteur est inactif afin de  valider un 0 sur ecouteur

ecouteur = état de l'écouteur filtré



#### AMBIANCE.VEILLE

+ ambiance.veille.timer.max = temps maximum pour déclencher fadeout

+ ambiance.veille.timer.min = temps minimum pour déclencher fadeout

ambiance.veille.timer.time = temps aléatoire entre max et min

ambiance.veille.timer = activation ou désactivation du timer avant de déclencher fadeout



+ ambiance.count : nombre de fichier audio dans le dossier(devrait être à 1)
+ ambiance.filename : nom du fichier avant le underscore et l'index
- ambiance.path : /nom de la path/

+ ambiance.normal.vol
+ ambiance.normal.fadetime

- ambiance.cut.vol
- ambiance.cut.fadetime

+ ambiance.fadeout.vol
+ ambiance.fadeout.fadetime


Fichier de configuration expliqué

* soundOutput.vol 1 ; (volume général)
* ecouteur.actif.timer 100; (combien de temps pour qu'on considère actif)
* ecouteur.inactif.timer 1000; (combien de temps ça prend pour qu'on considère inactif)
* detecte.actif.timer 100; (combien de temps pour qu'on considère actif)
* detecte.inactif.timer 1000; (combien de temps ça prend pour qu'on considère inactif)
* synchrone.out 10.0.0.103 8000; (à qui il parle; 10.0.0.50, si pas de situations synchrone)
* ambiance.veille.timer.min 5;
* ambiance.veille.timer.max 10;
* ambiance.filename lieux2_am;
* ambiance.normal.vol 1; (peu être plus haut que vol général)
* ambiance.normal.fadetime 50;
* ambiance.fadeout.vol 0.01;
* ambiance.fadeout.fadetime 10000;
* ambiance.cut.vol 0;
* ambiance.cut.fadetime 500;
* circonstance.new.timer.min 25;
* circonstance.new.timer.max 27;
* circonstance.old.timer.min 30;
* circonstance.old.timer.max 55;
* circonstance.count 16; (nombre de fichiers circonstance)
* circonstance.filename lieux2_ci;
* circonstance.normal.vol 1;
* circonstance.normal.fadetime 50;
* circonstance.fadeout.vol 0.01;
* circonstance.fadeout.fadetime 10000;
* detection.timer.min 10; (pour éviter que des détections s'empilent les unes sur les autres)
* detection.timer.max 15;
* detection.count 7; (nombre de fichiers détecte)
* detection.filename lieux2_de;
* detection.normal.vol 1;
* detection.normal.fadetime 50;
* synchronie.timer.min 30;
* synchronie.timer.max 50;
* synchronie.count 10; (nombre de fichiers synchronie)
* synchronie.filename lieux2_sy;
* synchronie.normal.vol 1;
* synchronie.normal.fadetime 50;
