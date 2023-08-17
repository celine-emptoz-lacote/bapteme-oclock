# Évaluation de l'apprenant 2

Bon début de projet, le concept de MVC est compris.

Par cette évaluation je vais te donner des pistes d'améliorations concernant certains problèmes rencontrés : 

## Coté Back-end

- **Méthode HTTP**
Les méthodes que tu utilises pour tes routes ne sont pas toujours corrects. Pour la route **/teacher/add** qui te permet d'ajouter un prof, la méthode GET est utilisée au lieu de la méthode POST.

Rappel des méthodes HTTP :
- **GET** : Permet seulement de récupérer des données du serveur.
- **POST** : Permet d'envoyer des données au serveur, biensur on pense à les sécurisées avant :)
- **DELETE** : Permet de supprimer une donnée
- **PUT** : Permet de remplacer l'intégralité des infos d'une donnée (nom, prénom, ...) 
- **PATCH** : Permet de remplacer une seule info d'une donnée

- **Problèmes de sécurité**

 **Problème de sécurité BDD.**
	 
	 
Ne mets pas de donnée en dur dans tes requêtes tu exposes des données **aux injonctions SQL**. Renseigne toi sur la méthode `->prepare()` de PDO.

   **Problème de sécurité Front**

Que l'on soit ou pas connecté, chaque utilisateur peut accéder aux différentes pages. ***C'est un problème !*** L'axes a tes données et a ta base de données ne doit pas être accessible a tous les utilisateurs. Pour y remédier, donne des rôles différents a tes utilisateurs. La consigne demandait un rôle **admin** et un rôle **user**, pour identifier chaque personne, tu peux procéder comme suit :
				-- Une fois l'utilisateur **connecter**, c'est a dire qu'il a indiqué une adresse mail et un mot de passe correspondant a celui de la base de données, **récupère son rôle**.
				-- Sur chaque route accorde des droits. Par exemple : la page prof ne doit être accessible uniquement au personne possédant le rôle **admin**. **Mais comment garder en mémoire son rôle de page en page ?** A l'aide des `variables de session`
				
- **Erreurs qui s'affichent sur la page utilisateurs.**

Tu as oublié de mettre un dossier views ***errors*** avec un fichier ***err404***  contenant le code HTML de la page d'erreur.

- **Certains liens ne menant pas sur la bonne page.**

Pour modifier un formateur, je suis rediriger vers un formulaire d'ajout d'un formateur.

- **Formulaire d'ajout ne fonctionne pas.**

Ton formulaire ne fonctionne pas pour différentes raisons : 
			-	Il n'y a pas de **redirection** dans la propriété ***action*** de ton code HTML.
			-	Ajoute une méthode dans ta classe **TeachersController** qui aura pour but de ***récupérer les données*** de ton formulaire et de les ***sécurisés***.
			-	Créer une méthode dans la classe **TeacherModel** qui a pour but ***d'ajouter la donnée*** en BDD.

- **Attention aux conventions de nommage des fichiers Model**

Nomme tes fichiers comme tes noms de classe ainsi que le mot model afin de repérer rapidement les contrôleurs des Models.
Par exemple : `TeacherModel`  pour ta classe TeacherModel

- **Évite de te répéter.**

Pour éviter de répéter du code et ***oui je te rapelle qu'un développeur ne se répète jamais !(DRY)***, mets l’ensemble des données communes des models, comme par exemple la connexion a **PDO**, dans ta classe mère `CoreModel`. En cas de changement, tu sauras ou se touve la connexion à la BDD sans devoir modifier de nombreux fichiers.

-**Organise ton fichier index.php.**

Ce fichier est la porte d'entrée de ton application. Elle doit contenir que le strict minimum. Il serait donc bien de mettre toutes les définitions de tes routes dans un autre fichier et l'importer dans ton index.

-  **GitHub**

Pour un projet propre pense a mettre des messages de commit clair et précis. Un commit clair permet d’identifier une feature plus facilement.

## Coté Front-end

--  **Indentation de ton code**
Ton code HTML est souvent mal indenté.