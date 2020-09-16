# NoSQL

## Problématique

Propriétés ACID :
 - Atomicité
 - Cohérence
 - Isolation
 - Durabilité

Théorème CAP:

 - Cohérence
 - Avaibility
 - Partitionnability

## Partitionnement

Propriété d'un bon partitionnement :
- stabilité
- répartition homogène

Utilisation du partitionnement :
- en lecture → requêter une seule partition
- en écriture → répartir sur l'ensemble des partitions

## Map/reduce

Traitement _full scan_
- des exemples sur quoi faire en sur le map et sur le reduce
