# Landing Page Brinstar — brinstar.fr

Landing page / site vitrine de Brinstar Studio. Site statique, pas de build step.

## Contexte
- URL : https://brinstar.fr
- Hébergement : GitHub Pages (deploy auto sur push `main`)
- Custom domain : `CNAME` → `brinstar.fr` (DNS OVH)
- Repo : https://github.com/EverAsunder/landing-page-brinstar
- Pas de build process — le repo root est déployé tel quel
- Pas de package.json, pas de dépendances

## Architecture
- Single HTML file (`index.html`) + logo + CNAME
- **Tailwind CSS v2** chargé depuis CDN (pas installé localement)
- **Google Analytics** : tag `G-VZS7GYHQXM` (propre à la landing, séparé des apps)
- OG meta tags pointant vers `https://brinstar.fr/logo.png`
- Inline `<style>` pour les animations custom

## SEO (obligatoire)
La landing page DOIT être indexable par Google. Fichiers requis à la racine :
- **`sitemap.xml`** — liste des pages du site avec `<lastmod>`
- **`robots.txt`** — autorise le crawl, pointe vers le sitemap
- **Meta tags** dans `<head>` : title, description, og:title, og:description, og:image, canonical URL
- **Google Search Console** : le site doit être vérifié et le sitemap soumis
- Données structurées JSON-LD (Organization) si pertinent

## Apps Brinstar (à référencer sur la landing)
- **Habit Loop** — suivi d'habitudes → habitloop.brinstar.fr
- **Recall** — mini-jeux brain training → recall.brinstar.fr
- **Wallrun** — jeu de stratégie → wallrun.brinstar.fr
- **MealMap** — planification de repas → mealmap.brinstar.fr
- **Alchemy** — jeu merge/puzzle → alchemy.brinstar.fr
- **Banned** — tracker de mots bannis + gages → banned.brinstar.fr
- **Anima** — créature virtuelle + gamification → anima.brinstar.fr (à venir)
- **CaloriesGrind** — compteur de calories → calgrind.brinstar.fr (à venir)

## Design
- Esthétique retro gaming : fond sombre (`bg-gray-950`), accent pink (`pink-400`/`pink-500`), police monospace
- Cohérent avec le branding Brinstar (palette néon/synthwave)

## Git workflow (OBLIGATOIRE)

### Début de chaque session — exécuter en premier
```bash
git fetch origin
git branch -vv
```
- Si `main` est `[ahead X]` → **stop**, investiguer les commits sauvages avant de continuer
- Sinon :
```bash
git checkout main && git pull origin main
git checkout develop
git status
```

### Règles
- **JAMAIS de commit direct sur `main`** — `main` = prod (GitHub Pages deploy auto)
- Travailler sur `develop` ou `feature/*` + PR vers `main`
- `gh pr create --base main`

## Conventions
- Contact email : hugo@brinstar.fr
- **JAMAIS de mention de Claude, Anthropic, IA, "AI-assisted", "Co-Authored-By" ou similaire dans les commits, PRs, ou commentaires de code. Aucune trace d'IA dans l'historique git.**
