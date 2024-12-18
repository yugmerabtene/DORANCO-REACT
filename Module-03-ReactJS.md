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

## Étape 3 : Ajouter du CSS dans React

React permet d'ajouter du CSS de différentes manières pour styliser les composants. Voici les options les plus courantes :

### 1. CSS global

Ajoutez un fichier CSS global dans votre projet et importez-le dans `index.js` ou `App.js`.

#### Exemple

Créez un fichier `styles.css` dans le dossier `src` :

```css
body {
  font-family: Arial, sans-serif;
  margin: 0;
  padding: 0;
}

h1 {
  color: blue;
}
```

Importez ce fichier dans `index.js` :

```javascript
import './styles.css';
```

### 2. CSS spécifique à un composant

Créez un fichier CSS spécifique pour chaque composant et importez-le dans ce composant.

#### Exemple

Créez un fichier `Bonjour.css` :

```css
.titre {
  font-size: 24px;
  color: green;
}
```

Mettez à jour le composant `Bonjour.js` :

```javascript
import React from 'react';
import './Bonjour.css';

function Bonjour(props) {
  return <h1 className="titre">Bonjour, {props.nom}!</h1>;
}

export default Bonjour;
```

### 3. CSS inline

Ajoutez du CSS directement dans le JSX sous forme d'objet.

#### Exemple

```javascript
function BonjourInline(props) {
  const style = {
    fontSize: '24px',
    color: 'red'
  };

  return <h1 style={style}>Bonjour, {props.nom}!</h1>;
}

export default BonjourInline;
```

### 4. CSS Modules

CSS Modules permettent de scoper les styles localement à un composant.

#### Exemple

Créez un fichier `Bonjour.module.css` :

```css
.titre {
  font-size: 24px;
  color: purple;
}
```

Mettez à jour le composant `Bonjour.js` :

```javascript
import React from 'react';
import styles from './Bonjour.module.css';

function Bonjour(props) {
  return <h1 className={styles.titre}>Bonjour, {props.nom}!</h1>;
}

export default Bonjour;
```

### 5. Frameworks CSS

Vous pouvez également utiliser des frameworks CSS comme Bootstrap ou Tailwind CSS en les installant via npm et en les intégrant dans votre projet.

#### Exemple avec Bootstrap

1. Installez Bootstrap :

   ```bash
   npm install bootstrap
   ```

2. Importez-le dans `index.js` :

   ```javascript
   import 'bootstrap/dist/css/bootstrap.min.css';
   ```

3. Utilisez les classes Bootstrap dans vos composants :

   ```javascript
   function Button() {
     return <button className="btn btn-primary">Cliquez-moi</button>;
   }

   export default Button;
   ```

Lorsque vous créez un projet React, voici les principaux dossiers et fichiers :

- **`src/`** : Contient le code source de l'application.
  - `App.js` : Composant principal de l'application.
  - `index.js` : Point d'entrée principal de l'application.
- **`public/`** : Contient les fichiers statiques accessibles directement par le navigateur (comme `index.html`).
- **`package.json`** : Fichier de configuration pour npm.

## Étape 3 : Composants React

Un composant est une fonction ou une classe qui retourne un morceau d'interface utilisateur (du JSX).

### Composant fonctionnel

Un composant fonctionnel est une simple fonction JavaScript qui accepte des `props` comme paramètre et retourne du JSX. Les composants fonctionnels sont légers, faciles à lire, et sont souvent privilégiés pour des composants simples.

#### Exemple d'un composant fonctionnel

```javascript
function Bonjour(props) {
  return <h1>Bonjour, {props.nom}!</h1>;
}

export default Bonjour;
```

### Composant de classe

Un composant de classe hérite de `React.Component`. Il est plus puissant qu'un composant fonctionnel, car il peut gérer l'état local avec `this.state` et accéder à des méthodes du cycle de vie du composant. De plus, les composants de classe utilisent les **props**, qui sont des paramètres passés au composant pour personnaliser son comportement ou son affichage.

#### Exemple d'un composant de classe

