# Systemd

Pour avoir le status défilant du service puredata

```
sudo journalctl -f -u psis-pd
```

Pour recharger la liste des services (si il y a des changements)

```
sudo systemctl daemon-reload
```

Pour démarer un services

```
sudo systemctl start psis-gpioEcouteur.service
```

Pour redémarrer un service

```
systemctl restart psis-pd
```

Créer des services SystemD pour les composantes

```
sudo nano /etc/systemd/system/psis-gpioDetecte.service

sudo nano /etc/systemd/system/psis-gpioEcouteur.service

sudo nano /etc/systemd/system/psis-pd.service
```

A verifier si copier les service dans le dossier fonctionne ::
```
sudo cp ~/src/posteDecoute/services/* /etc/systemd/system/
```



activer les services

```
sudo systemctl enable psis-pd.service

sudo systemctl enable psis-gpioEcouteur.service

sudo systemctl enable psis-gpioDetecte.service

```


reboot



# Startup Script systemD

source :
https://www.raspberrypi.org/forums/viewtopic.php?f=29&t=7192&p=828947#p828947



References
https://wiki.archlinux.org/index.php/Systemd


https://www.digitalocean.com/community/tutorials/how-to-use-systemctl-to-manage-systemd-services-and-units





sudo systemctl stop startPD.service


dans le folder service


sudo cp * /etc/systemd/system/


PSIS-stat




https://www.digitalocean.com/community/tutorials/how-to-use-systemctl-to-manage-systemd-services-and-units




#### Créer un fichier script


```
cd ~/
```

```
nano ping
```

y écrire puis sauvegarder

```
#!/bin/sh
ping -c 50 www.google.com
```

authoriser l'execution du fichier
```
chmod 755 ping
```
tester l'execution du script
```
./ping #see that it works
```

#### Créer un service
```
sudo nano /etc/systemd/system/ping.service
```

```
[Unit]
Description=Ping auto test

[Service]
ExecStart=/home/pi/ping


[Install]
WantedBy=multi-user.target

```

#### Créer un service
```
sudo nano /etc/systemd/system/gpioOSC.service
```

```
[Unit]
Description=gpioOSC service

[Service]
ExecStart=/home/pi/posteDecoute/scripts/gpioOSC.sh
Restart=always

[Install]
WantedBy=multi-user.target

```

screen -dmS gpioOSC /home/pi/posteDecoute/scripts/gpioOSC.sh


#### Pour voir l'etat du service

```
sudo systemctl start ping.service
```

```
sudo systemctl enable ping.service
```
```
sudo systemctl status ping.service
```

```
sudo systemctl daemon-reload
```



#### Si besoin d'interaction avec le clavier,  s'inspirer de ça

```
[Unit]
Description=top test

[Service]
ExecStart=/usr/bin/top
StandardInput=tty
StandardOutput=tty
TTYPath=/dev/tty9
TTYReset=yes
Restart=always

[Install]
WantedBy=multi-user.target

```
