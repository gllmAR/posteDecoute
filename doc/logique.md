# Logique de fonctionnement

### AMBIANCE 
* lecture en Boucle
* lorsque INACTIF, réduit son volume  pendant longue période,  
* FadeOut Complet lorsque CIRCONSTANCE joue,

### CIRCONSTANCE
* lecture en alternance avec AMBIANCE,  
* choix aléatoire dans une banque de sons 
### SYNCHRONE 
* lecture en addition avec AMBIANCE, CIRCONSTANCE ou PONCTUELS  
* lecture quand la condition de synchro de deux postes dont actif 
* Choix aléatoire dans une banque de sons,
	
### DÉTECTE 
* Lecture en addition avec AMBIANCE 
* Lecture lorsque le capteur détecte un passage 
3 modes de fonctionnement, ce traduit par ce nombre de pistes actives
	
* SIMPLE :
	* AMBIANCE,  CIRCONSTANCE  
* SYNCHRONE : 
	* AMBIANCE, CIRCONSTANCE et SYNCHRONE
* DETECTE : 
	* AMBIANCE, CIRCONSTANCE et DÉTECTE	
