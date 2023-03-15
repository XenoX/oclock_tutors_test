# Feedback Apprenant1 PHP Projet Skoule 👤

Bonjour Apprenant1, voici les observations que j'ai pu faire sur ton projet :

## Installation 🔧

Pas de soucis à l'installation et configuration du projet, une petite remarque tout de même sur ton fichier config.ini.  
En effet, celui-ci est versionné, ce qu'il fait que quand on met ses informations de connexion à notre base de données, les changements sont pris en compte par Git.  

Pour palier à ça, tu peux simplement ajouter "config.ini" dans ton gitignore et ajouter un fichier "config.ini.dist" par exemple, qui sera un "modèle". La personne qui clone ton repository pourra simplement copier le config.ini.dist en config.ini et le modifier sans faire de diff dans git.

## Front 🖼️

Côté front, je vois que tu as un fichier d'update différent du fichier de création (pour les professeurs par exemple), ces fichiers se ressemblent donc on peut imaginer les mutualiser et conditionner quelques petites choses.  
Principe connu sous l'accronyme "DRY" (Don't Repeat Yourself), dès que tu vois un bloc de code similaire à un autre, il y a surement la possibilité de le mutualiser.  
Cela peut être fait en deux étapes si tu ne te sens pas à l'aise, tu peux faire tes deux fichiers et ensuite "refactoriser" pour n'en faire plus qu'un.

## Back ⚙️

Plusieurs petites astuces pour ton code PHP :  

- La qualité d'écritude du code peut être amélioré, en suivant les standards PHP (PSR) => https://www.php-fig.org/psr/psr-12/. Tu peux aussi utiliser un "linter", c'est un outil console ou directement sur ton IDE pour vérifier la qualité d'écritude de ton code PHP (PHP-CS par exemple)
- Le fichier index.php contient aussi tes routes, celles-ci auraient pu être dans un autre fichier "routes.php" par exemple avec un require_once depuis ton fichier index.php
- Les noms de tes contrôleurs sont très bien, au niveau des noms des méthodes, elles sont un peu redondantes avec le nom de ton controller, par exemple TeacherController::teacherDelete(), nous sommes dans le controller Teacher donc on peut en déduire que la méthode "delete" est pour supprimer un professeur (en base de données évidemment :p)
- La liste des professeurs doit être accessible par un utilisateur avec le rang "user", petit oubli j'imagine :)
- Les modifications ne fonctionnent pas malheureusement mais il ne manque pas grand-chose. La route "action" de tes formulaires de modifications n'est pas la bonne. Dans la plupart des cas, pas besoin de renseigner de valeur dans l'action d'un formulaire, car par défaut il POST sur la route courante, c'est ce qu'on veut ici ;)

J'ai aussi observé que tu n'utilisais pas de classe abstraites. C'est pourtant pratique, car ça permet d'être certain que notre classe ne soit jamais instanciée.  
Pour le CoreController par exemple, c'est juste une classe "mère", dont les autres controllers vont hériter, au même titre que ta classe CoreModel avec tes modèles.  
Au niveau de ton CoreController, n'hésite pas à lui ajouter des méthodes "génériques" à tes contrôleurs, comme une redirection vers une autre route par exemple (DRY principle ;))
Au niveau du CoreModel, pareil pour la propriété $status qui se trouve sur tous tes autres modèles :)

## Résumé 📝

Projet facile à installer, rapidement fonctionnel, quelques améliorations au niveau de la qualité de code (DRY + PSR-12 + Nommage).  
Félicitations pour les bonus, la validation des données, la liste des utilisateurs et la CRUD des étudiants et des professeurs (même si l'édition n'était pas 100% fonctionnelle, il ne manquait pas grand-chose :))