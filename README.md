

# ⏱️ Cooking Timer —  Eggs & n'Tea

- **Participantes du projet** : Souare Khadidiatou | Sahraoui Selma
- **Formation** : LP PROJET WEB
- **Date** : Mars 2026

Une petite application web développée avec **Svelte + Vite** permettant de lancer facilement des minuteries pour :

* 🍵 l’infusion du thé
* 🥚 la cuisson des œufs

L’objectif du projet est de proposer une **interface simple et intuitive** pour gérer différents temps de cuisson ou d’infusion.

---

# 🚀 Aperçu du projet

L’application permet de :

* sélectionner un type de **thé**
* sélectionner une **recette d'œuf**
* lancer un **timer automatique**
* suivre la progression avec une **barre de progression**
🔊 **Notification sonore :** Une alerte sonore a été intégrée afin de signaler la fin du timer. Cette fonctionnalité améliore l’expérience utilisateur en permettant d’être averti sans avoir à surveiller l’écran en continu. Des contraintes liées aux navigateurs (autoplay audio) ont été prises en compte lors de son implémentation.

⚠️ **Note pour la démonstration :** Conformément aux consignes, les durées réelles d'infusion et de cuisson ont été divisées par 20 pour les besoins de la démo.

Le projet met en pratique plusieurs concepts importants :

* architecture modulaire
* composants réutilisables
* séparation logique / interface
* organisation par fonctionnalités

---

# 🛠️ Technologies utilisées

* **Svelte**
* **Vite**
* **JavaScript**
* **CSS**

Ces technologies permettent de construire une application **rapide, légère et moderne**.

---

# 📦 Installation du projet

Clone le projet :

```bash
git clone https://github.com/SelmaaSah/projet-svelte-timer
```

Entrer dans le dossier :

```bash
cd projet-svelte-timer
```

Installer les dépendances :

```bash
npm install
```

Lancer le serveur de développement :

```bash
npm run dev
```

L'application sera disponible sur :

```
http://localhost:5173
```

---

# 📁 Architecture du projet

Le projet suit une **architecture modulaire et scalable**.

```text
src/
├── App.svelte
├── main.js
│
├── data/
│   ├── teas.js
│   └── eggs.js
│
├── components/
│   ├── Header.svelte
│   ├── Tabs.svelte
│   ├── Timer.svelte
│   └── ProgressBar.svelte
│
├── features/
│   ├── tea/
│   │   ├── TeaSection.svelte
│   │   └── TeaCard.svelte
│   │
│   └── egg/
│       ├── EggSection.svelte
│       └── EggRecipe.svelte
│
├── lib/
│   └── timer.js
│
└── styles/
    └── app.css
```

---

# 🧩 Composants principaux

## Header

Affiche le **titre de l’application** et l’en-tête de l’interface.

---

## Tabs

Permet de **basculer entre les sections** :

* Tea
* Eggs

---

## Timer

Composant principal qui gère :

* démarrage du timer
* réinitialisation
* affichage du temps restant

---

## ProgressBar

Affiche **visuellement la progression du timer**.

La barre se remplit progressivement jusqu'à la fin du compte à rebours.

---

# 🧩 Organisation par fonctionnalités

Le dossier `features` regroupe les composants **par domaine fonctionnel**.

## 🍵 Tea

```
features/tea/
```

Contient les composants liés aux recettes de thé :

* `TeaSection` : liste des thés
* `TeaCard` : carte individuelle d'un thé

---

## 🥚 Egg

```
features/egg/
```

Contient les composants liés à la cuisson des œufs :

* `EggSection` : liste des recettes
* `EggRecipe` : recette individuelle

---

# 📊 Gestion des données

Les données statiques sont stockées dans :

```
data/
```

Exemples :

* temps d'infusion des thés
* temps de cuisson des œufs

Cela permet de **séparer les données de l’interface utilisateur**.

---

#  Logique métier

Le dossier `lib` contient la logique réutilisable :

```
lib/
└── timer.js
```

Ce fichier peut contenir des fonctions comme :

* formater le temps
* calculer la progression
* gérer le fonctionnement du timer

Cela permet de **séparer la logique métier de l'interface**.

---

# 🎨 Styles globaux

Les styles globaux sont définis dans :

```
styles/app.css
```

Ils permettent de gérer :

* typographie
* layout global
* variables CSS
* reset CSS

---

#  Principes d’architecture utilisés

### Architecture par composants

L’interface est découpée en **petits composants réutilisables**.

---

### Organisation par fonctionnalités

Le projet est organisé par **domaines fonctionnels** :

```
features/
  tea/
  egg/
```

Cela rend l'application plus **facile à maintenir et à faire évoluer**.

---

### Séparation des responsabilités

| Dossier    | Rôle                             |
| ---------- | -------------------------------- |
| components | composants UI réutilisables      |
| features   | logique et UI par fonctionnalité |
| data       | données statiques                |
| lib        | logique métier                   |
| styles     | styles globaux                   |

---

# 👨‍💻 Auteur

Projet réalisé dans le cadre d’un **apprentissage de Svelte et de l’architecture frontend moderne**.
