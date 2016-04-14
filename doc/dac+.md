# DAC+

Cette opération sert à rendre fonctionnel et par defaut la carte audui IQAUDIO Device drivers

Editer le fichier de config du PI
```
sudo nano /boot/config.txt
```

Inserer la ligne suivante

```
dtoverlay=iqaudio-dacplus

```

Commenter la ligne suivante : comme suis :
```
# dtparam=audio=on
```
