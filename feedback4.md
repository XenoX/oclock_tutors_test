# Feedback Apprenant4 PHP Projet Skoule 👤

Bonjour Apprenant4, voici les observations que j'ai pu faire sur ton projet :

```
Je soupçonne que tu es un peu perdu, n'hésite pas à faire appel à moi dès que tu en ressens le besoin, je suis là pour ça. Il n'y a pas de question idiotes ;)
```

## Autoloader ⚙️

Je vois que tu as un soucis au niveau de l'ajout de ton namespace (cf le fichier composer.json) : 

```json
"autoload": {
    "psr-4": {"App\\": "app/"}
}
```

Ce bout de code permet d'ajouter ton namespace "App\\" à l'autoloader de composer.  
Un autoloader est un fichier qui s'occupe de "charger" les classes qu'on utilise dans le projet. C'est grâce à ça qu'on peut "use" des classes quand on en a besoin.  
PSR-4 est le standard pour l'autoloader, inutile pour l'instant d'essayer de comprendre cette instruction.  
Par contre : "App\\": "app/" permet de préfixer ton dossier (ici app/), par le namespace "App\".  
On ajoute "App\" par convention pour éviter un conflit de namespace avec des classes dans tes dépendances (dans le dossier vendor/).

Ici ton souci est "juste" que le dossier "app" n'existe pas, car le tient comporte une majuscule.

Deux solutions : 
- mettre "App/" au lieu de "app/"
- renommer ton dossier App en app

NB : il y a deux slashs sur le namespace pour "échapper", c'est à dire pour qu'il soit interprété en tant que texte.

## Astuces pour comprendre la correction ☑️

Il va falloir procéder étapes par étapes, je te conseil de prendre une fonctionnalité du site, par exemple "la connexion".  
Ensuite tu peux regarder dans la correction, partir du contrôleur frontale pour ensuite arriver jusqu'à la vue (Contrôleur frontal > Router > Contrôleur > Model > Vue).

Si tu as un doute sur le contenu d'une variable, tu peux utiliser la fonction "dd" (dump & die) : dd($myVar) par exemple, une fois que tu rafraichis la page (à condition que ton dd() soit au bon endroit évidemment), tu vas voir son contenu au moment où ton code passe dans le dd().

Une fois que tu as compris la fonctionnalité, tu peux essayer de la reproduire, en premier lieu sur papier avec tes mots ou en pseudo code. Si tu te sens chaud tu peux directement la coder en gardant le chemin d'une requête en tête et n'oublie pas la fonction dd() ;)

Tu as toutes les cartes en main !

## Résumé 📝

Le projet n'est pas très avancé mais c'est carrément rattrapable !  
J'espère que j'ai pu t'aider et te débloquer, n'hésite pas à me contacter si tu as des questions ou un bloc de code que tu veux que j'éclaircisse.  
N'oublie pas de venir me demander de l'aide pendant le cours la prochaine fois ;)

Courage ! Crois en toi !