```javascript
import React, { Component } from 'react';

class BonjourClasse extends Component {
  render() {
    return (
      <div>
        <h1>Bonjour, {this.props.nom}!</h1>
        <p>Vous avez {this.props.age} ans.</p>
      </div>
    );
  }
}

export default BonjourClasse;
```

#### Utilisation d'un composant de classe avec des props

Pour utiliser ce composant dans `App.js` :

```javascript
import React from 'react';
import BonjourClasse from './BonjourClasse';

function App() {
  return (
    <div>
      <BonjourClasse nom="Alice" age={25} />
      <BonjourClasse nom="Bob" age={30} />
    </div>
  );
}

export default App;
```

#### Concepts clés sur les props

- **Immutables** : Les props ne peuvent pas être modifiées par le composant qui les reçoit.
- **Transmission des données** : Les props permettent de transmettre des données d'un composant parent à un composant enfant.
- **Déstructuration** : Pour simplifier le code, vous pouvez déstructurer les props :

```javascript
class BonjourClasse extends Component {
  render() {
    const { nom, age } = this.props;
    return (
      <div>
        <h1>Bonjour, {nom}!</h1>
        <p>Vous avez {age} ans.</p>
      </div>
    );
  }
}
```

### Comparaison avec un composant fonctionnel utilisant les props

Un composant fonctionnel gère les props de manière similaire, mais avec une syntaxe plus concise.

#### Exemple d'un composant fonctionnel

```javascript
function Bonjour(props) {
  return (
    <div>
      <h1>Bonjour, {props.nom}!</h1>
      <p>Vous avez {props.age} ans.</p>
    </div>
  );
}

export default Bonjour;
```

#### Utilisation

```javascript
import React from 'react';
import Bonjour from './Bonjour';

function App() {
  return (
    <div>
      <Bonjour nom="Charlie" age={35} />
    </div>
  );
}

export default App;
```

### Différences entre composant fonctionnel et composant de classe pour les props

| Aspect                  | Composant fonctionnel                  | Composant de classe                  |
|-------------------------|-----------------------------------------|--------------------------------------|
| **Gestion des props**   | Accès direct via `props` dans les arguments de la fonction | Accès via `this.props`               |
| **Simplicité**          | Plus concis                           | Moins concis                         |
| **Déstructuration**    | Possible dans les arguments            | Possible dans `this.props`           |

Les deux approches sont équivalentes pour gérer les props, mais les composants fonctionnels sont généralement préférés pour leur simplicité.

Un composant de classe hérite de `React.Component`. Il est plus puissant qu'un composant fonctionnel, car il peut gérer l'état local avec `this.state` et accéder à des méthodes du cycle de vie du composant.

#### Exemple d'un composant de classe

```javascript
import React, { Component } from 'react';

class BonjourClasse extends Component {
  render() {
    return <h1>Bonjour, {this.props.nom}!</h1>;
  }
}

export default BonjourClasse;
```

### Utilisation de CSS avec React

React prend en charge plusieurs manières d'utiliser du CSS pour styliser les composants. Voici quelques-unes des approches courantes :

#### 1. Ajouter un fichier CSS global

1. Créez un fichier CSS, par exemple `App.css`.

   ```css
   h1 {
     color: blue;
   }
   ```

2. Importez ce fichier dans votre composant :

   ```javascript
   import './App.css';

   function Bonjour(props) {
     return <h1>Bonjour, {props.nom}!</h1>;
   }

   export default Bonjour;
   ```

#### 2. Styles en ligne

Vous pouvez définir des styles directement dans le composant avec une syntaxe d'objet JavaScript :

```javascript
function Bonjour(props) {
  const style = {
    color: 'green',
    fontSize: '20px',
  };

  return <h1 style={style}>Bonjour, {props.nom}!</h1>;
}

export default Bonjour;
```

#### 3. Modules CSS

Les modules CSS permettent de scoper les styles à un composant spécifique.

1. Créez un fichier CSS module, par exemple `Bonjour.module.css` :

   ```css
   titre {
     color: red;
     text-align: center;
   }
   ```

