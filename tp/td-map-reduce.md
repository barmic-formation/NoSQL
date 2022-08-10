# Exercice 1

## Données: liste de proverbe

| id | langue | proverbe |
|---|---|---|
| 1 | FR | La douceur du miel ne console pas de la piqûre de l'abeille. |
| 2 | FR | Les paroles s'envolent, les écrits restent. |
| 3 | EN | In prosperity caution, in adversity patience. |

## Question

On cherche à compter le nombre de mots par langue des proverbe. Pour ça on va utiliser :

- une fonction map qui va donner pour chaque proverbe la langue et le nombre de mots
- une fonction reduce qui va faire la moyenne du nombre de mot pour chaque langue

Décrivez le résultat de chaque execution de la méthode map() et de la méthode reduce().

# Exercice 2

## Données : liste de chef d'État

| id | Pays | Nom | Prise de function | Fin | Naissance |
|---|---|---|---|---|---|
| 1 | France | René Coty | 1954 | 1959 | 1882 |
| 2 | Royaume-Unis | Winston Curchill | 1951 | 1955 | 1874 |
| 3 | État-Unis | Theodore Roosevelt | 1901 | 1909 | 1858 |
| 4 | France | Vincent Auriol | 1947 | 1954 | 1884 |

## Question 1

On cherche la durée moyenne des mandats.

- Indiquer ce que doit faire la fonction map()
- Indiquer ce que doit faire la fonction reduce()

Montrez les résultats des fonctions que vous avez décrit.

## Question 2

Même question, mais pour connaire l'age moyen de prise de fonction par décénie. Exemple de résultats :

| Décénie | age moyen |
|---|---|
| 1920 | 45 |
| 1930 | 46.1 |
| 1940 | 43.7 |
