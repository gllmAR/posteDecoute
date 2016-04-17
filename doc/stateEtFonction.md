#States

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



# Fonctions


##### function : SYNCHRONIE :
- joue un fichier pigé depuis le dossier Synchrome en addition avec AMBIANCE et CIRCONSTANCE lorsque 2 écouteurs sont actifs.
- Un délai aléatoire  entre les lectures de fichiers

* si ecouteur = 1 & synchrone = 1 & synchrone.timer = 0 => syncronie.play

* syncronie.rnd.timer



##### function : DÉTECTION
- joue un fichier pigé depuis le dossier Détecte en addition avec AMBIANCE lorsqu'un senseur est déclenché.
* detection.rnd.timer
