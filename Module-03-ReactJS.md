# Introduction à React.js

React.js est une bibliothèque JavaScript open-source utilisée pour construire des interfaces utilisateur interactives et dynamiques. Elle est créée par Facebook et s'est rapidement imposée comme l'une des technologies les plus populaires pour le développement front-end. React permet de construire des applications web basées sur des composants, favorisant la réutilisabilité et la modularité du code.

## Une brève histoire de React

React a été initialement développé par Jordan Walke, un ingénieur de Facebook, en 2011. L'objectif principal était de simplifier la gestion des interfaces utilisateur complexes en utilisant un système basé sur des composants. React a été introduit au public en 2013 lors de la conférence JSConf US. Depuis lors, React a été largement adopté et est devenu une technologie essentielle pour le développement d'applications modernes.

Facebook utilise React dans ses produits comme Facebook, Instagram et WhatsApp, ce qui a contribué à sa popularité et à son écosystème en constante expansion.

## Prérequis

Avant de commencer avec React, assurez-vous d'avoir des connaissances de base en :

- HTML
- CSS
- JavaScript (ES6+)

Assurez-vous également d'avoir Node.js installé sur votre machine.

## Étape 1 : Créer un projet React

### Installation de Node.js

1. Rendez-vous sur le site officiel de Node.js : [https://nodejs.org](https://nodejs.org).
2. Téléchargez et installez la version LTS (Long Term Support).
3. Pour vérifier l'installation, exécutez les commandes suivantes dans un terminal :
   ```bash
   node -v   # Affiche la version de Node.js
   npm -v    # Affiche la version de npm
   ```

### Créer une application React avec Create React App

1. Ouvrez un terminal.

2. Exécutez la commande suivante pour créer une nouvelle application React :

   ```bash
   npx create-react-app mon-app
   ```

3. Une fois l'installation terminée, accédez au répertoire du projet :

   ```bash
   cd mon-app
   ```

4. Lancez le serveur de développement :

   ```bash
   npm start
   ```

Votre application sera accessible à l'adresse [http://localhost:3000](http://localhost:3000).

### Installer le plugin de débogage React

Pour faciliter le développement, installez l'extension React Developer Tools dans votre navigateur :

- **Chrome** : Rendez-vous sur le [Chrome Web Store](https://chrome.google.com/webstore/detail/react-developer-tools/fmkadmapgofadopljbjfkapdkoienihi) et ajoutez l'extension.
- **Firefox** : Installez l'extension depuis le [site des modules Firefox](https://addons.mozilla.org/fr/firefox/addon/react-devtools/).

Cette extension permet d'inspecter les composants React et leur état directement dans les outils de développement du navigateur.

## Étape 2 : Comprendre la structure d'un projet React

Lorsque vous créez un projet React, voici les principaux dossiers et fichiers :

- **`src/`** : Contient le code source de l'application.
  - `App.js` : Composant principal de l'application.
  - `index.js` : Point d'entrée principal de l'application.
- **`public/`** : Contient les fichiers statiques accessibles directement par le navigateur (comme `index.html`).
- **`package.json`** : Fichier de configuration pour npm.

## Étape 3 : Composants React

Un composant est une fonction ou une classe qui retourne un morceau d'interface utilisateur (du JSX).

### Exemple d'un composant fonctionnel

```javascript
function Bonjour(props) {
  return <h1>Bonjour, {props.nom}!</h1>;
}

export default Bonjour;
```

### Exemple d'un composant de classe

Un composant de classe hérite de `React.Component` et doit avoir une méthode `render` qui retourne du JSX :

```javascript
import React, { Component } from 'react';

class BonjourClasse extends Component {
  render() {
    return <h1>Bonjour, {this.props.nom}!</h1>;
  }
}

export default BonjourClasse;
```

### Utilisation d'un composant

Pour utiliser ces composants dans `App.js` :

```javascript
import React from 'react';
import Bonjour from './Bonjour';
import BonjourClasse from './BonjourClasse';

function App() {
  return (
    <div>
      <Bonjour nom="Alice" />
      <BonjourClasse nom="Bob" />
    </div>
  );
}

export default App;
```

### Résultat attendu
Vous verrez :

```
Bonjour, Alice!
Bonjour, Bob!
```

```javascript
function Bonjour(props) {
  return <h1>Bonjour, {props.nom}!</h1>;
}

export default Bonjour;
```

### Utilisation d'un composant

Pour utiliser un composant dans React :

1. **Importer le composant** : Dans le fichier où vous souhaitez l'utiliser, importez le composant avec `import`.
2. **Ajouter le composant dans le JSX** : Utilisez le nom du composant comme une balise HTML.

Voici un exemple complet :

#### Composant `Bonjour`

Créez un fichier `Bonjour.js` :

```javascript
function Bonjour(props) {
  return <h1>Bonjour, {props.nom}!</h1>;
}

export default Bonjour;
```

#### Utilisation dans `App.js`

Ajoutez ce composant dans le fichier `App.js` :

```javascript
import React from 'react';
import Bonjour from './Bonjour';

function App() {
  return (
    <div>
      <Bonjour nom="Alice" />
      <Bonjour nom="Bob" />
      <Bonjour nom="Charlie" />
    </div>
  );
}

export default App;
```

#### Résultat attendu
Lorsque vous exécutez l'application, vous verrez :

```
Bonjour, Alice!
Bonjour, Bob!
Bonjour, Charlie!
```

Dans `App.js`, importez et utilisez le composant :

```javascript
import React from 'react';
import Bonjour from './Bonjour';

function App() {
  return (
    <div>
      <Bonjour nom="Youghourta" />
    </div>
  );
}

export default App;
```

### Exercices

1. Créez un composant `Bienvenue` qui accepte une propriété `nom` et affiche un message d'accueil.
2. Ajoutez plusieurs instances de `Bienvenue` dans `App.js` avec différents noms.

## Étape 4 : État (« State ») dans les composants

L'état est une manière de gérer des données dynamiques dans un composant.

### Exemple avec `useState`

```javascript
import React, { useState } from 'react';

function Compteur() {
  const [compte, setCompte] = useState(0);

  return (
    <div>
      <p>Vous avez cliqué {compte} fois.</p>
      <button onClick={() => setCompte(compte + 1)}>
        Cliquez-moi
      </button>
    </div>
  );
}

export default Compteur;
```

### Exercices

1. Créez un composant `CompteurDouble` qui affiche deux compteurs indépendants.
2. Ajoutez un bouton pour réinitialiser chaque compteur à zéro.

## Étape 5 : Gestion des événements

React gère les événements de manière similaire à JavaScript, mais utilise une syntaxe camelCase.

### Exemple

```javascript
function Clique() {
  function handleClick() {
    alert('Bouton cliqué !');
  }

  return <button onClick={handleClick}>Cliquez ici</button>;
}

export default Clique;
```

### Exercices

1. Créez un formulaire simple avec un champ de texte et un bouton. Affichez une alerte contenant le texte saisi lors du clic sur le bouton.
2. Ajoutez une validation pour empêcher l'envoi si le champ est vide.

## Étape 6 : Requêtes HTTP avec `fetch`

React ne fournit pas de méthode intégrée pour faire des requêtes HTTP, mais vous pouvez utiliser `fetch` ou des bibliothèques comme Axios.

### Exemple avec `fetch`

```javascript
import React, { useState, useEffect } from 'react';

function Utilisateurs() {
  const [utilisateurs, setUtilisateurs] = useState([]);

  useEffect(() => {
    fetch('https://jsonplaceholder.typicode.com/users')
      .then((response) => response.json())
      .then((data) => setUtilisateurs(data));
  }, []);

  return (
    <div>
      <h1>Liste des utilisateurs</h1>
      <ul>
        {utilisateurs.map((user) => (
          <li key={user.id}>{user.name}</li>
        ))}
      </ul>
    </div>
  );
}

export default Utilisateurs;
```

### Exercices

1. Créez un composant `Articles` qui affiche une liste d'articles depuis une API.
2. Ajoutez une fonction de recherche pour filtrer les articles par titre.

## Conclusion

React est une bibliothèque puissante qui permet de créer des applications web modernes. En suivant ces étapes, vous avez appris les bases de React : composants, état, gestion des événements, et interaction avec des APIs. Pour aller plus loin, explorez des concepts avancés comme les hooks personnalisés, le routing avec React Router, et la gestion de l'état global avec Redux.

