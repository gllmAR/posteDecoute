install sur la carte

ssh pi@raspberrypi.local

sudo raspi-config

hostname
Password
resize

ssh pi@psis01.local


sudo apt-get update && sudo apt-get upgrade

sudo apt-get install netatalk git python-rpi.gpio python-setuptools &&
sudo easy_install pip &&
sudo pip install pyOSC

configurer afp
configurer dac+
configurer ip manuel

installer pd


sudo reboot

baisser le son à 35 sur alsamixer


git clone --recursive https://github.com/gllmAR/posteDecoute.git


sudo nano /etc/systemd/system/psis-gpioDetecte.service

sudo nano /etc/systemd/system/psis-gpioEcouteur.service

sudo nano /etc/systemd/system/psis-pd.service


sudo systemctl daemon-reload

sudo systemctl enable psis-pd.service

reboot
