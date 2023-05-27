Hello ! Voici le feedback que tu m'as demandé.
Déjà félicitation pour ton travail, le site fonctionne comme attendu et tu as su réaliser ce qui était demandé lors du parcours ainsi que les bonus.

## Bonus Recherche par direction
---
Au niveau d'un des bonus, lors de la recherche de cartes par direction, si nous choisissons la direction 'north' avec la valeur 1 par exemple, cela ne nous affiche que les cartes qui sont égales à 1.
Dans l'énoncé, il est écrit que l'on veut toutes les cartes ayant au moins la valeur recherchée.
Dans notre exemple de recherche donc, il faudrait que cela affiche les cartes ayant une valeur "north" supérieure ou égale à 1.

Dans les requêtes SQL, tu peux aussi y utiliser les opérateurs de comparaisons supérieurs ou égales. Cela te permet lors de la requête de filtrer directement tes résultats.

Par contre, tu as pensé à remplacer les apostrophes simples et ça, c'est cool !

## Nommage de fonctions
---
Fait attention lorsque tu nommes des méthodes à ne pas avoir déjà utilisé le même nom.
Dans ton searchController.js, tu as une méthode async qui se nomme searchByElement qui fait une requête avec la fonction searchByElement de ton dataMapper.
Ici ta requête passe, car c'est une méthode de ton objet dataMapper, et tu l'appelles bien, mais un oubli et c'est l'erreur assurée qui te prendra un certain temps avant de la trouvée.

Et c'est pareil pour toutes tes méthodes de searchController.js

## Index.js & req.secret
---
Pour gérer ton enregistrement de cookies de sessions, tu utilises req.secret, mais attention, c'est maintenant obsolète. La méthode req.secret était utilisée dans les versions antérieures d'Express.js.

Dans les versions plus récentes d'Express.js, il faut utiliser l'option secret lors de la configuration de la session.

## router.js
---
Ton router est bien organisé, clair et compréhensible ! Si tu souhaites pousser un peu +, tu pourrais commenter chaque ligne pour savoir à quoi correspond telle ou telle route. Mais au top



