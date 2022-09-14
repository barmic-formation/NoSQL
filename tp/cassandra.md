# Cassandra

## Mise en place

Nous utiliserons un notebook.

Créez ensuite votre notebook et donnez lui le nom que vous souhaitez.

Ensuite créer votre key space avec la commande suivante en indiquand le nom que vous souhaitez :

```sql
CREATE KEYSPACE nom_keyspace
WITH replication = {'class':'SimpleStrategy', 'replication_factor' : 1};
```

# Exercice 1

Vous allez devoir créer votre table dans votre keyspace. Vous pouvez choisir votre keyspace en haut du bloc de text de votre notebook, sinon il faudra suffixer votre table par le nom de votre keyspace (exemple : `<keyspace>.<table>`).

Pour la suite du TP, nous allons imaginer comment stocker les vidéos d'une plateforme comme Youtube.

Pour créer votre table la syntaxe est :

```sql
CREATE TABLE nom_table (
  champ1 text,
  champ2 date,
  champ3 int,
  PRIMARY KEY ((poi_name))
);
```

Pour voir l'ensemble des types, vous pouvez voir sur cette page :
https://cassandra.apache.org/doc/latest/cassandra/cql/types.html

Créez quelques entrées qui permettraient de créer les interfaces de youtube avec entre autre :

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

Documentation sur les requêtes CQL :
https://cassandra.apache.org/doc/latest/cassandra/cql/dml.html
https://docs.datastax.com/en/cql-oss/3.3/cql/cql_reference/cqlSelect.html

Maintenant que vous avez quelques documents, tentez de les requêter en répondant à ces interrogations :

1. lister toutes les vidéos d'une chaine
2. lister les 5 dernières vidéos d'une chaine
3. trouver les vidéos les mieux notées
4. trouver les vidéos ayant un tag donné
5. trouver toutes les vidéos commentée par un utilisateur donné
