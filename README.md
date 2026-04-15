# Solstice — Bibliothèque d'Assistants

Bibliothèque interne recensant tous les assistants Groupe SNCF GPT créés par la **Fabrique de l'Adoption Numérique** (FAN) · e.SNCF Solutions · Direction Numérique Groupe.

## Fonctionnalités

- **Catalogue filtrable** par catégorie (Ateliers, Cadrage, Rédaction, Dev & Tech, Analyse, Formation) et par plateforme (GPT, Claude, Mistral)
- **Recherche plein texte** sur le nom, la description et les tags
- **Favoris** persistants dans le navigateur (localStorage)
- **Carte vedette** mise en avant pour l'assistant du moment
- **Formulaire de proposition** Microsoft Forms intégré en panneau latéral
- **Base de données JSON** versionnable sur GitHub, rechargée à chaque visite

## Structure du projet

```
solstice/
├── index.html            # Application (HTML + CSS + JS, fichier unique)
└── data/
    └── assistants.json   # Base de données des assistants
```

## Ajouter ou modifier un assistant

Toutes les données sont dans [`data/assistants.json`](data/assistants.json). Chaque entrée suit ce schéma :

```json
{
  "id": "identifiant-unique",
  "nom": "Nom de l'assistant",
  "description": "Description courte (2-3 phrases max).",
  "categorie": "cadrage",
  "plateforme": "gpt",
  "icone": "⚡",
  "couleur": "cerulean",
  "auteur": "Prénom",
  "runs": 42,
  "url": "https://chatgpt.com/g/...",
  "vedette": false,
  "tags": ["Cadrage", "GPT-4o"]
}
```

### Valeurs possibles

| Champ | Valeurs acceptées |
|---|---|
| `categorie` | `atelier` · `cadrage` · `redaction` · `dev` · `analyse` · `formation` |
| `plateforme` | `gpt` · `claude` · `mistral` |
| `couleur` | `cerulean` · `menthe` · `lavande` · `ambre` · `ocre` · `bourgogne` |
| `vedette` | `true` pour un seul assistant (affiché en carte héro) |

## Brancher le formulaire Microsoft Forms

Dans [`index.html`](index.html), repérez le commentaire `INTÉGRATION MICROSOFT FORMS` et remplacez le bloc `forms-placeholder` par :

```html
<iframe
  src="https://forms.office.com/Pages/ResponsePage.aspx?id=VOTRE_ID&embed=true"
  title="Proposer un assistant"
  allow="camera; microphone; geolocation"
  loading="lazy">
</iframe>
```

L'URL d'embed se trouve dans Microsoft Forms → **Partager** → **Incorporer** → copier le `src` de l'iframe.

## Automatisation via Power Automate

Pour que les réponses du formulaire mettent à jour `assistants.json` automatiquement :

1. **Déclencheur** : _Microsoft Forms — Quand une nouvelle réponse est soumise_
2. **Action** : _HTTP — PUT_ vers l'API GitHub Contents  
   `PUT https://api.github.com/repos/ORG/REPO/contents/data/assistants.json`
3. **Corps** : JSON de la réponse encodé en base64 + SHA du fichier actuel
4. GitHub committe automatiquement — la page se met à jour dès le prochain rechargement

> Un token GitHub (scope `repo` ou `contents:write`) est nécessaire dans les en-têtes de l'appel HTTP.

## Déploiement sur GitHub Pages

1. Pousser le repo sur GitHub
2. **Settings → Pages → Source** : branche `main`, dossier `/` (root)
3. Dans `index.html`, mettre à jour `DATA_URL` :

```js
const DATA_URL = 'https://raw.githubusercontent.com/ORG/REPO/main/data/assistants.json';
```

L'application est entièrement statique — aucun serveur backend requis.

## Palette de couleurs

| Couleur | Hex | Usage |
|---|---|---|
| Primaire (bleu marine) | `#001b44` | En-têtes, boutons principaux |
| Cerulean | `#0088cc` | Catégorie Cadrage |
| Menthe | `#007a5e` | Catégorie Rédaction |
| Lavande | `#5c4ec4` | Catégorie Dev & Tech |
| Ambre | `#c4900d` | Catégorie Ateliers |
| Ocre | `#c04a1a` | Catégorie Analyse |
| Bourgogne | `#7a1e30` | Catégorie Formation |

## Contribuer

1. Ouvrir une PR avec la modification de `data/assistants.json`
2. Décrire l'assistant dans le corps de la PR
3. Après merge, la bibliothèque se met à jour automatiquement

---

*Fabrique de l'Adoption Numérique · e.SNCF Solutions*
