# IozyKit

La charte graphique des apps Iozy : IozyCore (dépôt `iozycore`) et IozyTest (dépôt `iozytest`). Les trois dépôts se clonent côte à côte dans `Projets/`. `README.md` décrit le contenu, `CHARTE.md` les règles et leurs raisons : lis-les avant de toucher à une couleur.

## Vérifier

`npm test` : régénère `css/tokens.css` depuis `tokens.json` et vérifie le contraste AA dans les deux thèmes (texte 4,5:1, bord des champs et focus 3:1). Lis le code de sortie. `css/tokens.css` est généré : ne l'édite pas à la main. Sous Windows, `npm test` le réécrit en LF : un ` M` sans changement de contenu est du bruit, remets le fichier tel qu'il était.

## Publier

Les apps épinglent un tag par l'archive HTTPS (`IozyKit/archive/refs/tags/vX.Y.Z.tar.gz`), jamais `github:` (npm en ferait une adresse `git+ssh`). Pour livrer une charte :

1. `npm test`, puis commit ;
2. avance `version` dans `package.json`, tag annoté `vX.Y.Z`, push du commit et du tag ;
3. dans chaque app, la nouvelle adresse dans `package.json`, `npm install`, puis ses contrôles (IozyCore : `npm test` et `npm run check:contrast` dans `iozycore/web` ; IozyTest : `npm run typecheck`, `npm run lint`, `npm run test:unit`).

Un tag publié ne bouge plus : une correction est un nouveau tag.

## Conventions

- Commentaires, documents et messages de commit en **français**, Conventional Commits (`feat(kit): …`, `fix(kit): …`).
- Pas de couleur en dur dans les apps : tout passe par un jeton `--iozy-*`.
- Ce qu'on touche est une pilule (`.iozy-btn`, `.iozy-field`, `--iozy-radius-pill`) ; les panneaux et squelettes gardent `--iozy-radius-control`.
- Dépôt public : aucune adresse ni clé d'une installation.
