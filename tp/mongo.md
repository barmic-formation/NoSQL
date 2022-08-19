# MongoDB

## Mise en place

Nous utiliserons le client Studio 3T disponible à l'adresse : https://robomongo.org/

Une fois lancé créé une nouvelle connexion avec l'URL :

```
mongo_url
```

# Exercice 1

Dans la sidebar à gauche vous trouverais la liste des bases de données auquel vous avez accès.

Dans la base de données `exercice_1`, créer votre collection. Donnez lui le nom que vous souhaitez.
Pour ça déplier la base de données, faites un clique droit sur Collections, puis `Add collections…`.
Ne vous souciez pas des autres paramètres, ils ne sont pas utile pour le TP.

Pour la suite du TP, nous allons imaginer comment stocker les vidéos d'une plateforme comme Youtube.

Mongo n'a pas de schema, en guise de schema vous allez créer quelques documents qui servirons d'exemples.

Créez quelques documents qui permettraient de créer les interfaces de youtube avec entre autre :

> - nom de la vidéo
> - durée
> - nombre de vues
> - chaine
> - date
> - description
> - [commentaires]
> - [tags]
> - …

https://www.mongodb.com/docs/v5.2/core/shell-types/

## Requêtes

Maintenant que vous avez quelques documents, tentez de les requêter en répondant à ces interrogations :

1. lister toutes les vidéos d'une chaine
2. lister les 5 dernières vidéos d'une chaine
3. trouver les vidéos les mieux notées
4. trouver les vidéos ayant un tag donné
5. trouver toutes les vidéos commentée par un utilisateur donné
