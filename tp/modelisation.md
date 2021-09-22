# TD

## Objets trouvés à la SNCF

Données (uniquement pour information) : [objets trouvés à la SNCF](https://ressources.data.sncf.com/explore/dataset/objets-trouves-restitution/information/?sort=date&dataChart=eyJxdWVyaWVzIjpbeyJjaGFydHMiOlt7InR5cGUiOiJiYXIiLCJmdW5jIjoiQ09VTlQiLCJjb2xvciI6InJhbmdlLWN1c3RvbSIsInNjaWVudGlmaWNEaXNwbGF5Ijp0cnVlfV0sInhBeGlzIjoiZGF0ZSIsIm1heHBvaW50cyI6IiIsInRpbWVzY2FsZSI6InllYXIiLCJzb3J0IjoiIiwic2VyaWVzQnJlYWtkb3duIjoiZ2Nfb2JvX3R5cGVfYyIsInNlcmllc0JyZWFrZG93blRpbWVzY2FsZSI6Im1vbnRoIiwic3RhY2tlZCI6Im5vcm1hbCIsImNvbmZpZyI6eyJkYXRhc2V0Ijoib2JqZXRzLXRyb3V2ZXMtcmVzdGl0dXRpb24iLCJvcHRpb25zIjp7InNvcnQiOiJkYXRlIn19fV0sInRpbWVzY2FsZSI6IiIsImRpc3BsYXlMZWdlbmQiOnRydWUsImFsaWduTW9udGgiOnRydWV9)

Quelques exemples de données :

| Date | Type d'objets | Nature d'objets | Gare | Code UIC | Date et heure de restitution |
|---|---|---|---|---|---|
| 16 sept 2020 14:57 | Bagagerie: sacs, valises, cartables | Valise, sac sur roulettes | Cherbourg | 0087444877 | |
| 16 sept 2020 14:51 | Vêtements, chaussures | Autres vêtements | Cherbourg | 0087444877 | |
| 16 sept 2020 14:50 | Vêtements, chaussures | Chaussures (autre que chaussures de ski et patins) | Paris Montparnasse | 0087391003 | |
| 16 sept 2020 14:47 | Optique | Lunettes | Paris Montparnasse | 0087391003 | |

Considérez que l'on vous donne en temps réel les nouveaux objets trouvés.

### Questions

 1. Trouvez une clef de partitionnement valide (en expliquant)
 2. À partir des quelques exemples utilisez votre clef de partitionnement pour les regrouper
 3. Pour la suite nous allons interroger la base tel que vous l'avez organisé. Pour chaque question indiquez si la requête s'effectue "directement" sur une partition ou si plusieurs partitions doivent être interrogées. Dans ce dernier cas indiquez distinctement ce qu'il y a à faire dans la partie map et dans la partie reduce :
	 1. Quels sont les objets trouvés aujourd'hui ?
	 2. Quel jour de la semaine trouvons-nous le plus d'objets ?
	 3. Quel jour de la semaine trouvons-nous le plus d'objets du type vêtement ?
	 4. Quels sont les objets trouvés à Paris Gare de Lyon ?
	 5. Combien d'objets trouvés le 2 janvier 2020 ont été restitués ?

### Réponses possibles

1. Nous décidons de prendre les gares comme clef de partitionnement en utilisant un hash. C'est une donnée stable et le hash sur le nom de la gare va permettre de répartir les gares entre les plus chargées et les moins chargées sur notre cluster.
2. Pour les exemples présentés : les 2 premières lignes seront dans une partition et les 2 suivantes seront dans une autre.
3. Requêtes :
  1. Cette requête va nous demander de parcourir toutes les partitions, on va avoir besoin de map/reduce:
    - map: doit retourner toutes les lignes représentant un objet trouvé aujourd'hui
    - reduce: doit juste concaténer tous les résultats fourni par map
  2. Cette requête va nous demander de parcourir toutes les partitions, on va avoir besoin de map/reduce:
    - map: doit retourner un dictionnaire contentant en clef chaque jour de la semaine et en valeur le nombre d'objet trouvés ce jour là (`{'lundi':12,'mardi':8,…}`)
    - reduce: va faire la somme jour à jour des résultats des map puis chercher le jour avec le plus grand nombre
  3. Cette requête va nous demander de parcourir toutes les partitions, on va avoir besoin de map/reduce:
    - map: doit retourner un dictionnaire contentant en clef chaque jour de la semaine et en valeur le nombre d'objet trouvés du type vêtement ce jour là
    - reduce: va faire la somme jour à jour des résultats des map puis chercher le jour avec le plus grand nombre
  4. Avec notre clef de partitionnement cette information peut être directement trouvée (type 2)
  4. Cette requête va nécessiter un map/reduce:
    - map: compter les objets trouvés le 2 janvier 2020 qui ont une date de restitution
	- reduce: faire la somme des résultats des map
	

## Disponibilité des places Vélomagg

Données (uniquement pour information) : [Disponibilité des places Vélomagg en temps réel](https://data.montpellier3m.fr/dataset/disponibilite-des-places-velomagg-en-temps-reel)

Quelques exemple de données :

| nom | identifiant | latitude | longitude | places occupées | places libres | places total |
|---|---|---|---|---|---|---|
| Rue Jules Ferry - Gare Saint-Roch | 001 | 43.605366 | 3.881346 | 10 | 2 | 12 |
| Comédie | 002 | 43.608148 | 3.878778 | 9 | 15 | 24 |
| Esplanade | 003 | 43.609478 | 3.881293 | 18 | 14 | 32 |
| Hôtel de Ville | 004 | 43.599088 | 3.894866 | 6 | 10 | 16 |
| Corum | 005 | 43.613989 | 3.881600 | 11 | 1 | 12 |
| Place Albert 1er - St Charles | 006 | 43.616768 | 3.873375 | 16 | 15 | 31 |
| Foch | 007 | 43.610989 | 3.873345 | 7 | 1 | 8 |

Considérez que toutes les minutes, vous recevez la liste complète à jour.

### Questions

 1. Trouvez une clef de partitionnement valide (en expliquant)
 2. À partir des quelques exemples utilisez votre clef de partitionnement pour les regrouper
 3. Pour la suite nous allons interroger la base tel que vous l'avez organisé. Pour chaque question indiquez si la requête s'effectue "directement" sur une partition ou si plusieurs partitions doivent être interrogées. Dans ce dernier cas indiquez distinctement ce qu'il y a à faire dans la partie map et dans la partie reduce :
	 1. Combien de places sont disponibles à l'Hotel de Ville ?
	 2. Je suis à la latitude x et longitude y où puis-je trouver une place ?
	 3. Quel est le graphique d'occupation de la station Place Albert 1er - St Charles ?

### Réponses possibles

1. Je décide d'utiliser le nom comme clef de partitionnement avec un hash. C'est une information stable et toute mes partitions auront la même taille (toutes les stations ont 24h*60 minutes lignes par jours).
2. Toutes les lignes présentées seront dans des partitions différentes
3. Requêtes :
  1. C'est une requête direct avec le nom de la station et la date je peux aller directement chercher la ligne qui m'intéresse
  2. Je dois chercher pour toutes les stations donc je passe par un map/reduce
    - map: calcule la distance entre ma position et la position de la station et renvoie un tuple de 3 valeurs : l'identifiant de la station, la distance avec moi et le nombre de places disponibles
	- reduce: prend la station avec la distance minimum qui a un nombre de place supérieur à 0
  3. C'est une requête de type 2. Je peux aller dans une partition et chercher toutes les données pour tracer une courbe où pour chaque minute (en abscisse) j'aurais calculé en ordonnée le pourcentage de places occupées (`{places occupées}*100/{places total}`)

Note:

Pour bien comprendre les partitions auront une forme comme celle-ci:

| date | nom | identifiant | latitude | longitude | places occupées | places libres | places total |
|---|---|---|---|---|---|---|---|
| 16 sept 2020 14:57 | Rue Jules Ferry - Gare Saint-Roch | 001 | 43.605366 | 3.881346 | 10 | 2 | 12 |
| 16 sept 2020 14:56 | Rue Jules Ferry - Gare Saint-Roch | 001 | 43.605366 | 3.881346 | 10 | 2 | 12 |
| 16 sept 2020 14:55 | Rue Jules Ferry - Gare Saint-Roch | 001 | 43.605366 | 3.881346 | 9 | 3 | 12 |
| 16 sept 2020 14:54 | Rue Jules Ferry - Gare Saint-Roch | 001 | 43.605366 | 3.881346 | 7 | 5 | 12 |
| 16 sept 2020 14:53 | Rue Jules Ferry - Gare Saint-Roch | 001 | 43.605366 | 3.881346 | 7 | 5 | 12 |
| 16 sept 2020 14:52 | Rue Jules Ferry - Gare Saint-Roch | 001 | 43.605366 | 3.881346 | 1 | 9 | 12 |

- J'ai uniquement ajouté la date pour conserver un historique des données.
- Au sujet de l'évidente duplication des informations il y a différentes manière de gérer ça, ça dépend beaucoup de la base de données utilisé. Les bases de données orientées colonnes n'ont particulièrement pas de problème avec des colonnes comme cela. Elles dédupliquent "naturellement" ces données.
