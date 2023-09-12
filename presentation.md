
## Monorepo 
#### Un seul repo pour les gouverner tous 

---

### 👋 Maximilien Gilet
Développeur frontend
[@Alltech](https://www.alltechconsulting.fr)

![profile picture](https://avatars.githubusercontent.com/u/10434870?v=4) <!-- .element: class="r-profile-picture" -->

---

## Bienvenue chez 
## TurboCorp <!-- .element: class="r-colored" -->

--

## Chez TurboCorp, nous avons **beaucoup** de projets frontend

--

- Un site vitrine
- Une application SaaS <!-- .element: class="fragment" -->
- Une application mobile React Native <!-- .element: class="fragment" -->
- Un site de documentation <!-- .element: class="fragment" -->
- Des composants partagés <!-- .element: class="fragment" -->

---

## Bref, c'est le __bor***__ 🤯

Copier-coller, dépendances multiples, versions incohérentes...

Note: Imaginez-vous en train de travailler sur plusieurs projets à la fois. Copier-coller, dépendances multiples, versions incohérentes. C'est un vrai casse-tête !

--

### L'enfer des dépendances 💀

On a essayé de faire les choses bien, pourtant...

- Chaque projet a ses propres dépendances
- On doit s'y retrouver dans les composants partagés
- On doit gérer un registre des composants

Note: Nous sommes confrontés à l'enfer des dépendances. Avec plusieurs projets frontend, il est inévitable que nous ayons différentes versions de bibliothèques et de packages dans chaque projet. Cela crée des conflits et des incompatibilités qui nous font perdre un temps précieux à les résoudre.

--

### Perdus dans les versions 😵‍💫

On a beau faire attention, pourtant...

- On utilise des versions différentes d'une même bibliothèque
- On doit constamment vérifier les versions
- On doit faire un tag à chaque modification de dépendance interne

Note: Et comme si cela ne suffisait pas, nous sommes souvent perdus dans les versions. Il est fréquent que nous utilisions des versions différentes d'une même bibliothèque dans différents projets, ce qui crée une confusion énorme. Nous devons constamment vérifier les versions, ce qui augmente le risque d'erreurs et d'incohérences dans notre code.

-- 

![les problèmes](/assets/problemes.jpg)

Note: En résumé, en tant que développeurs frontend, nous sommes confrontés à des défis de gestion des ressources au sein de notre entreprise. Le copier-coller fastidieux de code, l'enfer des dépendances et les versions inconsistences entravent notre productivité et augmentent les risques d'erreurs.

---

## Le fonctionnement actuel

--

![Schéma présentant l'architecture de plusieurs repositories avec des dépendances](/assets/polyrepo-practice.svg) <!-- .element: width="80%" -->

--

### Permet une
### ✨ **Autonomie des équipes** ✨

- Choix des librairies 
- Gestion du déploiement 
- Travail asynchrone

--

### Super, mais...

- Difficile de partager le code
- Des duplications
- Complexité de partage des dépendances
- Un outillage et des pratiques non homogènes

--

> ✨ Seul on va plus vite, ensemble on va plus loin ✨

---

## Et si on mettait tout au même endroit ? 🤔

--

![polyrepo](/assets/polyrepo.png) <!-- .element: width="100%" -->

-- 

![monorepo](/assets/monorepo.png) <!-- .element: width="100%" -->

--

## Juste colocs ? Bien plus que ça 😏

-- 

![monolith - modular](/assets/monolith-modular.svg) <!-- .element: width="100%" -->


---

## Ça apporte quoi ?

--

### Des changements atomiques

- Tout est testé en même temps
- Fini les breaking changes qui cassent tout

![Changements atomiques](/assets/atomic-change.gif) <!-- .element: width="40%" -->

--

### Une seule version: la dernière

- Pas d'incompatibilités internes
- Une image de votre code à un instant T

![Snapshot](/assets/snapshot.gif) <!-- .element: width="40%" -->
--

### Un nouveau projet ? Trop facile !

- Pas de configuration à faire
- CI/CD déjà en place

![Done](/assets/done.gif) <!-- .element: width="40%" -->
--

### Une collaboration facilitée

- Cohérence des outils
- Partage de code facilité
- Plus de repo caché à trouver

![Handshake](/assets/handshake.gif) <!-- .element: width="40%" -->

---

Le problème dans tout ça ?

## C'est leeeeent 🐢 <!-- .element: class="fragment" -->

--

![Délais importants de build](/assets/local-caching.webp) <!-- .element: width="100%" -->

--

````
yarn workspaces run lint
yarn workspaces run test
yarn workspaces run build
````

![Tâches exécutées de manière séquentielles](/assets/tasks-queue.webp) <!-- .element: width="100%" -->

---

## Comment y remédier ?

Exemple avec <!-- .element: class="fragment" -->

![Logo Turborepo](/assets/turborepo.png) <!-- .element: width="40%" class="fragment" -->

--

- Builds incrémentaux
- Exécution parallèle
- Partage du cache
- Pipelines de tâches
- Génération de packages

![Ça fait beaucoup de features](/assets/features.gif) 

-- 

![Délais importants de build](/assets/local-caching.webp) <!-- .element: width="80%" -->

![Build avec cache](/assets/why-turborepo-solution.webp) <!-- .element: width="80%" -->

--

![Exécution parallèle](/assets/turborepo-parallel.webp)

--

### Comment migrer ?

```text
web (repo 1)
├─ package.json
docs (repo 2)
├─ package.json
app (repo 3)
├─ package.json
```

```text
my-monorepo
├─ apps
│  ├─ app
│  │  └─ package.json
│  ├─ docs
│  │  └─ package.json
│  └─ web
│     └─ package.json
└─ package.json
```

--

```diff
  my-monorepo
  ├─ apps
  │  ├─ app
  │  │  └─ package.json
  │  ├─ docs
  │  │  └─ package.json
  │  └─ web
  │     └─ package.json
+ ├─ packages
+ │  └─ shared
+ │     └─ package.json
  └─ package.json
```

--


`/package.json`
```json
"scripts": {
  "build": "turbo build",
  "dev": "turbo dev --no-cache --continue",
  "lint": "turbo lint",
  "clean": "turbo clean && rm -rf node_modules",
  "format": "prettier --write \"**/*.{ts,tsx,md}\"",
  "changeset": "changeset",
  "version-packages": "changeset version",
  "release": "turbo build --filter=docs^... && changeset publish"
},
```

Note: On peut voir ici que les scripts sont très simples. Turbo s'occupe de tout et permet une adoption incrémentale en passant les packages ne définissant pas de script.

--

## Pipeline

```json
"pipeline": {
  "build": {
    // A workspace's `build` task depends on that workspace's
    // topological dependencies' and devDependencies'
    // `build` tasks  being completed first. The `^` symbol
    // indicates an upstream dependency.
    "dependsOn": ["^build"],
    "outputs": [".next/**", "!.next/cache/**", ".svelte-kit/**"]
  },
  "deploy": {
      // A workspace's `deploy` task depends on the `build`,
      // `test`, and `lint` tasks of the same workspace
      // being completed.
      "dependsOn": ["build", "test", "lint"]
  },
  "test": {
    // A workspace's `test` task depends on that workspace's
    // own `build` task being completed first.
    "dependsOn": ["build"],
    // A workspace's `test` task should only be rerun when
    // either a `.tsx` or `.ts` file has changed.
    "inputs": ["src/**/*.tsx", "src/**/*.ts", "test/**/*.ts", "test/**/*.tsx"]
  },
  // A workspace's `lint` task has no dependencies and
  // can be run whenever.
  "lint": {},
  "dev": {
    "cache": false,
    "persistent": true
  }
}
```

---

### Je dois faire un breaking change, comment je fais ?

-- 

![It's not a bug, it's a feature](/assets/bug-feature.jpg)

Note: Le fait de devoir gérer tous les breaking changes en même temps peut être un frein à l'adoption de cette solution, cependant 

-- 

### 3 approches possibles

- 😰 Faire des PR énormes
- 😵 Revenir à une gestion de versions <!-- .element: class="fragment" -->
- 😎 Utiliser les dépréciations <!-- .element: class="fragment" -->

--

```javascript
/**
 * A magic method that multiples digits.
 *
 * @deprecated [#1] since version 2.3 [#2].
 * [#3] Will be deleted in version 3.0.
 
 * [#4] In case you need similar behavior, implement it on you own,
 * preferably in vanilla JavaScript
 * or use the multiplyTheSameNumber method instead,
 * if the same number needs to be multiplied multiple times, like so:
 * multiplyDigits([5, 5, 5]) === multiplyTheSameNumber(5, 3)
 *
 * @param {array} _digits - digits to multiply
 */
function multiplyDigits(_digits) {
  console.warn("Calling a depricated method!"); // [#5]
  
  // ....
}
```

-- 

```javascript
/**
 * Creating a deprecated / obsolete behavior for methods in a library.
 * [Credits]{@link: https://stackoverflow.com/q/21726472/1333836}
 * 
 * @param  {function} replacementFunction
 * @param  {string} oldFnName
 * @param  {string} newFnName
 * @return {function}
 */
const Oboslete = function(replacementFunction, oldFnName, newFnName) {
    const wrapper = function() {
       console.warn("WARNING! Obsolete function called. Function '" + oldFnName + "' has been deprecated, please use the new '" + newFnName + "' function instead!");

        replacementFunction.apply(this, arguments);
    }
    wrapper.prototype = replacementFunction.prototype;

    return wrapper;
}
```

---

## Pourquoi ne pas utiliser un monorepo

![J'ai pas envie](/assets/pas-envie.gif) 

--

- Beaucoup de bruit dans les PR
- Culture de développement à mettre en place
- Pas adapté aux trop grosses organisations
- Énorme tentation du couplage fort

---

## Un entre-deux : plusieurs monorepos

-- 

- Allier les avantages
- Réduire les inconvénients

--

## Découpages possibles

- Par domaine métier
- Par technologie

---

# Conclusion

À retenir :

- Unifier la technique
- Régler les problèmes de librairies internes
- Pas une solution miracle

---

## Sources

- https://monorepo.tools/
- https://opensource.google/documentation/reference/thirdparty/oneversion
- https://turbo.build/repo