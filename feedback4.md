

Hello ! Voici le feedback que tu m'as demandé.

## Routes paramétrées
---

Lorsque l'on passe des variables entre différentes pages avec le router, il est important de les nommer correctement.
Imaginons 2 pages d'un site. La page d'accueil avec une liste d'ingrédients, et la page de détails d'un ingrédient.
Nous avons 2 ingrédients : Farine avec l'id 1, et oeufs avec l'id 2
Pour chaque ingrédients, il a son id et son nom.
L'url de la page d'accueil est comme ceci : https://monsite.fr
Et l'url de la page ingrédient selon l'id : https://monsite.fr/1


Donc si je vais sur l'url https://monsite.fr/1, cela devrait m'afficher sur la page le nom farine.


Je vais te poser 2 questions:
La première :
- Quel est l'élément qui permet d'afficher le bon nom sur la page?


Et la deuxieme :
- Comment récupère-t-on cet élément ?


Rassure-toi, je ne vais pas te laisser sans réponse :D


Pour répondre à la première question, il s'agit de l'id.
Avec l'id tu peux récupérer toutes les infos de ta carte qui correspond à cet id.


Pour répondre à la deuxième question, il faut mettre l'objet qui correspond à cet id dans une constante.

Mais ensuite, une fois que tu as cette constante, tu l'envoies dans l'autre page pour pouvoir la récupérer.
Et c'est là qu'il faut faire attention.
Notre page de détails d'ingrédient par défaut, n'a pas de variables.
Si je lui envoie la constante detailsIngredient
```js
   try {
     const detailsIngredient = await dataMapper.getIngredient(ingredientId);
      if (detailsIngredient) {
       response.render('unSeulIngredient', {detailsIngredient});
```
C'est cette constante-là qu'il faudra que je récupère pour afficher les détails de mon ingrédient. Si je cherche à récupérer un autre nom, cela me produira une erreur.


Donc bien faire attention aux noms de tes variables, un seul s par exemple en moins ou en trop, et c'est l'erreur assurée !


Pense à faire des console.log() pour vérifier si tu récupères bien ta constante dans la page que tu souhaites, ou pour vérifier que ta constante a le type ou la donnée attendue.
console.log(detailsIngredient) -> affiche un seul ingrédient
console.log(typeof detailsIngredient) -> affiche le type de ma constante detailsIngredient


## Requêtes SQL et paramètres de fonctions
---
Quand on met un paramètre à une fonction, il ne faut pas oublier de l'utiliser. Si tu demandes un paramètre id il faut que ensuite, tu utilise le paramètre id.
Si on prend l'exemple d'une fonction d'addition
```js
function addition(a, b) {
    const result = a + b
    return result
}
```
Les paramètres dans la fonction sont a et b.
Ensuite, j'utilise ces paramètres là pour faire mon addition. J'additionne les nombre a et b.
Bon là, c'est abstrait, mais si lorsque j'appelle ma fonction je lui passe des nombres 
```js
const resultatAddition = addition(1, 1)
console.log(resultatAddition)
// 2
```
Voila à quoi servent les paramètres. Si je n'utilise pas les paramètres dans ma fonction
```js
function addition(a, b) {
    const result = 2 + 2
    return result
}
```
```js
const resultatAddition = addition(1, 1)
console.log(resultatAddition)
// 4

const resultatAddition = addition(500, 1000)
console.log(resultatAddition)
// 4
```

Maintenant ma fonction renverra toujours le même résultat : 4. J'aurais beau changer mes chiffres lors de l'appel de ma fonction, cela ne changeras rien.

Et bien dans ta requête SQL dans getCard c'est pareil, tu demandes un paramètre 'id', mais ce paramètre id l'utilises-tu quelque part dans ta fonction ?

Pense aussi à bien revoir les syntaxes des requêtes SQL. Ici nous ne faisons pas de jonction de table il faut donc écrire une requête un peu plus simple
[Lien](https://sql.sh/cours/select "Sql.sh").


### La recherche

Pense à l'architecture MVC.
Modèle Vue Controller
Modèle correspond aux requêtes de ta base de donnée
Vue correspond à ton affichage
Controller correspond aux actions faites entre ton modèle et ta vue

Pour effectuer une recherche sur le site donc il faudrait procéder comme ceci :
- On créer la requête SQL qui permet de rechercher l'élément dans la base de donnée
- Ensuite on créait le controller qui va nous permettre de récupérer les données reçues de la requête SQL et de les envoyer à la vue
- Enfin, on créer la vue afin d'afficher l'élément qui a été recherché dans la requête et nous a été envoyé par le controller

Si tu es un peu perdu, fais ces étapes toujours dans le même ordre. Afin d'avoir une marche à suivre et comme ça tu verras par la suite que tu sauras où chercher ce qu'il ne va pas et ce qu'il te manque

Prenons l'exemple d'une liste de taches
Les tâches à faire sont déjà enregistrées dans la bdd.

La requete SQL : Retourne moi toutes les taches qui se trouvent dans la table taches
Le controller : Maintenant que j'ai toutes les taches à faire, je les envoies à la vue pour les afficher
La vue: j'affiche toutes les tâches à faire

Si je veux voir les détails pour une tache je clique dessus

Le controller : La méthode pour afficher une seule tache à été appelée lors du clic
La requête SQL : Recherche dans la table tache que la tâche qui correspond celle que je viens de cliquer
Le controller : Maintenant que j'ai obtenu la tâche en question, j'envoi le résultat à la vue 
La vue : J'affiche les détails de la tâche cliquée

Bien sur c'est un peu plus complexe que ça, mais ça reste le même principe de fonctionnement:
Le contrôleur interagit avec le modèle (dans ce cas, la base de données) pour obtenir les données, puis les envoie à la vue pour l'affichage.

## Pour finir
---
Pense à bien revoir le modèle MVC et fait toi une marche à suivre quitte à toujours coder dans le même ordre. Si tu prends ces habitudes tu arriveras à mieux te retrouver dans ce que tu as à faire.

Revois les fonctions, c'est important et tu en auras dans tous les codes. Pense à l'exemple que je t'ai mis avec les paramètres c'est un exemple clair et ça te montre comment utiliser les paramètres

Fais attention avec les requêtes SQL elles sont sensibles à la casse et elles ont une certaine syntaxe. Au moindre doutes n'hésite pas à consulter la doc. Elle est claire et tu peux y trouver facilement ton bonheur.
