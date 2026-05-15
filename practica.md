## Bloc 1 – Preguntes teòriques

### 1. Quina és la diferència entre docker run i docker compose up?

`docker run` serveix per arrancar un únic contenidor de forma manual, 
especificant totes les opcions per línia de comandes. 
`docker compose up` llegeix el fitxer `docker-compose.yml` i arranca 
tots els serveis definits de cop, amb tota la configuració ja guardada 
(xarxes, volums, variables d'entorn...). És més pràctic quan treballem 
amb múltiples contenidors que han de funcionar junts.

### 2. Per a què serveix depends_on? Garanteix que el servei dependent estigui completament operatiu?

`depends_on` indica l'ordre d'arrencada dels serveis. En el nostre cas, 
Mongo Express no arrancarà fins que el contenidor de MongoDB hagi arrancat.
Però **no garanteix** que MongoDB estigui completament operatiu i llest 
per acceptar connexions, només que el contenidor ha estat iniciat. 
Per això Mongo Express té `restart: unless-stopped`, per reiniciar-se 
automàticament si no pot connectar amb MongoDB.

### 3. Diferència entre xarxa bridge per defecte i xarxa personalitzada

- **Bridge per defecte:** Docker assigna automàticament una xarxa als 
contenidors, però aquests no es poden comunicar entre ells pel nom del 
contenidor, cal usar la IP.

- **Xarxa personalitzada (amb nom):** La creem nosaltres al 
`docker-compose.yml` (com `xarxa-botiga`). Els contenidors es poden 
comunicar entre ells usant el nom del contenidor com a hostname. 
Per exemple, Mongo Express pot connectar amb MongoDB usant 
`mongodb-botiga:27017` en lloc d'una IP.

Estructura que hay que seguir:
En finalitzar la pràctica el fitxer practica.md haurà de tenir:
•	Respostes a les preguntes teòriques de tots els blocs
•	Captures de pantalla que es demanen.

