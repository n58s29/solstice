# Changelog

Toutes les modifications notables de ce projet sont documentées ici.  
Format basé sur [Keep a Changelog](https://keepachangelog.com/fr/1.0.0/).

---

## [0.4.0] — 2026-04-15

### Ajouté
- **Tags métiers** sur chaque carte : affichage des familles métier associées à l'assistant (fond indigo clair)
- **Filtre par métier** dans la sidebar : 12 chips cliquables (Transverse, RH, Achats, Finance, Marketing & Com, Ingénierie, Exploitation, Commercial, Juridique, Sécurité, IT & Numérique, Immobilier & Facilities) — sélection multiple possible, logique OU
- **Colonne `metiers`** dans `data/assistants.csv` : valeurs séparées par `|` (ex. `Transverse|RH`)
- La recherche plein texte couvre désormais aussi les tags métiers

---

## [0.3.0] — 2026-04-15

### Ajouté
- **Dossier `img/`** : images par assistant (PNG/JPG), avec fallback automatique sur un placeholder initiales + fond bleu marine si le fichier est absent
- **Toggle "Mes favoris"** dans la sidebar pour n'afficher que les assistants étoilés

### Modifié
- **Base de données CSV** : `data/assistants.json` remplacé par `data/assistants.csv` — plus simple à éditer dans Excel ou un éditeur texte
- **Schéma des données simplifié** : 5 champs uniquement — `nom`, `description`, `lien`, `contact`, `image`. Suppression des catégories, plateformes, runs et couleurs (tous les assistants sont sur Groupe SNCF GPT)
- **Images à la place des emojis** : les cartes affichent désormais une image illustrant l'assistant plutôt qu'un caractère emoji
- **Sidebar épurée** : suppression des filtres catégorie et plateforme, remplacés par le toggle favoris
- **Note panneau Forms** mise à jour pour refléter le processus manuel (mise à jour du CSV après réception des réponses)

### Supprimé
- Carte vedette (featured/hero card)
- Filtres par catégorie et par plateforme
- Emojis comme icônes de carte
- `data/assistants.json`

---

## [0.2.0] — 2026-04-15

### Ajouté
- Panneau "Proposer un assistant" (bouton `+` → panneau latéral coulissant avec iframe Microsoft Forms)
- `data/assistants.json` comme base de données chargée dynamiquement
- Favoris persistants via localStorage (étoile ☆/★ sur chaque carte)
- Données de secours intégrées si le fichier JSON est inaccessible

### Modifié
- Redesign des cartes : style Groupe SNCF GPT — icône en haut à gauche, étoile + menu en haut à droite, tags colorés par catégorie, coins arrondis à 16 px
- Rendu dynamique des cartes depuis les données (fin du HTML statique)
- Sidebar : fond blanc, champ de recherche avec icône loupe, chips avec bordure

### Supprimé
- Barre d'accent colorée en haut de carte
- Carte "Nouvelle" statique en bas de grille

---

## [0.1.0] — 2026-04-15

### Ajouté
- Structure initiale : layout sidebar 1/3 + contenu 2/3
- 8 assistants en HTML statique : Sunshine (vedette), Aurore, Éclipse, Zénith, Équinoxe, Halo, Lumière, Rayon
- Carte vedette hero pleine largeur avec illustration animée
- Filtres catégorie (6) et plateforme (3)
- Recherche plein texte en temps réel
- Animations d'apparition au scroll via IntersectionObserver
- Responsive mobile (colonne unique sous 860 px)

---

*Les versions suivent [Semantic Versioning](https://semver.org/lang/fr/) : MAJEUR.MINEUR.CORRECTIF*
