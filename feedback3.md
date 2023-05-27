Hello ! Voici le feedback que tu m'as demandé.


### Boucles et affichage cardDetails.ejs


Faire une boucle dans le code, c'est pour itérer plusieurs fois jusqu'à ce qu'une condition soit atteinte ou un but rempli.
Prenons par exemple un tableau javascript constitué de chiffres de 1 à 10
```js
const array = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
```
Si je souhaite afficher tous les résultats un par un avec des console.log(), je vais faire une boucle dessus
```js
for (nombre of array) {
 console.log(nombre)
}
```
Ici, les console.log() afficherons 1 puis 2 puis 3 ... et enfin 10.


C'est le même cas dans notre code avec les cards. Chaque carte est un objet. Et cet objet nous le mettons dans la constante cards qui est créée lorsque qu'on utilise la méthode homePage de mainController. Cette constante cards est un tableau ( plus précisément un tableau d'objets ).


Maintenant qu'on a notre tableau, sur la page d'accueil on affiche tous les résultats du tableau un par un. Donc, on utilise une boucle. Une boucle qui se fait sur le tableau cards. Comme dans l'exemple avec les nombres.


En récupérant la carte qu'on veut afficher directement avec une requête SQL, tu obtiens une constante qui n'est pas itérable. Tu n'as qu'un seul élément dedans donc pour afficher les détails de la carte voulue, tu n'as pas besoin de faire de boucle dessus.


### Requête SQL


Fais attention à la syntaxe dans tes requêtes SQL. Les requêtes sont sensibles à la casse ( il y a une difference entre majuscules et minuscules par exemple ), et à la ponctuation.


Les points virgule dans une requête SQL servent à séparer les instructions


Dans le cas de ta requête getCard, il n'y a qu'une seule instruction
Je te laisse revoir les requêtes SQL dans tes cours


### Passage de variables avec le router


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


Et en +, tu as pensé à convertir l'id que tu as récupéré en nombre !


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


### Fonction next()


Attention à son utilisation. C'est pratique, car le code continu, mais c'est dangereux. En effet, s'il y a une erreur à cet endroit-là, tu ne la verras pas car dans tous les cas, tu passes à la suite. Il vaut mieux être prudent et signaler l'erreur, par une page not found au moins


Cette fonction-là est à utiliser vraiment avec précautions. Si tu ne veux pas afficher d'erreur sur la page ou mettre une 404, met au moins un console.log() pour dire qu'il y a une erreur et savoir que c'est à cet endroit-là.


### Recherche par élément


Pense à bien importer tes modules au début de ton fichier. Dans le cas du parcours, les modules correspondent à d'autres fichiers js. Mais si tu ne l'importe pas, tu ne peux pas utiliser l'objet et les méthodes qui se trouvent dedans.
La console peut t'aider dans ces cas là, la plupart du temps cela te désigne avec précision l'erreur qu'il y a.


### Pour finir


N'hésite pas à mettre des console.log() partout s'il le faut pour contrôler ce que tu obtiens. C'est vraiment important et ça permet de savoir ce qu'il se passe dans ton code. Tu peux en abuser ce n'est pas un problème


N'hésite pas à regarder les messages d'erreurs dans ta console aussi, généralement ils sont explicites et cela indique où se trouvent les erreurs. Et si tu ne comprend pas le message d'erreur, un copier-coller sur google et tu trouveras certainement quelque chose qui s'en rapproche. D'autres l'ont faite avant toi.


Les boucles c'est important tu vas les utiliser ( et ne pas les utiliser ) très souvent. N'hésite pas à aller sur la doc officielle de mdn pour mieux comprendre leur fonctionnement
[Lien](https://developer.mozilla.org/fr/docs/Web/JavaScript/Guide/Loops_and_iteration#linstruction_for...of "doc mdn").