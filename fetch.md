# Fetch

## Informations générales

La fonction "fetch" est une méthode native de Javascript qui est utilisée pour effectuer des requêtes HTTP asynchrones vers des ressources externes telles que des API. Elle permet de récupérer des données depuis un serveur et de les utiliser dans le code. La syntaxe de base de la fonction "fetch" est la suivante :

```javascript
fetch(url)
  .then(response => {
    // traitement de la réponse
  })
  .catch(error => {
    // gestion des erreurs (si il y a une erreur)
  });
```

"url" représente l'adresse de la ressource externe que tu souhaites récupérer. La méthode "fetch" retourne une "promesse" qui est résolue avec un objet "Response" représentant la réponse de la requête HTTP.

Une fois que la promesse est résolue, tu peux utiliser la méthode ".json()" pour transformer la réponse sous la forme d'un objet JSON.  
Voici un exemple de code pour extraire des données JSON à partir d'une requête "fetch" :

```javascript
fetch(url)
  .then(response => response.json())
  .then(data => {
    // traitement des données
  })
  .catch(error => {
    // gestion des erreurs (si il y a une erreur)
  });
```

## Cas pratique avec ton projet

Tes routes retournent du HTML, la réponse du fetch sera donc du texte.

On va prendre ta page d'accueil et faire un fetch dessus pour récupérer le HTML de la page.

### Avec le chainage de méthodes then

```javascript
fetch('http://127.0.0.1:8000/')
  .then(response => {
    return response.text();
  })
  .then(html => {
    console.log(html);
  })
  .catch(error => {
    console.error(error);
  })
;
```

Ci-dessus, la méthode avec les .then(), vu que c'est de l'asynchrone, la méthode "then" permet d'attendre que le traitement qui est fait dans la méthode d'avant soit terminé (qu'elle "return" quelque chose).  
Ici on attend le retour du fetch, une fois qu'on l'a, on rentre dans le 1er then, on transforme la réponse en text et on le retourne pour enchaîner sur le prochain then qui affiche le contenu dans la console. Pas besoin de faire un return ici car nous n'avons rien après le console.log.

Nous avons bien le code HTML de ta page d'accueil affiché dans la console ! :)

Il y a une autre façon de faire que je te montre ci-dessous.

### Avec les async/await

```javascript
async function logHomepage() {
  const response = await fetch('http://127.0.0.1:8000/');
  const text = await response.text();
  console.log(text);
}
logHomepage();
```

Ici on déclare une fonction en asynchrone (async), ce qui nous permet d'utiliser le mot clef "await", ce mot clef permet d'attendre la réponse de l'instruction qu'il y a après (le fetch par exemple). Une fois que le fetch est terminé, le script continue et passe à la ligne suivante (le response.text() ici)

## Aller plus loin

Il est possible que tu aies besoin de passer des paramètres, soit dans l'URL (query params) soit dans le body, pour une requête POST par exemple.

```javascript
const data = { username: 'johndoe', password: 'secret' };

fetch(`https://api.example.com/login?redirectTo=dashboard`, {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json'
  },
  body: JSON.stringify(data),
})
  .then(response => response.json())
  .then(data => console.log(data))
;
```

Dans cet exemple, nous avons utilisé la méthode POST pour envoyer des données à notre API. Nous avons également ajouté un query paramètre 'redirectTo' à notre URL, qui contient la valeur 'dashboard'.

Pour inclure les données de notre requête, nous avons créé un objet data contenant un nom d'utilisateur et un mot de passe. Nous avons ensuite converti cet objet en une chaîne JSON en utilisant JSON.stringify, et l'avons ajouté à la requête en utilisant la propriété body.

Nous avons aussi ajouté un header 'Content-Type' avec 'application/json' en valeur pour spécifier que notre body est au format json.

J'espère que cet exemple t'aide à comprendre comment faire une requête fetch en utilisant une méthode différente et en envoyant des données à l'aide de la propriété body. N'hésite pas à me poser des questions si tu en as !

## Resources

Si tu veux tout savoir sur les promises, tu peux approfondir ici : https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise

Sur le fetch, c'est par ici : https://developer.mozilla.org/fr/docs/Web/API/fetch

L'asynchrone en Javascript : https://developer.mozilla.org/fr/docs/Learn/JavaScript/Asynchronous

N'hésite pas à me contacter si tu as des questions :) !