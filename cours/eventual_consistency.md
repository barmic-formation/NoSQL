# Consistence

## Propriété ACID

Cohérence : toute écrire amène le système dans un état valide.

### Théorème CAP

![tableau3](img/tableau3.webp)

#### BASE

- _Basically Available_ : quelle que soit la charge de la base de données, le système garantie un taux de disponibilité de la donnée
- _Soft state_ : l'état de la base peut changer, il n'a pas à être cohérent continuellement
- _Eventual consistency_ : la cohérence à terme. La base deviendra au final, mais on ne peut pas s'appuyer sur quand est-ce qu'elle le sera

## Propriété BASE

- **Basic available** la cohérence est maintenue autant que possible, mais pas garantie
- **Soft-state** après un certain temps, il n'y a qu'une probabilité que le système soit cohérent
- **Eventualle consistent** à terme le système deviendra cohérent