2. Importez et appliquez les styles :

   ```javascript
   import styles from './Bonjour.module.css';

   function Bonjour(props) {
     return <h1 className={styles.titre}>Bonjour, {props.nom}!</h1>;
   }

   export default Bonjour;
   ```

#### 4. Styled-components

Styled-components est une bibliothèque pour gérer le CSS dans les fichiers JavaScript en utilisant les balises template literals.

1. Installez la bibliothèque :

   ```bash
   npm install styled-components
   ```

2. Utilisez-la dans un composant :

   ```javascript
   import styled from 'styled-components';

   const Titre = styled.h1`
     color: purple;
     font-size: 24px;
   `;

   function Bonjour(props) {
     return <Titre>Bonjour, {props.nom}!</Titre>;
   }

   export default Bonjour;
   ```

### Différences entre ces méthodes

| Méthode              | Portée des styles       | Facilité d'utilisation | Modularité |
|----------------------|-------------------------|-------------------------|------------|
| Fichier CSS global   | Globale                | Simple                 | Faible     |
| Styles en ligne      | Composant unique       | Simple                 | Moyenne    |
| Modules CSS          | Scopée par composant   | Moyennement simple     | Bonne      |
| Styled-components    | Scopée par composant   | Avancée                | Excellente |

Choisissez la méthode qui convient le mieux à votre projet en fonction de vos besoins en modularité et complexité.

Un composant est une fonction ou une classe qui retourne un morceau d'interface utilisateur (du JSX).

### Composant fonctionnel

Un composant fonctionnel est une simple fonction JavaScript qui accepte des `props` comme paramètre et retourne du JSX. Les composants fonctionnels sont légers, faciles à lire, et sont souvent privilégiés pour des composants simples.

#### Exemple d'un composant fonctionnel

```javascript
function Bonjour(props) {
  return <h1>Bonjour, {props.nom}!</h1>;
}

export default Bonjour;
```

### Composant de classe

Un composant de classe hérite de `React.Component`. Il est plus puissant qu'un composant fonctionnel, car il peut gérer l'état local avec `this.state` et accéder à des méthodes du cycle de vie du composant.

#### Exemple d'un composant de classe

```javascript
import React, { Component } from 'react';

class BonjourClasse extends Component {
  render() {
    return <h1>Bonjour, {this.props.nom}!</h1>;
  }
}

export default BonjourClasse;
```

### Différences entre composant fonctionnel et composant de classe

| Aspect                  | Composant fonctionnel                  | Composant de classe                  |
|-------------------------|-----------------------------------------|--------------------------------------|
| **Structure**           | Fonction JavaScript simple             | Classe ES6 qui hérite de `React.Component` |
| **Gestion de l'état**   | Utilise les hooks comme `useState`     | Utilise `this.state`                |
| **Cycle de vie**        | Nécessite des hooks comme `useEffect`  | Méthodes comme `componentDidMount` et `componentDidUpdate` |
| **Performance**         | Plus performant, car il est plus léger | Moins performant pour les petits composants |

### Quand utiliser quoi ?

- **Composants fonctionnels** : Lorsque le composant est simple et n'a pas besoin de gérer un état ou d'utiliser des méthodes du cycle de vie.
- **Composants de classe** : Lorsque des fonctionnalités avancées comme le cycle de vie ou un état complexe sont nécessaires.

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

L'état est une manière de gérer des données dynamiques dans un composant. Contrairement aux props, l'état peut être modifié par le composant lui-même, ce qui permet de rendre l'interface utilisateur interactive.

### Exemple avec `useState`

La fonction `useState` permet d'ajouter un état local dans un composant fonctionnel.

#### Exemple : Compteur simple

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

#### Exemple : Formulaire avec état local

```javascript
import React, { useState } from 'react';

function Formulaire() {
  const [nom, setNom] = useState('');

  const handleChange = (event) => {
    setNom(event.target.value);
  };

  const handleSubmit = (event) => {
    event.preventDefault();
    alert(`Bonjour, ${nom}!`);
  };

  return (
    <form onSubmit={handleSubmit}>
      <label>
        Nom :
        <input type="text" value={nom} onChange={handleChange} />
      </label>
      <button type="submit">Envoyer</button>
    </form>
  );
}

export default Formulaire;
```

