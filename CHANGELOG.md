# Changelog

Toutes les modifications notables de ce projet sont documentées ici.  
Format basé sur [Keep a Changelog](https://keepachangelog.com/fr/1.0.0/).

---

## [0.2.0] — 2026-04-15

### Ajouté
- **Panneau "Proposer un assistant"** : bouton `+` dans le header ouvrant un panneau latéral coulissant prêt à accueillir un formulaire Microsoft Forms en iframe
- **Base de données JSON** : fichier `data/assistants.json` externalisant toutes les données — rechargé dynamiquement à chaque visite, versionnable sur GitHub
- **Favoris persistants** : étoile ☆/★ sur chaque carte, mémorisée dans le localStorage du navigateur
- **Données de secours** : si `assistants.json` est inaccessible (ouverture locale sans serveur), les données sont chargées depuis un tableau JS intégré

### Modifié
- **Redesign des cartes** : nouvelle structure visuelle inspirée de Groupe SNCF GPT — icône en haut à gauche (fond coloré), étoile + menu ⋮ en haut à droite, tags colorés par catégorie, coins arrondis à 16 px
- **Rendu dynamique** : les cartes sont désormais générées par JavaScript depuis les données JSON, plus de HTML statique pour chaque assistant
- **Palette de couleurs** : tons plus doux et contrastés, chaque catégorie dispose d'une couleur de fond claire et d'une couleur de texte assortie
- **Sidebar** : fond blanc, bordure droite, champ de recherche avec icône loupe et bordure arrondie
- **Filtres** : chips avec bordure et état actif plus marqué
- **Stats sidebar** : alimentées dynamiquement depuis `data/assistants.json`

### Supprimé
- Barre d'accent colorée en haut de chaque carte (remplacée par l'icône colorée)
- Carte "Nouvelle" statique en bas de grille (remplacée par le bouton `+` dans le header)
- HTML statique des cartes individuelles

---

## [0.1.0] — 2026-04-15

### Ajouté
- **Structure initiale** : application monopage (`index.html`) avec layout sidebar 1/3 + contenu 2/3
- **8 assistants** : Sunshine (vedette), Aurore, Éclipse, Zénith, Équinoxe, Halo, Lumière, Rayon
- **Carte vedette** (hero) : Sunshine en pleine largeur avec illustration animée et orbites
- **Filtres** par catégorie (6) et par plateforme (3)
- **Recherche plein texte** en temps réel
- **Animations d'apparition** au scroll via IntersectionObserver
- **Responsive** : layout colonne unique sous 860 px
- **Palette SNCF** : bleu marine primaire, cerulean, menthe, lavande, ambre, ocre, bourgogne

---

*Les versions suivent [Semantic Versioning](https://semver.org/lang/fr/) : MAJEUR.MINEUR.CORRECTIF*
