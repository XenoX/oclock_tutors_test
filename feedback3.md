# Feedback Apprenant3 PHP Projet Skoule 👤

Bonjour Apprenant3, voici les observations que j'ai pu faire sur ton projet :

```
Je soupçonne que tu es un peu perdu, n'hésite pas à faire appel à moi dès que tu en ressens le besoin, je suis là pour ça. Il n'y a pas de question idiotes ;)
```

## Installation 🔧

Pas de soucis à l'installation et configuration du projet, une petite remarque tout de même sur ton fichier config.ini.  
En effet, celui-ci est versionné, ce qu'il fait que quand on met ses informations de connexion à notre base de données, les changements sont pris en compte par Git.  

Pour palier à ça, tu peux simplement ajouter "config.ini" dans ton gitignore et ajouter un fichier "config.ini.dist" par exemple, qui sera un "modèle". La personne qui clone ton repository pourra simplement copier le config.ini.dist en config.ini et le modifier sans faire de diff dans git.

## Front 🖼️

Côté front, il y a des liens "mort" dans le header, en parlant de lui, j'ai pu voir que tu peux le "mutualiser", c'est-à-dire faire un fichier header.php par exemple, mettre le code de ta barre de navigation et les balises html, head etc (fichier app/views/layout/header.tpl.php de la correction)

Comme tu peux voir, certaines balises ne se ferment pas mais c'est normal, car du contenu va venir à la suite (le contenu de la page que tu veux afficher). Et ensuite tu peux faire pareil pour le bas de la page (le footer) ! 

Maintenant il suffit d'ajouter les "require_once" pour inclure ton header avant ton contenu et ton footer après ton contenu, tu peux voir ça ligne 165, 166 et 167 du CoreController.php dans la correction.

## Back ⚙️

On va se focaliser sur la méthodologie. Il faut y aller étapes par étapes, se fixer des petits jalons dans tes étapes, c'est le meilleur moyen d'avancer et de ne pas se décourager.  

Découpons le "projet" en parties :
- Contrôleur frontal (public/index.php)
- Router
- Contrôleurs
- Modèles
- Vues

### Le contrôleur frontal (index.php)

C'est vraiment le point d'entrer de ton site, il doit être accessible depuis le navigateur du client, c'est pour cela qu'il se trouve dans le dossier "public".  
Son rôle est de démarrer tout ce dont on aura besoin plus tard :
- La session
- L'autoloader (les dépendances)
- Le routeur
- Des variables si besoin

Au delà de "démarrer" le routeur, c'est aussi ce fichier qui délègue la requête au routeur (que j'explique juste après).

### Le routeur

Pour faire simple, le routeur récupère une requête, par exemple un 'GET' sur "/contact", en fonction de ces informations, il va être capable d'appeler la bonne méthode du bon contrôleur. Comme un aiguilleur du rail :)

### Les contrôleurs

Ils sont donc appelés par ton routeur. Leur rôle est de faire un traitement (si besoin) et de "rendre" quelque chose, dans la plupart des cas ce sera une vue (du HTML), une redirection ou des données au format JSON ou XML par exemple.  
S'ils ont besoin de récupérer des données en base de données, ils vont faire appel aux modèles (que j'explique juste après), ensuite on peut imaginer un traitement sur les données et l'ajout d'une condition et hop, on envoie les données à la vue.

### Les modèles

Un modèle est une classe PHP qui (pour simplifier) représente une table dans ta base de données. Cela va permettre de manipuler tes données sous la forme d'objet PHP, c'est quand même plus pratique et maintenable que sous forme d'un tableau.

### Les vues

Ce sont tes fichiers avec le code HTML/CSS/JS qui sera affiché et interprété par le navigateur du client.  
Il est possible d'avoir du PHP dedans (pour ça que ce sont des .php), pour pouvoir ajouter de la logique (boucles, conditions...).  
Le code PHP n'est pas envoyé au front par contre, il est interprété par PHP sur le serveur et transformer en HTML si besoin.  

Exemple : une boucle avec 100 itérations, dans cette boucle on affiche une citation au hasard. Le serveur va lire la boucle PHP, générer les 100 citations et va renvoyer tout cela au client (en HTML donc).

### Résumé

Tout ce qu'on vient de voir, c'est un modèle de conception connu sous le nom de "MVC" "Model Vue Controller", ce qui permet de scinder le code dans des fichiers différents, c'est plus clair et maintenable.

## Astuces pour comprendre la correction ☑️

Il va falloir procéder étapes par étapes, je te conseil de prendre une fonctionnalité du site, par exemple "la connexion".  
Ensuite tu peux regarder dans la correction, partir du contrôleur frontale pour ensuite arriver jusqu'à la vue (Contrôleur frontal > Router > Contrôleur > Model > Vue).

Si tu as un doute sur le contenu d'une variable, tu peux utiliser la fonction "dd" (dump & die) : dd($myVar) par exemple, une fois que tu rafraichis la page (à condition que ton dd() soit au bon endroit évidemment), tu vas voir son contenu au moment où ton code passe dans le dd().

Une fois que tu as compris la fonctionnalité, tu peux essayer de la reproduire, en premier lieu sur papier avec tes mots ou en pseudo code. Si tu te sens chaud tu peux directement la coder en gardant le chemin d'une requête en tête et n'oublie pas la fonction dd() ;)

Tu as toutes les cartes en main !

## Résumé 📝

Le projet n'est pas très avancé mais c'est carrément rattrapable !  
J'espère que j'ai pu t'aider, n'hésite pas à me contacter si tu as des questions ou un bloc de code que tu veux que j'éclaircisse.  
N'oublie pas de venir me demander de l'aide pendant le cours la prochaine fois ;)

Courage ! Crois en toi !