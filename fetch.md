Permets de faire du javascript asynchrone. On va demander d'aller chercher des données vers un serveur, un fichier ..., et  le reste du code va continuer de s'exécuter. Puis avec les données recus , on va faire quelque chose. Et tout ca sans rechargement de la page.
Fetch est une fonctionnalité fourni par javascript nativement, c'est le descendant de plusieurs methodes, bien plus compliqué a mettre en place.

***Qu'est-ce que l'asynchrone ? synchrone ?***
Pour comprendre ces notions compliquées, prennons l'exemple d'un serveur dans un restaurant.

**Synchrone** : Imagine que tu es un serveur qui prend les commandes de manière synchrone. Cela signifie que tu attends que chaque client te donne sa commande, tu la portes en cuisine, attends que le chef prépare le plat, puis reviens à la table du client avec la nourriture avant de passer à la commande suivante.

En dev, une opération synchrone se déroule de manière séquentielle. Par exemple, si tu devais rechercher plusieurs pages web, tu attendrais que chaque page soit récupérée avant de passer à la suivante.

**Asynchrone** : Maintenant, imagine que tu es un serveur asynchrone. Cela signifie que dès qu'un client te donne sa commande, tu l'envoies en cuisine et passes immédiatement à prendre la commande du client suivant, sans attendre que le premier plat soit préparé. Pendant que le chef cuisine, tu peux même servir d'autres tables.

Une opération asynchrone signifie que le programme n'attend pas nécessairement la fin d'une tâche pour en commencer une autre. Par exemple, lorsqu'une application envoie une requête asynchrone à un serveur, elle peut continuer à fonctionner et effectuer d'autres tâches pendant qu'elle attend la réponse du serveur. Pour rappel le code est lu de haut en bas.

Fetch permet de faire des **requêtes HTTP** depuis le navigateur et c'est le navigateur qui réceptionne la donnée.

***Clarifions qu'est-ce qu'une requête HTTP ?***
Une requête HTTP (Hypertext Transfer Protocol) est un protocole de communication utilisé par les navigateurs web et les serveurs pour échanger des données sur Internet. C'est le moyen standard grâce auquel ton navigateur demande des ressources ou des services à un serveur distant. Voici les éléments clés d'une requête HTTP

***Comment on fait ?***
Donc comme toute fonction elle a besoin de plusieurs paramètres pour fonctionner :

 1. URL corresponds à l'URL que vous voulez consulté
 2. Un objet avec plusieurs paramètres comme par exemple la méthode de la requête ( GET , POST , DELETE ...) , les entetes ... Ce deuxième paramètre est optionnel.

>    `fetch(URL,OBJET)`

 Comme toute fonction digne de ce nom, elle te renvoie une réponse, que l'on appelle une promesse. 
 
  ***Une promesse, qu'est-ce que c'est ?*** 
Et bien comme son nom l'indique, le navigateur te promet de te renvoyer quelque chose, ce que tu attends ou peu être une erreur mais quand ? ca on ne sait pas...

Reprenons le sujet skoule. 
Prenons l'exemple de vouloir qu'au click sur un bouton la liste des profs s'affiche.

 1. Apres avoir créer un event avec js (click sur un bouton) biensur sans rechargement de la page. On appele Fetch avec l'URL .


>   ` fetch("http://localhost/apprenant2/public/students")`


2. Je veux récupérer la liste des étudiants, et récupérer la promesse, pour se faire je vais utiliser une **fonction callback.**

***Qu'est-ce qu'une fonction callback ?***
C'est une methode qui attends qu'une action soit terminer pour passer à la suite.
Je veux donc attendre que fetch ai recu la data pour faire quelque chose.

Pour se faire je vais utiliser `.then` qui permet d'attendre que le serveur ai renvoyer la donnée, et je veux l'afficher 

>      `fetch("http://localhost/apprenant2/public/students")
>           `.then( response => console.log(response) )`

	
Ce qui sera afficher en console est un objet de type response avec de nombreuses valeurs. 
On a un propriété `ok`, elle est importante elle permet de voir si la reponse est bonne ou non.

Afficher la reponse dans la console est une premiere étape mais, a cette etape nous ne recuperons pas encore les donneées.

3. Recuperons les données
Dans notre exemple, la route en PHP nous renvois une liste d'étudiants sous format JSON.

 

>     `fetch('http://localhost/apprenant2/public/students")
>     	    .then(response => {
>     	    	    response.json()
>     		    }`

Ici dans notre callback .then, on utilise une methode `.json()` qui nous renverra le body de la requette sous format json.
Lorsque ce callback sera fini, on fera appel a notre deuxieme callback : 

>     ` fetch(http://localhost/apprenant2/public/students)
>     		.then(response => {
> 		    		response.json()
> 		    	}
> 		    .then(data => console.log(data)`

Notre deuxieme callback est utilisé pour recuperer notre données parsée et utilisable. A cette étape, nous avons la donnée.

Maintenant plus qu'a essayer, rien de mieux c'est une petite lecture de la documentation afin de voir toute les fonctionalité de fetch : https://developer.mozilla.org/fr/docs/Web/API/Fetch_API/Using_Fetch

Bon courage !