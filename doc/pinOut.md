

####  Activer NetTalk (être vu sur le réseau),  filesharing AFP compatible sur le pi

##### compilé depuis les sources suivantes :

* infos [netatalk](http://www.raspberrypi.org/forums/viewtopic.php?f=36&t=26826)
* file sharing : [http://raspberry.znix.com/2013/03/connecting-to-raspberry-pi-with-mac-os-x.html](http://raspberry.znix.com/2013/03/connecting-to-raspberry-pi-with-mac-os-x.html)

##### installer les dépendances requises (netatalk et x11vnc)

sudo apt-get install netatalk

##### Activer et configurer le file sharing AFP (apple file protocol)

sudo nano /etc/avahi/services/afpd.service

##### coller le texte suivant

```
<?xml version="1.0" standalone='no'?> <!--*-nxml-*-->
<!DOCTYPE service-group SYSTEM "avahi-service.dtd">
<service-group>
   	<name replace-wildcards="yes">%h</name>
   	<service>
      <type>_afpovertcp._tcp</type>
      	<port>548</port>
   	</service>
</service-group>
```


##### redémarrer le serveur avahi
* `
sudo /etc/init.d/avahi-daemon restart
`
