# Évaluation de l'apprenant 1

Bon projet dans l'ensemble. Les exigences de l'exercice sont respectées.

Néanmoins j'ai repérer quelques problèmes : 

## Coté Back-end

 **- Ton autoloader semble ne pas fonctionner**
Il te manque le fichier **.htaccess**.
Ce fichier est important, il permet de modifier la configuration serveur afin de permettre la redirection et la réécriture d'URL entre autre.

 - **La mise a jour des informations des profs et étudiants ne fonctionne pas et me renvois vers un 404.**

 - **Ton fichier index.php est beaucoup trop long.**
Ce fichier est la porte d'entrée de ton application. Elle doit contenir que le strict minimum.  Il serait donc bien de mettre toutes les définitions de tes routes dans un autre fichier et l'importer dans ton index.

 - **Décide d'une convention et tiens toi s’y.** 
Dans le nom de tes routes, on peut constater des routes en kebab cases et snakes case. Choisi en une et utilise uniquement celle la.
Exemple : `"main-home"` et `"signin_get"` devrais etre soit `"main-home"` et `"signin-get"` ou `"main_home"` et `"signin_get"`.
De plus, je remarque que tu ecris des commentaires et des noms de variable en français et en anglais. Dans la même idée fait un chois en amont du projet, en gardant en tête que l'anglais est une langue universelle.

 - **Problème de sécurité.**
Ne mets pas de donnée en dur dans tes requêtes, tu exposes des données **aux injonctions SQL**. Renseigne toi sur la méthode `->prepare()` de PDO. 

 - **Doublon de données.**
Pense a vérifier dans tes modèles si un student ou teacher n'existe pas. Cela évitera une surcharge de la BDD avec des doublons de données.

 - **GitHub**
 Pour un projet propre pense a mettre des messages de commit clair et précis. Un commit clair permet d’identifier une feature plus facilement. 

## Coté Front-end

 - **Balise HTML manquante**
Chaque texte inséré dans un page doit avoir une balise. `error_403.tpl.php`

 - **Indentation de ton code**
Ton code HTML est souvent mal indenté, comme dans le fichier `home.tpl.php` ou encore `error-404.tpl.php`. Un code bien indenté facilite la lecture
 