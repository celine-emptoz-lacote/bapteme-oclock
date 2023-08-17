# Évaluation de l'apprenant 4

Les bases du projet sont posées et le MCV est compris. 
De trop nombreux fichiers manquant ne me permettent pas de te faire un retour complet.
Dans ton repo de ton projet, il te manque les fichiers suivants : 

 - **.htaccess :** empêchant le bon fonctionnement de ton projet. Ce fichier est important, il permet de modifier la configuration serveur afin de permettre la redirection et la réécriture d'URL entre autre.
 - **MainController**
 - **CoreController**
 - **Du dossier layout avec les fichiers header et footer.php**


Voici quelques conseils qui te permettront de continuer ton projet et comprendre certaines de tes erreurs.

## Coté Back-end


- **Les classes**
Pour instancier une classe (créer une classe), il faut créer une variable portant un nom explicite comme par exemple `$studentModel`, en suite on va instancier la classe 

    // Le nom qui suit new correspond au nom de la classe que l'on souhaite
    $studentModel = new Students();
    
La variable `$studentModel` devient une variable d'instance.
Dans `$studentModel`, s'y trouvent toutes les méthodes liées a cette classe.

La **POO** , ***c'est toute une histoire de famille !***

Prends le temps de **penser**, **conceptualiser** celles-ci, cela t'évitera certaines erreurs comme remarqué dans ton projet.

Chaque classe doit regrouper les méthodes liée a celle-ci. Dans l'exemple plus haut, on a instancié la classe `StudentsController`. Dans celle-ci, on y retrouvera seulement les méthodes liées aux étudiants et seulement aux étudiants. Dans ton projet, on trouve des méthodes qui modifient des profs.

***Conseil*** : dans le mode de la POO, il y a aussi des conventions de nommage. Chaque nom de fichier doit être identique au nom de la classe, et en MVC, pour plus de clarté , on nomme  les controlleurs Nomducontroller+Controller et idem pour les classes Model : Nomdumodel+Model.

-  **Problèmes de sécurité** : 

**Problème de sécurité BDD.**

Ne mets pas de donnée en dur dans tes requêtes tu exposes des données **aux injonctions SQL**. Renseigne toi sur la méthode `->prepare()` de PDO.

Toutes les données de tes formulaires doivent être récupérées et vérifiées. Tu ne peux pas faire confiance  aux utilisateurs. Tu risques de compromettre tes données, de te les faire volées ou de te les faire effacer...

  **Problème de sécurité Front**

Penses a donner des droits pour chaques routes afin de proteger tes données !


## Coté Front-end

- **Organises ton code**
Ton **header** et **footer** étant utilisés sur **chaque views**, crée un fichier pour le header et le footer qui seront inclus grace a un **`require`** dans tes différentes pages de ton site.
