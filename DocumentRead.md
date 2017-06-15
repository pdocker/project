# Projecte DOCKER/LDAP/TLS (Pablo Prieto)

## Introducció

El meu projecte consisteix en generar un total de 4 dockers on cadascun  
d'ells realitza una funció, tots ells utilitzan ldap y certificats TLS  
per a funcionar.  
El contingut resumit de cada docker serà el següent:  
1. Docker amb base ldap: Base de dades funcional amb subarbres, objectes,  
clases i certificats amb CA generats a partir de 0.  
El seu contingut s'aprofitarà per investigar en l'emmagatzament d'imatges,  
documents i certificats en base binaria.  
2. Docker com a servidor ldap: Mateixa base que el primer docker amb la  
principal diferencia que aquests actuarà com a servidor per utilització  
externa amb clients, s'aprofitarà per utilitzar PAM o Kerberos.  
3. Docker gràfic?¿ de logs ldap: Docker que treballarà amb les característiques  
de Monitor i queda per investigar alguna aplicació o mètode gràfic que permeti  
veure els logs i estadístiques generades per les consultes ldap o de la pròpia BD  
4. Docker backup ldap: La seva funció es crear backups de la base de ldap i  
generar registres de logs cap al docker encarregat dels logs.  
5. Docker d'experimentació amb bases ldap (Opcional): Docker amb diverses BD  
de LDAP distribuïdes per els diferents tipus de contingut i relaciones entre  
elles per agilitzar les consultes i altres aspectes a investigar.  

## Preparació i documentació utilitzada

Primerament, he generat dos dockers mitjançant la documentació oficial  
de dockerfile a partir de dos scripts que cadascun d'ells realitza  
l'instal·lació dels paquets necesaris pel funcionament dels dos servers  
de LDAP.  
Cada server realitza la seva funció:  
## Server 1:  
Funciona a partir d'una base de dades LDAP amb certificats que tenen una entitat  
certificadora que els avala i están configurats amb protecció TLS per tant, es poden  
realitzar connexions segures alhora de fer consultes. També, s'ha buscat fer l'implementació  
de la tecnologia overlay per a poder treballar amb la traducció de referrals des d'un arbre a un  
altre. Aquesta tecnologia que es basa en el Distributed Directory Service y permet fer consultes  
client desde un servidor a l'altre. També s'ha procurat configurar el servei slapd per a que accepti  
tant connexions amb seguretat ldaps:// com connexions sense seguretat ldap://.
## Server 2:

