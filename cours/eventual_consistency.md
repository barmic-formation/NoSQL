# Consistence

## Propriété ACID

- *Atomicité* : une écriture se fait totalement ou pas du tout
- *Cohérence* : toute écriture amène le système dans un état valide.
- *Isolation* : les transactions s'executent comme si elles étaient seules sur la base
- *Durabilité* : si une écriture est acquitée, elle est durable (elle restera même en cas de redémarrage ou de panne)

### Théorème CAP

![tableau3](img/tableau3.webp)

## Propriété BASE

- **Basic available** la cohérence est maintenue autant que possible, mais pas garantie
- **Soft-state** après un certain temps, il n'y a qu'une probabilité que le système soit cohérent
- **Eventualle consistent** à terme le système deviendra cohérent

## Stratégies de cohérence

Pour rappel le fonctionnement général losrque l'on requête une base de données.

1. on envoie une requête sur un répartiteur
2. le répartiteur va envoyer la requête sur tous les nœuds concernés, c'est à dire sur tous les nœuds qui répliquent la partition concernant les données de la requête (si on a une réplication configurée à 5, la requête sera envoyée à 5 nœuds de la base)
3. le répartiteur va ensuite acquiter la requête

Pour contrôler la cohérence, on utilise des stratégies qui permettent de choisir quand est-ce que la base de données va acquiter nos requêtes.

Les stratégies les plus classiques sont :

- **ONE** la base de données va acquitter notre requête dès qu'un des réplicas lui aura répondu 
- **QUORUM** la base de données va acquitter notre requête lorsque la moitiée des réplicas + 1 lui auront répondu
- **ALL** la base de données va acquitter la requête lorsque tous les réplicas lui auront répondu

### Attention

Ces stratégies impactent la cohérence car elles vont impacter la manière dont la base va répliquer ses données. Prenons un exemple :

1. ma base de données a une réplication à 3
2. j'envoie une requête requête avec une cohérence à `ONE`
3. le répartiteur va la renvoyer à 3 nœuds
4. au premier nœud qui aura effectivement traité la requête et répondu au répartiteur le répartiteur va répondre à la requête
5. les 2 autres nœuds n'ont pas pu traiter la requête

Dans ce cas là la base de données aurant 3 nœuds qui seront incohérents (2 répliques d'une même données gardent une valeur ancienne et un nœud aura la dernière). Lorsque la base va corriger cette incohérence (ça dépend des bases, ça peut être une tâche en font exécutée régulièrement), la base de données va décider d'écrire la données ancienne sur le nœud qui était le plus à jour.

Note : il est impossible de faire confiance à un timestamp car il n'est pas possible de synchroniser les horloges des différentes nœuds de la base avec suffisament de précision.

## Choisir la cohérence

On peut choisir d'utiliser une stratégie différentes entre les requêtes de lecture et celles d'écriture pour obtenir la cohérence souhaitée tout en ayant une 

| WRITE | READ | cohérence |
|---|---|---|
| ONE | QUORUM | on a beaucoup d'écritures, mais on accepte d'en perdre (par exemple pour des stats - comme les compteurs de _like_ -) |
| QUORUM | ONE | on veut être sûr des données écrites et on souhaite que les lecture consomment peu de resource |

Les stratégies demandant `ALL` ne sont utilisées que pour certains usages internes des bases.