# Introduction à React.js

React.js est une bibliothèque JavaScript open-source utilisée pour construire des interfaces utilisateur interactives et dynamiques. Elle est créée par Facebook et s'est rapidement imposée comme l'une des technologies les plus populaires pour le développement front-end. React permet de construire des applications web basées sur des composants, favorisant la réutilisabilité et la modularité du code.

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

### Utilisation d'un composant

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

