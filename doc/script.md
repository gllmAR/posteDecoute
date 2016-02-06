# Startup Script systemD

source : https://www.raspberrypi.org/forums/viewtopic.php?f=29&t=7192&p=828947#p828947

documentation :
https://wiki.archlinux.org/index.php/Systemd


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


#### Pour voir l'etat du service
```
sudo systemctl status ping.service
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