# Module 1 : Introduction à JavaScript

## 1.1 : Les bases de JavaScript

### Introduction à JavaScript
JavaScript est un langage de programmation essentiel pour le développement web. Il permet de rendre les pages web interactives et dynamiques. Il fonctionne principalement côté client, mais peut aussi être utilisé côté serveur avec Node.js.

**Exemple** :
```html
<!DOCTYPE html>
<html>
<head>
    <title>Introduction à JavaScript</title>
</head>
<body>
    <h1>Bienvenue</h1>
    <button onclick="afficherMessage()">Cliquez-moi</button>
    <script>
        function afficherMessage() {
            alert('Bonjour, ceci est un message JavaScript!');
        }
    </script>
</body>
</html>
```

### Variables et types de données
- `var`: Ancienne manière de déclarer des variables.
- `let`: Variable modifiable dans une portée limitée au bloc.
- `const`: Variable constante, non modifiable.

**Exemple** :
```javascript
let nom = "Alice";
const age = 25;
var pays = "France";
console.log(nom, age, pays);
```

### Opérateurs
1. **Arithmétiques** : +, -, *, /, %
2. **Logiques** : &&, ||, !
3. **Comparaison** : ==, ===, !=, !==, <, >, <=, >=

**Exemple** :
```javascript
let a = 5, b = 10;
console.log(a + b); // Addition
console.log(a > b); // Comparaison
```

### Structures de contrôle
- `if`, `else` :
```javascript
if (a > b) {
    console.log("a est plus grand que b");
} else {
    console.log("a est plus petit ou égal à b");
}
```
- `switch` :
```javascript
switch (a) {
    case 5:
        console.log("a vaut 5");
        break;
    default:
        console.log("Valeur inconnue");
}
```
- Boucles : `for`, `while`, `do-while`

**Exemple** :
```javascript
for (let i = 0; i < 5; i++) {
    console.log(i);
}
```

### Fonctions
1. **Déclaration** :
```javascript
function addition(a, b) {
    return a + b;
}
```
2. **Expression** :
```javascript
const soustraction = function(a, b) {
    return a - b;
};
```
3. **Flèche** :
```javascript
const multiplication = (a, b) => a * b;
```

## 1.2 : Concepts avancés en JavaScript

### Portée et fermeture (Closures)
La portée d’une variable dépend de l’endroit où elle est déclarée. Une fermeture permet à une fonction interne d’accéder aux variables de sa fonction parente.

**Exemple** :
```javascript
function createCounter() {
    let count = 0;
    return function() {
        count++;
        return count;
    };
}
const counter = createCounter();
console.log(counter()); // 1
console.log(counter()); // 2
```

### Prototypes et héritage
JavaScript utilise un modèle basé sur les prototypes pour l’héritage.

**Exemple** :
```javascript
function Person(name) {
    this.name = name;
}
Person.prototype.sayHello = function() {
    console.log(`Bonjour, je m'appelle ${this.name}`);
};
const alice = new Person("Alice");
alice.sayHello();
```

### Programmation Orientée Objet (POO)
**Classes et héritage** :
```javascript
class Animal {
    constructor(nom) {
        this.nom = nom;
    }
    parler() {
        console.log(`${this.nom} fait un bruit.`);
    }
}
class Chien extends Animal {
    parler() {
        console.log(`${this.nom} aboie.`);
    }
}
const rex = new Chien("Rex");
rex.parler();
```

### Gestion des erreurs
```javascript
try {
    throw new Error("Une erreur est survenue");
} catch (error) {
    console.error(error.message);
} finally {
    console.log("Bloc finally exécuté");
}
```

### Manipulation du DOM
```javascript
const button = document.querySelector("button");
button.addEventListener("click", () => {
    document.body.style.backgroundColor = "blue";
});
```

## 1.3 : Manipulation des données et APIs

### Tableaux et objets
**Exemple** :
```javascript
const nombres = [1, 2, 3, 4, 5];
const doubles = nombres.map(n => n * 2);
console.log(doubles);
```

### JSON
```javascript
const utilisateur = { nom: "Alice", age: 25 };
const json = JSON.stringify(utilisateur);
console.log(json);
```

### Asynchronisme
```javascript
async function fetchData() {
    try {
        const response = await fetch("https://api.example.com/data");
        const data = await response.json();
        console.log(data);
    } catch (error) {
        console.error("Erreur lors de la récupération des données", error);
    }
}
fetchData();
```

### Fetch API : appels REST
#### GET Request :
```javascript
fetch("https://api.example.com/posts")
    .then(response => response.json())
    .then(data => console.log(data))
    .catch(error => console.error("Erreur: ", error));
```
#### POST Request :
```javascript
fetch("https://api.example.com/posts", {
    method: "POST",
    headers: {
        "Content-Type": "application/json",
    },
    body: JSON.stringify({ title: "Nouvel Article", content: "Ceci est le contenu." })
})
    .then(response => response.json())
    .then(data => console.log(data))
    .catch(error => console.error("Erreur: ", error));
```

## 1.4 : Outils modernes de JavaScript

### ES6+ Modules
```javascript
// addition.js
export const addition = (a, b) => a + b;

// main.js
import { addition } from "./addition.js";
console.log(addition(5, 10));
```

### Babel et Webpack
- **Babel** : Convertit le code moderne en une version compatible avec les anciens navigateurs.
- **Webpack** : Outil de bundling pour regrouper plusieurs fichiers JavaScript en un seul fichier utilisable.

### Introduction à Node.js
Node.js permet d’exécuter JavaScript côté serveur.

**Exemple** :
```javascript
const http = require("http");
const server = http.createServer((req, res) => {
    res.statusCode = 200;
    res.setHeader("Content-Type", "text/plain");
    res.end("Bonjour depuis Node.js");
});
server.listen(3000, () => {
    console.log("Serveur en cours d'exécution sur le port 3000");
});
```
