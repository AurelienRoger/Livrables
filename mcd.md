User : une ou plusieurs adresse 
User : like ou plusieurs produits
User: avoir une ou plusieurs commandes

Order: Peut contenir un ou plusieurs product
Order: Peut etre généré par un seul user

Product: Est contenu obligatoirement dans un order Et plusieurs product
Product est like par un ou plusieurs user

Relatation: Pas many to many pour le moment

Alors, pour reprendre le fonctionnement du site

## Les cardinalités et relations

### Un utilisateur peut avoir une ou plusieurs adresses.
---
ADRESS 1,1 HAS 0,N USER est correct. A savoir ensuite si l'adresse de livraison est obligatoire ou non.
Si elle l'est, alors il faudra changer les cardinalités 0,N en 1,N (Un user à obligatoirement 1 et Infini adresse)

### Un utilisateur peut "liker" un ou plusieurs produits.
---
Donc pour tes entités USER 1,1 LIKE 1,1 PRODUCT ça ne convient pas. Telles que tu les a écrites, un utilisateur est obligé d'avoir un produit 'like' dès sa création et il ne peut aimer qu'un seul produit. 
Mais aussi un produit ne peut être aimé que par un seul user. Et un produit est obligatoirement aimé par un utilisateur

Les cardinalités seraient alors comme ça : USER 0,N LIKE 0,N PRODUCT. On peut le traduire comme ceci :
- Un utilisateur peut aimer minimum 0 produit et maximum une infinité de produit
- Un produit peut être aimé par minimum 0 user et maximum une infinité de user

Ce que tu as entouré en mettant la relation Many To Many est donc bon, mais pas avec tes cardinalités actuelles.

### Un utilisateur génère une commande
---
Tes cardinalités sont bonnes. En effet un utilisateur peut ne pas avoir de commandes et une commande est générée par un, et un seul utilisateur

### Une commande contient un produit
---
Ici rien à signaler non plus. Un order contient obligatoirement un produit et maximum une infinité. Et un produit peut avoir entre 0 et infini commande.

## Les termes
---

**Attention**
Dans un MCD on ne met **jamais** le terme **id**. Pour un identifiant unique de l'entité, il vaut mieux mettre code avec le nom de l'entité. 
Exemple pour l'entité USER il vaut mieux mettre code_user
Evite aussi au maximum les underscore dans les noms. Colle plutôt les mots en y mettant une majuscule à chaque première lettre du mot. 
N'utilise les underscores que pour les code quelque chose (code_user)

## Pour finir
---

Tu as différents outils pour réaliser un MCD.
Tu as par exemple [Lien](https://mocodo.net "mocodo"). Il est assez complet et facile d'utilisation.
Mais aussi [Lien](https://www.lucidchart.com/ "LucidChart")

Sinon bon MCD dans l'ensemble :D


