# Operation Bellatrix 2026 CTF
Voici le writeup du CTF Bellatrix 2026 "Operation Orion" organisé par COMCYBER en mars 2026.

## Table of Contents
### Phase 1 - Analyse
- [Un message d'alerte](#challenge-1)
- [Trop beau pour être vrai](#challenge-2)
- [(Dé)-Crédibiliser l'information](#challenge-3)
- [La vidéo du sauvetage](#challenge-4)
- [Au service d'une cause](#challenge-5)

## Challenge 1
### Un message d'alerte
On a ici un challenge qui requiert de trouver un blog diffusant des fausses informations sur l'armée française.
Notre seule ressource disponible est une capture d'écran d'un post supprimé mentionnant ce blog :
![Capture Rafale](img/rafale.png)

Sur cette capture, on peut voir la mention d'un blog du nom de global-news-maq, on va donc essayer de voir si on peut trouver ce blog. On va d'abord essayer de trouver le domaine du site, donc on essaie `global-news-maq.fr`, `global-news-maq.com`, jusqu'a arriver à `global-news-maq.info`, qui fonctionne ! Cela nous donne le site suivant :
![Global News Maq](img/globalnews.png)

Cela correspond bien à un site de désinformation qui diffuserait des fausses informations un peu partout sur les réseaux !

On entre donc l'url du blog en tant que flag et ça valide le challenge :
> BELLATRIX{global-news-maq.info}
 
## Challenge 2
### Trop beau pour etre vrai
#### OPTIONNEL
On nous dit ici que le logo du site trouvé dans le challenge précédent (*Un message d'alerte*), est pris d'un autre site de news connu. 
![Global News Maq Logo](img/logoglobalnews.png)

En faisant une recherche inversée sur ce logo, ou en recherchant `Global News`, qui est un terme plutot commun utilisé par les sites d'information, on tombe sur un site au logo ressemblant :
![Vrai Global News](img/vraiglobalnews.png)

On essaie donc d'entrer l'url de ce site en tant que flag et ça marche :
> BELLATRIX{globalnews.ca}

## Challenge 3
### (Dé)-Crédibiliser l'information
#### OPTIONNEL
Toujours en rapport avec le blog de désinformation, on doit cette fois-ci trouver les faux experts mentionnés dans les articles, et qui servent d'argument d'autorité pour convaincre les lecteurs de la véracité des propos.

## Challenge 4
### La vidéo du sauvetage 
On nous demande ici de retrouver une vidéo et d'identifier le site d'où elle provient. On commence d'abord par trouver l'article auquel une video est liée, et on la trouve sous l'article `MASSACRE DANS LE GOLFE DE GASCOGNE : LA FRANCE COMMET UN CRIME DE GUERRE CONTRE DES AQUILONNIENS SANS DÉFENSE !` :
![Video](img/video.png)

En analysant le code HTML de cette partie du blog, on y voit le lien vers le site d'où provient la vidéo :
![Video Provenance](img/provenancevideo.png)

On essaie donc le domaine du site en tant que flag et cela valide le challenge :
>BELLATRIX{passion-video.tech}

## Challenge 5
### Au service d'une cause
On nous demande cette fois de trouver la source de la vidéo trouvée précédemment et de suivre son utilisation sur d'autres blogs pour comprendre d'où elle vient et si une information réelle se cache derrière.

On se rend donc d'abord sur le site dont on avait trouvé l'url au challenge précédent (*passion-video.tech*) et on va naviguer dans les posts pour trouver quelque chose en lien avec la vidéo. Au bout d'un moment, on finit par trouver un post qui utilise la vidéo :
![Rafale Forum](img/rafaleforum.png)

Dans les commentaires on trouve quelqu'un qui explique qu'un autre site utilise la vidéo :
>La vidéo semble avoir été reprise sur le site https://le-mercurien-victorieux.info/

On se rend donc sur le site et on essaie de trouver un article en rapport avec la vidéo ou un des sujets de celle-ci (le rafale, le golfe de gascogne, etc) et bingo ! On trouve un article réutilisant la vidéo :
![Rafale Forum 2](img/rafaleforum2.png)

L'article semble encore intérpréter différemment les événements de la vidéo, cette fois-ci indiquant que des pêcheurs se sont fait attaquer par l'armée.
Encore dans les commentaires de l'article, on peut trouver un utilisateur qui dément 