### Exemple avec plusieurs états

Vous pouvez gérer plusieurs états en utilisant plusieurs appels à `useState`.

#### Exemple : Gestion de deux compteurs

```javascript
import React, { useState } from 'react';

function Compteurs() {
  const [compteur1, setCompteur1] = useState(0);
  const [compteur2, setCompteur2] = useState(0);

  return (
    <div>
      <div>
        <p>Compteur 1 : {compteur1}</p>
        <button onClick={() => setCompteur1(compteur1 + 1)}>Incrémenter Compteur 1</button>
      </div>
      <div>
        <p>Compteur 2 : {compteur2}</p>
        <button onClick={() => setCompteur2(compteur2 + 1)}>Incrémenter Compteur 2</button>
      </div>
    </div>
  );
}

export default Compteurs;
```

### Exemple avancé : Liste dynamique

#### Gestion d'une liste d'éléments

```javascript
import React, { useState } from 'react';

function Liste() {
  const [items, setItems] = useState([]);
  const [nouvelItem, setNouvelItem] = useState('');

  const ajouterItem = () => {
    setItems([...items, nouvelItem]);
    setNouvelItem('');
  };

  return (
    <div>
      <h2>Liste de courses</h2>
      <input
        type="text"
        value={nouvelItem}
        onChange={(e) => setNouvelItem(e.target.value)}
        placeholder="Ajouter un article"
      />
      <button onClick={ajouterItem}>Ajouter</button>
      <ul>
        {items.map((item, index) => (
          <li key={index}>{item}</li>
        ))}
      </ul>
    </div>
  );
}

export default Liste;
```

### Concepts clés sur l'état

1. **Initialisation** : `useState` accepte une valeur initiale pour l'état.
2. **Mise à jour** : Utilisez la fonction fournie par `useState` pour mettre à jour l'état.
3. **Composants contrôlés** : L'état peut être utilisé pour contrôler des formulaires et d'autres interactions utilisateur.

### Exercices

1. Créez un composant `TodoList` où l'utilisateur peut ajouter et supprimer des tâches.
2. Implémentez un système de votes avec deux boutons : "Like" et "Dislike" qui affichent le total des votes.
3. Ajoutez un champ de saisie pour filtrer les éléments d'une liste affichée à l'écran.

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

## Étape 7 : Création d'une application To-Do List

### Structure des dossiers du projet

Pour organiser votre projet, nous allons créer un dossier `components` dans le dossier `src` pour y placer tous les composants de l'application.

Voici la structure recommandée :

```
mon-app/
├── public/
├── src/
│   ├── components/
│   │   ├── TodoList.js
│   │   ├── TodoList.css
│   ├── App.js
│   ├── index.js
│   ├── index.css
├── package.json
```

- **`components/`** : Contiendra tous les composants réutilisables, comme `TodoList.js`.
- **`App.js`** : Le composant principal où les composants enfants seront intégrés.
- **`TodoList.css`** : Fichier pour styliser spécifiquement le composant `TodoList`.

### Étape 1 : Créer la To-Do List avec des classes

Nous allons maintenant créer une application de to-do list complète en utilisant des composants basés sur des classes. Cette application permettra à l'utilisateur d'ajouter, de supprimer et de marquer des tâches comme terminées.

Nous allons maintenant créer une application de to-do list complète en utilisant des composants basés sur des classes. Cette application permettra à l'utilisateur d'ajouter, de supprimer et de marquer des tâches comme terminées.

### Étape 1 : Structure du projet

Assurez-vous d'avoir un projet React déjà configuré (voir les étapes précédentes pour créer un projet React).

Créez un fichier `TodoList.js` dans le dossier `src`.

### Étape 2 : Code complet de l'application avec classes

