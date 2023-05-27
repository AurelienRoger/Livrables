
Hello ! Voici le feedback que tu m'as demandé.
Déjà félicitation pour ton travail, le site fonctionne quasiment comme attendu. Quelques petits détails sont manquants ou peuvent tout de même être améliorés

## Recherche par élément 
---
Lorsque nous faisons une recherche par éléments, il y a bien la liste qui s'affiche et ce sont les bons résultats attendus
Ce qui serait cool, c'est de voir directement les détails de la carte, sans devoir cliquer dessus. Ta réfléxion est bonne, on clique sur le lien de la carte pour l'affichée
Mais il y a aussi la possibilité d'afficher directement les détails des cartes recherchées.

Pour trier les résultats retournés, tu utilises la méthode filter. C'est un bon raisonnement aussi. Mais tu peux directement trier tes résultats renvoyés dans une requête SQL en passant des arguments à ta requête.
Cette démarche consommera moins de ressources lors de tes renvois de données et moins de temps de chargement. Ici ça va, mais imagine une application avec + de 20 000 cartes.
Si tu fais une requête pour toutes les récupérées, cela prendra + de temps que de les trier directement dans ta requête.

## Ajout de cartes dans le deck
---
Déjà, c'est super tu gères l'ajout des cartes, et si elles existent elles ne se rajoutent pas. 
Il manque le lien de suppression sur les cartes dans le deck tu pourrais l'afficher directement sur la carte dans ta vue de deck. C'est le même lien que l'ajout de carte, mais avec une route différente

Dans ton controller deckController.js tu ne vérifie pas si le nombre de cartes est strictement inférieur à 5. Ce qui fait qu'on peut ajouter autant de cartes dans le deck qu'on le souhaite. Il faudrait que tu controle le nombre de carte présentes dans ton deck dans ta méthode addDeck avec une condition. 
Tu peux le faire après avoir vérifier si la carte n'existe pas déjà par exemple

Et j'ai vu que tu as mis un card.price dans ta vue deck.ejs, une future idée d'amélioration? :D

## Commentaires
---
Je ne vois aucunes lignes vertes dans ton code (les commentaires :D) Certe ça fait propre mais quelques commentaires bien placés permettent de voir en un coup d'oeil ce que la méthode ou l'action doit faire 
Je ne dis pas qu'il faut en mettre à chaques lignes, mais si tu peux mettre au moins un commentaire pour décrire ce que la méthode doit faire ce serait top ! 
Et si jamais tu dois rouvrir ce code dans les mois à venir, tu pourras voir tout de suite ce que dois faire ton code
