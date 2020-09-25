# TD

## Objets trouvés à la SNCF

Données (uniquement pour information) : [objets trouvés à la SNCF](https://ressources.data.sncf.com/explore/dataset/objets-trouves-restitution/information/?sort=date&dataChart=eyJxdWVyaWVzIjpbeyJjaGFydHMiOlt7InR5cGUiOiJiYXIiLCJmdW5jIjoiQ09VTlQiLCJjb2xvciI6InJhbmdlLWN1c3RvbSIsInNjaWVudGlmaWNEaXNwbGF5Ijp0cnVlfV0sInhBeGlzIjoiZGF0ZSIsIm1heHBvaW50cyI6IiIsInRpbWVzY2FsZSI6InllYXIiLCJzb3J0IjoiIiwic2VyaWVzQnJlYWtkb3duIjoiZ2Nfb2JvX3R5cGVfYyIsInNlcmllc0JyZWFrZG93blRpbWVzY2FsZSI6Im1vbnRoIiwic3RhY2tlZCI6Im5vcm1hbCIsImNvbmZpZyI6eyJkYXRhc2V0Ijoib2JqZXRzLXRyb3V2ZXMtcmVzdGl0dXRpb24iLCJvcHRpb25zIjp7InNvcnQiOiJkYXRlIn19fV0sInRpbWVzY2FsZSI6IiIsImRpc3BsYXlMZWdlbmQiOnRydWUsImFsaWduTW9udGgiOnRydWV9)

Quelques exemples de données :

| Date | Type d'objets | Nature d'objets | Gare | Code UIC | Date et heure de restitution |
|---|---|---|---|---|---|
| 16 septembre 2020 14:57 | Bagagerie: sacs, valises, cartables | Valise, sac sur roulettes | Cherbourg | 0087444877 | |
| 16 septembre 2020 14:51 | Vêtements, chaussures | Autres vêtements | Cherbourg | 0087444877 | |
| 16 septembre 2020 14:50 | Vêtements, chaussures | Chaussures (autre que chaussures de ski et patins) | Paris Montparnasse | 0087391003 | |
| 16 septembre 2020 14:47 | Optique | Lunettes | Paris Montparnasse | 0087391003 | |

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

## Disponibilité des places Vélomagg

Données (uniquement pour information) : [Disponibilité des places Vélomagg en temps réel](https://data.montpellier3m.fr/dataset/disponibilite-des-places-velomagg-en-temps-reel)

Quelques exemple de données :

| nom | identifiant | latitude | longitude | places occupées | places libres | total |
|---|---|---|---|---|---|---|
| 001 Rue Jules Ferry - Gare Saint-Roch | 001 | 43.605366 | 3.881346 | 10 | 2 | 12 |
| 002 Comédie | 002 | 43.608148 | 3.878778 | 9 | 15 | 24 |
| 003 Esplanade | 003 | 43.609478 | 3.881293 | 18 | 14 | 32 |
| 004 Hôtel de Ville | 004 | 43.599088 | 3.894866 | 6 | 10 | 16 |
| 005 Corum | 005 | 43.613989 | 3.881600 | 11 | 1 | 12 |
| 006 Place Albert 1er - St Charles | 006 | 43.616768 | 3.873375 | 16 | 15 | 31 |
| 007 Foch | 007 | 43.610989 | 3.873345 | 7 | 1 | 8 |

Considérez que toutes les minutes, vous recevez la liste complète à jour.

### Questions

 1. Trouvez une clef de partitionnement valide (en expliquant)
 2. À partir des quelques exemples utilisez votre clef de partitionnement pour les regrouper
 3. Pour la suite nous allons interroger la base tel que vous l'avez organisé. Pour chaque question indiquez si la requête s'effectue "directement" sur une partition ou si plusieurs partitions doivent être interrogées. Dans ce dernier cas indiquez distinctement ce qu'il y a à faire dans la partie map et dans la partie reduce :
	 1. Combien de places sont disponibles à l'Hotel de Ville ?
	 2. Je suis à la latitude x et longitude y où puis-je trouver une place ?
	 3. Quel est le graphique d'occupation de la station Place Albert 1er - St Charles ?
   
   
   
