# Site Roger.dev

Site one-page pour [Roger.dev](https://roger.dev) — développeur indépendant en Suisse. Présente le projet et les 3 applications Android (alpha-theta, habitflow-mobile, subtracker-mobile).

> **Statut** : aucune application n'est encore publiée. Cette page décrit le projet et le travail en cours.

## Stack

- **HTML5 + CSS pur** (aucun framework, aucune dépendance JS lourde)
- **Police** : [Inter](https://fonts.google.com/specimen/Inter) (Google Fonts)
- **Icônes** : SVG inline (favicon + 3 icônes d'apps, dans `assets/`)
- **JS** : ~20 lignes vanilla (menu mobile + année dynamique)
- **Hébergement prévu** : GitHub Pages (statique, aucun build)

## Arborescence

```
site/
├── index.html         # page unique
├── styles.css         # styles + variables CSS
├── README.md          # ce fichier
└── assets/
    ├── favicon.svg            # favicon gradient + R
    ├── app-alpha-theta.svg    # icône méditation
    ├── app-habitflow.svg      # icône tracker
    └── app-subtracker.svg     # icône radar
```

## Déployer sur GitHub Pages (3 minutes)

### 1. Créer le dépôt

Crée un dépôt nommé **`rogerdev.github.io`** (ou un autre nom si tu utilises un domaine personnalisé). Coche *Add a README file*.

### 2. Pousser le contenu du site

```bash
cd site
git init -b main
git add .
git commit -m "feat: site roger.dev one-page"
git remote add origin https://github.com/rogerdev/rogerdev.github.io.git
git push -u origin main
```

### 3. Activer Pages

Sur GitHub : **Settings → Pages → Build and deployment → Source : Deploy from a branch**, choisir `main` et `/ (root)`. Attendre ~1 minute.

→ Le site sera accessible sur **https://rogerdev.github.io**

### Domaine personnalisé (optionnel)

Si tu achètes `roger.dev` :
1. Dans `site/`, créer un fichier `CNAME` (sans extension) contenant juste `roger.dev`
2. Chez ton registrar, ajouter un CNAME `www` → `rogerdev.github.io` et un A record vers les IPs GitHub (185.199.108.153, .109.153, .110.153, .111.153)
3. Dans Settings → Pages → Custom domain : `roger.dev`, cocher *Enforce HTTPS*

## Développer en local

Aucun build : double-clic sur `index.html` suffit. Pour un serveur local propre (et tester le burger mobile) :

```bash
cd site
python -m http.server 8000
# ou avec npx
npx serve .
```

→ Ouvrir `http://localhost:8000`

## Modifier le contenu

| Pour changer… | Édite… |
|---|---|
| Nom de marque, liens nav | `index.html` section `<header>` |
| Titre hero, sous-titre | `index.html` section `.hero` |
| Description d'une app | `index.html` section `#applications` (article `.card`) |
| Roadmap (statuts) | `index.html` section `#roadmap` (modifier `class="done"` ↔ `"planned"` et le texte `.status`) |
| Couleurs | `styles.css` en haut, bloc `:root { --primary: …; --accent: …; }` |
| Liens « Google Play » | `index.html` boutons `.btn-soft` (chercher `href="#"`) |

## Quand une application sera publiée

Pour chaque app publiée :
1. **Card** : remplacer `<a class="btn btn-soft" href="#" aria-disabled="true">Bientôt…</a>` par un vrai lien Google Play (`href="https://play.google.com/store/apps/details?id=…"`) + retirer `aria-disabled`
2. **Roadmap** : passer le `<li>` de `class="roadmap-item planned"` à `class="roadmap-item done"`, et le texte de `.status` à « publié »
3. **Hero** : retirer la mention `⏳ Les applications ne sont pas encore publiées`

## Licence

Code du site : libre de droits. Contenu textuel (descriptions, ton éditorial) : à toi de décider — par défaut tout est Roger.dev.
