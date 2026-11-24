# banjo-flux

Un relais quotidien du flux **Syceron** de l'Assemblée nationale (comptes rendus des
séances publiques, XVIIe législature), pour le serveur de [BanJO](https://banjo-parl.fr).

## Ce que ce dépôt fait

Chaque matin, vers 03:30 UTC, le workflow `relayer` :

1. télécharge `syseron.xml.zip` depuis
   <https://data.assemblee-nationale.fr/static/openData/repository/17/vp/syceronbrut/syseron.xml.zip> ;
2. vérifie que c'est un zip lisible, de moins de 512 Mio ;
3. demande si le flux de la législature suivante est publié ;
4. publie le zip, son empreinte (`SHA256SUMS.txt`) et `meta.json` dans la release
   [`syceron-17`](../../releases/tag/syceron-17), en remplaçant ceux de la veille ;
5. verse `meta.json` dans le dépôt : son historique est celui des relais.

Le zip n'est pas modifié. `meta.json` donne son empreinte, la date de réécriture annoncée
par l'Assemblée (`last_modified`), l'heure du relais et l'exécution qui l'a fait.

## Pourquoi

Le serveur de BanJO ne peut pas joindre data.assemblee-nationale.fr (constat du
24 novembre 2026). Il lit donc le flux ici.

## Source et licence

Les données sont celles de l'**Assemblée nationale**, publiées en données ouvertes sur
<https://data.assemblee-nationale.fr> sous la
[Licence Ouverte / Open Licence 2.0 (Etalab)](https://www.etalab.gouv.fr/licence-ouverte-open-licence/).
Source : Assemblée nationale, flux Syceron. Ce relais n'est ni produit ni approuvé par
l'Assemblée nationale. Seule la source fait foi : en cas d'écart, c'est elle qu'il faut lire.
