# Solstice — Bibliothèque d'Assistants

Bibliothèque interne recensant tous les assistants **Groupe SNCF GPT** créés par la Fabrique de l'Adoption Numérique (FAN) · e.SNCF Solutions · Direction Numérique Groupe.

## Structure du projet

```
solstice/
├── index.html              # Application (HTML + CSS + JS, fichier unique)
├── data/
│   └── assistants.csv      # Base de données des assistants
└── img/
    ├── sunshine.png         # Image illustrant l'assistant (même nom que la colonne "image" du CSV)
    ├── aurore.png
    └── ...
```

## Ajouter ou modifier un assistant

Toutes les données sont dans [`data/assistants.csv`](data/assistants.csv). Ouvrez-le dans Excel (UTF-8) ou un éditeur texte.

### Colonnes

| Colonne | Description | Exemple |
|---|---|---|
| `nom` | Nom de l'assistant | `Sunshine` |
| `description` | Description courte (2-3 phrases) | `Prépare vos ateliers IAGEN...` |
| `lien` | URL de l'assistant sur Groupe SNCF GPT | `https://chatgpt.com/g/...` |
| `contact` | Personne référente | `Mathieu Ribourg` |
| `image` | Nom du fichier image dans `img/` | `sunshine.png` |

### Exemple de ligne CSV

```csv
Sunshine,"Prépare vos ateliers IAGEN de A à Z.",https://chatgpt.com/g/xxx,Mathieu Ribourg,sunshine.png
```

> Si la description contient une virgule, entourez-la de guillemets doubles.

### Ajouter une image

1. Déposez le fichier image dans le dossier `img/` (PNG ou JPG, idéalement carré, minimum 104×104 px)
2. Renseignez le nom du fichier dans la colonne `image` du CSV
3. Si aucune image n'est fournie, l'application affiche automatiquement les initiales du nom sur fond bleu marine

## Brancher le formulaire Microsoft Forms

Dans [`index.html`](index.html), repérez le commentaire `MICROSOFT FORMS` et remplacez le bloc `placeholder-forms` par :

```html
<iframe
  src="https://forms.office.com/Pages/ResponsePage.aspx?id=VOTRE_ID&embed=true"
  title="Proposer un assistant"
  loading="lazy">
</iframe>
```

L'URL d'embed se trouve dans Forms → **Partager** → **Incorporer** → copier le `src` de l'iframe.

Après réception des réponses du formulaire, mettez à jour `data/assistants.csv` manuellement et ajoutez l'image correspondante dans `img/`.

## Déploiement sur GitHub Pages

1. Pousser le repo sur GitHub
2. **Settings → Pages → Source** : branche `main`, dossier `/` (root)
3. Dans `index.html`, mettre à jour `CSV_URL` :

```js
const CSV_URL = 'https://raw.githubusercontent.com/ORG/REPO/main/data/assistants.csv';
```

L'application est entièrement statique — aucun serveur backend requis.

## Contribuer

1. Modifier `data/assistants.csv` avec le nouvel assistant
2. Ajouter l'image dans `img/`
3. Ouvrir une PR sur la branche `main`
4. Après merge, la bibliothèque se met à jour au prochain rechargement de la page

---

*Fabrique de l'Adoption Numérique · e.SNCF Solutions*
