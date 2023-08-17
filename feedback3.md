# Évaluation de l'apprenant 3

Les bases du projet sont posées. 
Voici quelques conseils qui te permettront de continuer ton projet et comprendre certaines de tes erreurs.

## Coté Back-end

 - **- Ton autoloader semble ne pas fonctionner**
 Il te manque le fichier **.htaccess**.
Ce fichier est important, il permet de modifier la configuration serveur afin de permettre la redirection et la réécriture d'URL entre autre.

- **Héritage de tes classes**
Tu as crée ton projet a l'aide de la POO et c’est très bien. Néanmoin, la **POO** , ***c'est toute une histoire de famille !***
Prends le temps de **penser**, **conceptualiser** celles-ci, cela t'évitera certaines erreurs comme remarqué dans ton projet.
Si tu remarques que plusieurs méthodes de tes controllers sont identique alors crées une **classe mère** et fait **hériter** cette classe a tout tes autres controlleurs. Cela permettra aux enfants de pouvoir utiliser cette méthode sans devoir l'écrire dans chaque controlleur.
***Conseil*** : dans le mode de la POO, il y a aussi des conventions de nommage. Chaque nom de fichier doit être identique au nom de la classe, et en MVC, pour plus de clarté , on nomme  les controlleurs Nomducontroller+Controller et idem pour les classes Model : Nomdumodel+Model.

-  **Problèmes de sécurité** : 

**Problème de sécurité BDD.**

Ne mets pas de donnée en dur dans tes requêtes tu exposes des données **aux injonctions SQL**. Renseigne toi sur la méthode `->prepare()` de PDO.

  **Problème de sécurité Front**

  Que l'on soit ou pas connecté, chaque utilisateur peut accéder aux différentes pages. ***C'est un problème !*** L'axes a tes données et a ta base de données ne doit pas être accessible a tous les utilisateurs. Pour y remédier, donne des rôles différents a tes utilisateurs. La consigne demandait un rôle **admin** et un rôle **user**, pour identifier chaque personne, tu peux procéder comme suit :

-- Une fois l'utilisateur **connecter**, c'est a dire qu'il a indiqué une adresse mail et un mot de passe correspondant a celui de la base de données, **récupère son rôle**.

-- Sur chaque route accorde des droits. Par exemple : la page prof ne doit être accessible uniquement au personne possédant le rôle **admin**. **Mais comment garder en mémoire son rôle de page en page ?** A l'aide des `variables de session`

- **Requêtes SQL :**
Certaines de tes requêtes te renvois une erreur de type : `Warning: PDO::exec(): SQLSTATE[HY000]: General error: 1364 Field 'teacher_id' doesn't have a default value in C:\wamp64\www\apprenant3\app\Models\Student.php on line _39_ ` 
Prends le temps de comprendre les erreurs en PHP , elles sont très souvent explicites et t'indiquent même la ligne de code concerné. Dans l'exemple ci dessus, elle t'indique que tu as une erreur SQL ligne 39 de ton fichier Student.php et que le champ `teacher_id` ne peut pas avoir de valeur par defaut.  Fait donc en sorte de récupérer la valeur  manquante soit l'ID du prof dans ton formulaire d'enregistrement de l'étudiant. 
Pour rappel, l'ID d'une donnée, ici l'ID du teacher correspond à une occurrence en base de données (une ligne dans une table :) ).

- **Erreur instance de classe**
Dans ton fichier **TeacherController** tu instancie l'objet **Teacher** dans la variable `$newTeacher` et tu fait appelle a une variable `$newStudent` pour appeler les methode de celle-ci. Tu t'es tromper de nom de variable.


## Coté Front-end

- **Organises ton code**
Ton **header** et **footer** étant utilisés sur **chaque views**, crée un fichier pour le header et le footer qui seront inclus grace a un **`require`** dans tes différentes pages de ton site.

- **Ta navigation ne semble pas fonctionner**
Les liens de ta **navbar** ne fonctionnent pas. Et c'est normal, tu utilises des chemins de fichiers en dure comme par exemple `index.html`. Utilise plutôt le routeur comme tu l'as fait pour les liens vers la page Profs ou Etudiants.

- **Trop de balises tuent les balises**
Dans certaines pages de ton projet je remarque des balises PHP ouvertes et jamais utilisé, ce n'est pas nécessaire !