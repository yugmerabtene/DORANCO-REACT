# Support de cours complet : TypeScript


## Module 1 : Introduction à TypeScript

### 1.1 : Introduction à TypeScript
TypeScript est un langage de programmation développé par Microsoft. C'est un sur-ensemble typé de JavaScript qui améliore la maintenabilité du code et la détection des erreurs. Il se compile en JavaScript standard.

#### Exemple :
```typescript
function saluer(nom: string): string {
    return `Bonjour, ${nom}`;
}
console.log(saluer("Alice"));
```

---

### 1.2 : Installation et configuration

#### Installation :
1. **Installer TypeScript via npm :**
   ```bash
   npm install -g typescript
   ```
2. **Initialiser un projet TypeScript :**
   ```bash
   tsc --init
   ```
   Un fichier `tsconfig.json` sera créé pour configurer le compilateur.

#### Compilation :
```bash
tsc fichier.ts
```

---

### 1.3 : Variables et types de données

- **Types primitifs :** `string`, `number`, `boolean`, `null`, `undefined`
- **Tableaux :**
  ```typescript
  let nombres: number[] = [1, 2, 3];
  ```
- **Tuples :**
  ```typescript
  let tuple: [string, number] = ["Alice", 25];
  ```
- **Enums :**
  ```typescript
  enum Couleur {
      Rouge,
      Vert,
      Bleu
  }
  let maCouleur: Couleur = Couleur.Rouge;
  ```
- **Types particuliers :** `any`, `unknown`, `never`, `void`

#### Exemple d’utilisation :
```typescript
let variable: any = 42;
let inconnu: unknown = "Texte";
```

#### Exercices :
1. Déclarer une variable `prenom` de type `string` et l’afficher dans la console.
2. Créez un tableau de nombres, calculez la somme de ses éléments.

**Solution :**
```typescript
const prenom: string = "Jean";
console.log(prenom);

const nombres: number[] = [10, 20, 30];
const somme = nombres.reduce((a, b) => a + b, 0);
console.log(somme);
```

---

### 1.4 : Fonctions et typage

#### Typage des paramètres et des retours :
```typescript
function addition(a: number, b: number): number {
    return a + b;
}
```

#### Paramètres optionnels :
```typescript
function salutation(nom: string, titre?: string): string {
    return titre ? `${titre} ${nom}` : nom;
}
```

#### Exercices :
1. Écrire une fonction `multiplication` qui prend deux nombres en paramètres et retourne leur produit.
2. Ajouter un paramètre optionnel à la fonction pour afficher le résultat dans la console.

**Solution :**
```typescript
function multiplication(a: number, b: number, afficher?: boolean): number {
    const resultat = a * b;
    if (afficher) {
        console.log(resultat);
    }
    return resultat;
}
multiplication(3, 5, true);
```

---

## Module 2 : Concepts avancés

### Interfaces
Les interfaces définissent la structure des objets.
```typescript
interface Utilisateur {
    nom: string;
    age: number;
    email?: string;
}
const utilisateur: Utilisateur = {
    nom: "Alice",
    age: 30
};
```

#### Exercices :
1. Créez une interface `Vehicule` avec les propriétés `marque` et `modele`, et implémentez-la dans une classe `Voiture`.

**Solution :**
```typescript
interface Vehicule {
    marque: string;
    modele: string;
}
class Voiture implements Vehicule {
    constructor(public marque: string, public modele: string) {}
    afficher(): void {
        console.log(`${this.marque} ${this.modele}`);
    }
}
const maVoiture = new Voiture("Toyota", "Corolla");
maVoiture.afficher();
```

---

### Classes et héritage
TypeScript facilite la POO avec les classes.

#### Exemple :
```typescript
class Animal {
    constructor(public nom: string) {}
    parler(): void {
        console.log(`${this.nom} fait un bruit.`);
    }
}
class Chien extends Animal {
    parler(): void {
        console.log(`${this.nom} aboie.`);
    }
}
const rex = new Chien("Rex");
rex.parler();
```

#### Exercices :
1. Créez une classe `Personne` avec les propriétés `nom` et `age`, et une méthode `sePresenter`.
2. Héritez de cette classe pour créer une classe `Etudiant` avec une propriété supplémentaire `matiere`.

---
