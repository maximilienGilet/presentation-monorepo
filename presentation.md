
## Turborepo 
#### Mettez le turbo dans votre monorepo

![turbo](/assets/turbo.png) <!-- .element: width="200" -->


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

> Seul on va plus vite, ensemble on va plus loin ✨

---

## Et si on mettait tout au même endroit ? 🤔

--

![polyrepo](/assets/polyrepo.png) <!-- .element: width="100%" -->

-- 

![monorepo](/assets/monorepo.png) <!-- .element: width="100%" -->

--

## Justes colocs ? Bien plus que ça 😏

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

## Et dans la pratique ?

Turborepo

---

## Comment bien structurer son Monorepo

Lors de la création de notre Monorepo, il est essentiel de définir une structure claire et cohérente. Nous pouvons organiser nos projets en fonction des domaines fonctionnels, des équipes ou des fonctionnalités communes. Une structure bien pensée facilite la navigation et la collaboration entre les développeurs.

---

## Comment gérer les mises à jour et les conflits de code

Avec TurboRepo, nous disposons d'outils puissants pour gérer les mises à jour et les conflits de code. Il est essentiel de définir des processus clairs pour la validation et la fusion des modifications. Nous pouvons également tirer parti des fonctionnalités de TurboRepo pour détecter automatiquement les conflits et les résoudre de manière efficace.

---

## Comment optimiser la performance et la collaboration entre les équipes

Pour optimiser la performance de notre Monorepo, nous pouvons mettre en place des mécanismes de mise en cache. TurboRepo nous permet de configurer un cache partagé, ce qui améliore la vitesse de construction et de développement. De plus, nous devons encourager une collaboration étroite entre les équipes pour partager les bonnes pratiques et les connaissances.

---

## Setup d'un nouvel environnement de développement avec un cache partagé

Lorsqu'un nouveau développeur rejoint notre équipe, nous pouvons configurer un nouvel environnement de développement avec un cache partagé. Cela lui permettra de démarrer rapidement en utilisant les ressources déjà disponibles dans le Monorepo. Nous pouvons également fournir des directives claires sur la manière d'utiliser TurboRepo pour une intégration transparente dans notre flux de travail.

---

# Conclusion

Le Monorepo avec TurboRepo est la solution idéale pour harmoniser nos projets frontend, simplifier la gestion des dépendances et des versions, et améliorer notre productivité. En adoptant cette approche, nous réduisons les erreurs, facilitons la collaboration et accélérons nos processus de développement.

N'attendons plus, faisons le choix du Monorepo avec TurboRepo et prenons notre développement frontend vers de nouveaux sommets !


---

# Sources

- https://monorepo.tools/