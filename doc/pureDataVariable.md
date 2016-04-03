Config : path du lieu dasn lieu.path

#### ÉCOUTEUR

ecouteur.raw = nom du send 

+ ecouteur.actif.timer = temps en ms ou le senseur ecouteur est actif afin de  valider un 1 sur ecouteur

+ ecouteur.inactif.timer = temps en ms ou le senseur ecouteur est inactif afin de  valider un 0 sur ecouteur

ecouteur = état de l'écouteur filtré



#### 



#### AMBIANCE.VEILLE

+ ambiance.veille.timer.max = temps maximum pour déclencher fadeout

+ ambiance.veille.timer.min = temps minimum pour déclencher fadeout
 
ambiance.veille.timer.time = temps aléatoire entre max et min 

ambiance.veille.timer = activation ou désactivation du timer avant de déclancher fadeout



+ ambiance.count : nombre de fichier audio dans le dossier(devrait être à 1)
+ ambiance.filename : nom du fichier avant le underscore et l'index 
- ambiance.path : /nom de la path/

+ ambiance.normal.vol
+ ambiance.normal.fadetime

- ambiance.cut.vol
- ambiance.cut.fadetime

+ ambiance.fadeout.vol
+ ambiance.fadeout.fadetime