```javascript
import React, { Component } from 'react';
import './TodoList.css';

class TodoList extends Component {
  constructor(props) {
    super(props);
    this.state = {
      tasks: [],
      taskInput: ''
    };
  }

  handleInputChange = (event) => {
    this.setState({ taskInput: event.target.value });
  };

  addTask = () => {
    const { taskInput, tasks } = this.state;
    if (taskInput.trim() === '') return;
    this.setState({
      tasks: [...tasks, { text: taskInput, completed: false }],
      taskInput: ''
    });
  };

  toggleTask = (index) => {
    const newTasks = this.state.tasks.map((task, i) => {
      if (i === index) {
        return { ...task, completed: !task.completed };
      }
      return task;
    });
    this.setState({ tasks: newTasks });
  };

  deleteTask = (index) => {
    const newTasks = this.state.tasks.filter((_, i) => i !== index);
    this.setState({ tasks: newTasks });
  };

  render() {
    const { tasks, taskInput } = this.state;

    return (
      <div className="todo-list">
        <h1>To-Do List</h1>
        <div className="input-container">
          <input
            type="text"
            value={taskInput}
            onChange={this.handleInputChange}
            placeholder="Ajouter une tâche..."
          />
          <button onClick={this.addTask}>Ajouter</button>
        </div>
        <ul>
          {tasks.map((task, index) => (
            <li key={index} className={task.completed ? 'completed' : ''}>
              <span onClick={() => this.toggleTask(index)}>{task.text}</span>
              <button onClick={() => this.deleteTask(index)}>Supprimer</button>
            </li>
          ))}
        </ul>
      </div>
    );
  }
}

export default TodoList;
```

### Étape 3 : Style CSS

Créez un fichier `TodoList.css` pour styliser l'application.

```css
.todo-list {
  font-family: Arial, sans-serif;
  max-width: 400px;
  margin: 0 auto;
  padding: 20px;
  border: 1px solid #ddd;
  border-radius: 5px;
}

h1 {
  text-align: center;
}

.input-container {
  display: flex;
  margin-bottom: 20px;
}

input {
  flex: 1;
  padding: 10px;
  border: 1px solid #ddd;
  border-radius: 5px;
  margin-right: 10px;
}

button {
  padding: 10px 20px;
  background-color: #007bff;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

button:hover {
  background-color: #0056b3;
}

ul {
  list-style: none;
  padding: 0;
}

li {
  display: flex;
  justify-content: space-between;
  padding: 10px;
  border: 1px solid #ddd;
  border-radius: 5px;
  margin-bottom: 10px;
}

li.completed span {
  text-decoration: line-through;
  color: gray;
}

li span {
  cursor: pointer;
}
```

### Étape 4 : Intégration dans `App.js`

Mettez à jour votre fichier `App.js` pour inclure le composant `TodoList`.

```javascript
import React from 'react';
import TodoList from './TodoList';

function App() {
  return (
    <div>
      <TodoList />
    </div>
  );
}

export default App;
```

### Fonctionnalités de l'application

1. **Ajouter une tâche** : L'utilisateur peut saisir du texte dans le champ d'entrée et cliquer sur "Ajouter" pour ajouter une nouvelle tâche.
2. **Marquer comme terminée** : En cliquant sur une tâche, elle est marquée comme terminée (ou réactivée).
3. **Supprimer une tâche** : Un bouton "Supprimer" est disponible pour chaque tâche.

### Exercices

1. Ajoutez une fonctionnalité pour modifier une tâche existante.
2. Implémentez une option pour supprimer toutes les tâches terminées.
3. Ajoutez un compteur affichant le nombre de tâches restantes.

Nous allons maintenant créer une application de to-do list complète. Cette application permettra à l'utilisateur d'ajouter, de supprimer et de marquer des tâches comme terminées.

### Étape 1 : Structure du projet

Assurez-vous d'avoir un projet React déjà configuré (voir les étapes précédentes pour créer un projet React).

Créez un fichier `TodoList.js` dans le dossier `src`.

### Étape 2 : Code complet de l'application

