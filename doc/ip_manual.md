https://raspiugv.raudasoja.com/documentation/raspi/network/staticfallback

```
sudo nano /etc/network/intefaces
```


```
auto eth0:1
iface eth0:1 inet static
address 10.0.0.101
netmask 255.255.255.0
```


```
sudo ifup eth0:1
```