```javascript
import React, { useState } from 'react';
import './TodoList.css';

function TodoList() {
  const [tasks, setTasks] = useState([]);
  const [taskInput, setTaskInput] = useState('');

  const addTask = () => {
    if (taskInput.trim() === '') return;
    setTasks([...tasks, { text: taskInput, completed: false }]);
    setTaskInput('');
  };

  const toggleTask = (index) => {
    const newTasks = tasks.map((task, i) => {
      if (i === index) {
        return { ...task, completed: !task.completed };
      }
      return task;
    });
    setTasks(newTasks);
  };

  const deleteTask = (index) => {
    const newTasks = tasks.filter((_, i) => i !== index);
    setTasks(newTasks);
  };

  return (
    <div className="todo-list">
      <h1>To-Do List</h1>
      <div className="input-container">
        <input
          type="text"
          value={taskInput}
          onChange={(e) => setTaskInput(e.target.value)}
          placeholder="Ajouter une tâche..."
        />
        <button onClick={addTask}>Ajouter</button>
      </div>
      <ul>
        {tasks.map((task, index) => (
          <li key={index} className={task.completed ? 'completed' : ''}>
            <span onClick={() => toggleTask(index)}>{task.text}</span>
            <button onClick={() => deleteTask(index)}>Supprimer</button>
          </li>
        ))}
      </ul>
    </div>
  );
}

export default TodoList;
```

### Étape 3 : Style CSS

Créez un fichier `TodoList.css` pour styliser l'application.

```css
.todo-list {
  font-family: Arial, sans-serif;
  max-width: 400px;
  margin: 0 auto;
  padding: 20px;
  border: 1px solid #ddd;
  border-radius: 5px;
}

h1 {
  text-align: center;
}

.input-container {
  display: flex;
  margin-bottom: 20px;
}

input {
  flex: 1;
  padding: 10px;
  border: 1px solid #ddd;
  border-radius: 5px;
  margin-right: 10px;
}

button {
  padding: 10px 20px;
  background-color: #007bff;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

button:hover {
  background-color: #0056b3;
}

ul {
  list-style: none;
  padding: 0;
}

li {
  display: flex;
  justify-content: space-between;
  padding: 10px;
  border: 1px solid #ddd;
  border-radius: 5px;
  margin-bottom: 10px;
}

li.completed span {
  text-decoration: line-through;
  color: gray;
}

li span {
  cursor: pointer;
}
```

### Étape 4 : Intégration dans `App.js`

Mettez à jour votre fichier `App.js` pour inclure le composant `TodoList`.

```javascript
import React from 'react';
import TodoList from './TodoList';

function App() {
  return (
    <div>
      <TodoList />
    </div>
  );
}

export default App;
```

### Fonctionnalités de l'application

1. **Ajouter une tâche** : L'utilisateur peut saisir du texte dans le champ d'entrée et cliquer sur "Ajouter" pour ajouter une nouvelle tâche.
2. **Marquer comme terminée** : En cliquant sur une tâche, elle est marquée comme terminée (ou réactivée).
3. **Supprimer une tâche** : Un bouton "Supprimer" est disponible pour chaque tâche.

### Exercices

1. Ajoutez une fonctionnalité pour modifier une tâche existante.
2. Implémentez une option pour supprimer toutes les tâches terminées.
3. Ajoutez un compteur affichant le nombre de tâches restantes.

## Conclusion

React est une bibliothèque puissante qui permet de créer des applications web modernes. En suivant ces étapes, vous avez appris les bases de React : composants, état, gestion des événements, et interaction avec des APIs. Vous avez également construit une application complète de to-do list, illustrant l'utilisation pratique des concepts React. Pour aller plus loin, explorez des concepts avancés comme les hooks personnalisés, le routing avec React Router, et la gestion de l'état global avec Redux.

React est une bibliothèque puissante qui permet de créer des applications web modernes. En suivant ces étapes, vous avez appris les bases de React : composants, état, gestion des événements, et interaction avec des APIs. Pour aller plus loin, explorez des concepts avancés comme les hooks personnalisés, le routing avec React Router, et la gestion de l'état global avec Redux.

