# Journal de bord — Portfolio de Lucas Charron

Compte rendu de la conversation avec Claude. Mis à jour à chaque étape importante.
Les règles de travail sont dans `CLAUDE.md` (même dossier).

---

## Où on en est (résumé rapide)

| Élément | État |
|---|---|
| Variables CSS (polices, graisses, couleurs, tailles en rem) | ✅ fait |
| Polices `@font-face` (Montserrat, Lexend, Antic Slab) | ✅ fait |
| `index.html` (méta, structure sémantique, classes des boutons) | ✅ fait |
| 11 autres pages HTML créées d'après le Figma | ✅ fait (images de 3 projets manquantes) |
| Header mobile (logo, burger, menu déroulant) | ✅ fait par Lucas |
| Header desktop (menu en ligne, bouton contact) | ✅ fait par Lucas |
| Boutons `.btn` (3 variantes + hover + focus) | ✅ fait par Lucas |
| **Hero** (accueil + à propos : mobile, tablette 768, desktop 1000+) | ✅ fait et vérifié par Lucas (21 nov.). Reste : décision sur le paragraphe 16 px (Figma) vs 14 px (charte/CSS) |
| Section accueil « À propos de moi » (carte) | ✅ fait et vérifié par Lucas (390 / 768 / 1440 px) |
| Sections accueil (compétences, projets, contact) | ⏳ à faire. **Reprise : « Mes compétences informatiques »** (plan et mesures dans la chronologie, rien d'écrit) |
| Footer | ⏳ à faire |
| Pages projets, à propos, contact, projet détail, mentions, justification | ⏳ à faire |

---

## Chronologie

### Session du 20 novembre 2026

**Variables CSS**
- Création d'un `:root` avec les polices (`--font-primary` Montserrat, `--font-secondary` Lexend, `--font-accent` Antic Slab) et les graisses (`--fw-*`).
- Lecture de la charte graphique Figma : 6 couleurs ajoutées (`--color-fond #E8D7F1`, `--color-mauve #DDCBD7`, `--color-accent #A167A5`, `--color-accent-fonce #7E4585`, `--color-violet-fonce #4A306D`, `--color-bleu-nuit #0E273C`).
- Ajout des tailles de texte (`--fs-*`). Les paires « 28 / 21 » et « 18 / 14 » de la charte sont des tailles **desktop / mobile**.
- Passage des tailles en **rem** (base `html { font-size: 62.5% }`, 1rem = 10px).
- Réorganisation de `style.css` : polices, variables, base.

**index.html**
- Explication des commentaires du modèle (lang, title, description, Open Graph, favicons).
- Remplissage : `lang="fr"`, `<title>Accueil-portfolio</title>` (choisi par Lucas), `description`, `og:title`, `og:type`, `og:image` (`img/logos/logo-lc-1200x630.png`). Reste à faire : `og:url` et une adresse complète pour `og:image` (quand l'URL du site sera connue).
- Revue du HTML puis corrections : `<script>` déplacé avant `</body>`, un seul `<main>`, titres h1 → h2 → h3, plus de `<p>` dans les `<a>`, `width`/`height` sur les images, `alt` améliorés, fautes corrigées.
- Comparaison avec le Figma mobile, puis application des améliorations sémantiques : burger (`<button>` + `aria-expanded`), icônes de compétences, `aria-label` sur les liens de projets, `aria-labelledby` sur les sections, groupe de boutons, photo en premier dans le hero.

**Autres pages (créées d'après le Figma)**
- `projets.html`, `a-propos.html`, `contact.html`, `mentions-legales.html`, `justification-des-choix.html`, et 6 pages projet : `page-robbies-lens.html`, `page-huddle.html`, `page-card-nft.html`, `page-flex-car.html`, `page-ia-au-travail.html`, `page-generateur-mdp.html`.
- Choix : listes en `<ul>` (Lucas préfère `<ul>` à `<ol>`, y compris pour le fil d'Ariane et le parcours).
- Pédagogie : explication de `<aside>` et `<dl>/<dt>/<dd>`, et de `action="#"` dans un formulaire.
- Ajout de **commentaires de structure** dans toutes les pages.

**CSS écrit par Claude puis retiré**
- Claude avait écrit un CSS complet (mobile-first + desktop). **Lucas a demandé de tout retirer** : `style.css` est revenu à l'état d'avant (polices, variables, base).

### Session du 21 novembre 2026

**Règle importante posée par Lucas**
- Il est développeur junior et **doit faire son portfolio à la main**. Claude doit le **guider et le conseiller**, pas coder à sa place. (Voir `CLAUDE.md`.)

**Header (fait par Lucas avec les conseils de Claude)**
- Header en flex, logo à gauche, burger à droite.
- Burger : `burger.svg` créé par Claude (autorisé : c'est un élément graphique). Taille Figma : 28 × 21 px, trois barres de 3 px. Bouton de 44 × 44 px (zone de clic), texte caché avec `font-size: 0`.
- Menu mobile : `position: absolute` sous le header. Piège compris : ne pas mettre `display: flex` directement sur `.menu-principal`, sinon `hidden` est annulé. Le menu mobile reste **en colonne** (en horizontal ça débordait).
- Logo : `logo-lc.svg` recadré par Claude sur le dessin, **fond retiré**, et ratio du **rectangle d'or** (`viewBox="419.5 258 783 484"`, ratio 1,618 ; Figma = 1,6). Dimensions HTML des 12 pages : `width="57" height="35"`.
- Header mobile aux mesures du Figma : hauteur 67 px (`padding: 1.15rem 2rem`), logo 35 px de haut, burger à 20 px du bord droit (`margin-right: -0.8rem`). Liens du menu alignés avec le logo.
- **Header desktop** (Figma 1440 px) : hauteur 103 px, `padding: 2.4rem 8rem`, logo 55 px de haut, menu en ligne avec `gap: 4.8rem`, bouton « contact » (fond accent foncé) via `.menu-principal li:last-child a`, burger caché. Vérifié responsive.

**Boutons**
- Convention de classes : `.btn` (base) + `.btn--primary` / `.btn--secondary` / `.btn--accent`.
- Claude a ajouté les classes dans le HTML de **toutes les pages** (15 boutons) et vérifié chaque bouton avec le Figma. Écart corrigé : le hero de `a-propos.html` a maintenant « Télécharger mon CV » (accent) puis « Me contacter » (secondaire).
- Lucas a écrit le CSS des boutons. Corrections demandées et faites par Claude : `padding: 1.2rem 2.6rem` (hauteur de 46 px comme Figma) et `border-color` au `:hover`.
- Note PhpStorm : l'avertissement « font-family does not have generic default » sur `var(--font-accent)` est une **fausse alerte** (la police générique est dans la variable). Lucas peut l'ignorer.

**Hero — avancement (21 novembre)**
- Classes ajoutées dans `index.html` par Lucas : `hero`, `hero__photo`, `hero__text`, `hero__badge`, `hero__subtitle`, `hero__buttons`. Claude a ajouté `hero__description` sur le paragraphe.
- CSS écrit par Lucas : `.hero`, `.hero__photo`, `.hero__text`, `.hero__badge`, `h1`, `.hero__subtitle`, `.hero__description`. `body` a maintenant `font-family` (Lexend) et `color`.
- Valeur Figma de la photo : `border-radius` 21,6 px = `2.16rem` (comme le décalage du rectangle accent), pas `0.8rem`.
- Piège rencontré : l'attribut HTML `height="1322"` de l'image écrasait `aspect-ratio` → ajouter `height: auto` en CSS.
- Bug corrigé par Claude : le sélecteur `.hero p` écrasait `.hero__subtitle` (spécificité plus forte) → remplacé par la classe `.hero__description`.
- Relecture de Claude contre le Figma, puis corrections de Lucas : `h1` en `var(--font-primary)` + `var(--fw-medium)` ✅, `color: var(--color-violet-fonce)` sur `.hero__subtitle` ✅.
- **Écarts Figma encore ouverts** (Claude les avait appliqués puis ils ne sont plus dans les fichiers : à refaire par Lucas) :
  - `margin-bottom: 2.16rem` sur `.hero__photo` (le rectangle accent, en `box-shadow`, ne prend pas de place : sans ça il ne reste que 10 px avec le texte au lieu de 32 px) ;
  - mot « web » à la fin de la pastille dans `index.html` (Figma : « Recherche une alternance en développement web ») ;
  - `line-height` : `1.35` sur le `h1` et `1.33` sur `.hero__subtitle` (le reset met 1,5).
- **Reste ensuite** : écrire `.hero__buttons` (colonne, `gap: 2rem`, `align-items: flex-start`) ; version desktop du hero ; classes du hero de `a-propos.html`.
- **Suite (21 novembre)** : Lucas a demandé à Claude d'appliquer les points 1, 3, 4 → fait dans `style.css` : `margin-bottom: 2.16rem` sur `.hero__photo`, `line-height` 1.35 (`h1`) et 1.33 (`.hero__subtitle`), nouveau bloc `.hero__buttons` (flex colonne, `align-items: flex-start`, `gap: 2rem`). Point 2 (mot « web » dans la pastille) : **abandonné**, Lucas le juge inutile. Hero mobile terminé, à vérifier dans le navigateur. Prochaine étape : hero desktop.
- **Comparaison Figma mis à jour (21 nov.)** : `h1` 40 px, sous-titre 21 px et lien CV (accent foncé) sont maintenant d'accord avec la charte et le CSS. Corrigé par Claude à la demande de Lucas : `line-height` du hero (`h1` 1.2 ; sous-titre, paragraphe, pastille 1.25, car le Figma est en interligne automatique, estimation d'après capture), pastille pleine largeur (`align-self: stretch`) et en Regular, `.hero__cv` en SemiBold + `:focus-visible`, espace avant `{` sur les règles du hero. **Encore ouvert** : paragraphe du hero à 16 px dans le Figma contre 14 px (charte et CSS) → Lucas doit trancher (conseil : mettre 14 px dans le Figma). Décalage de 8 px des boutons/CV : artefact du Figma, non reproduit.
- **Hero desktop (21 nov.)** : Lucas a écrit la `@media (min-width: 768px)` (ligne, `padding 9.6rem 8rem`, `gap 6.4rem`, `order: 2`, etc.). Mesures Figma desktop corrigées : gap texte/photo **64 px** (pas 24), gap interne du texte 24 px. Claude, à la demande de Lucas, a ajouté : tailles de texte (`--fs-title-xl`, `--fs-text-l`, `--fs-text-m`), photo 36rem / rayon et ombre 2.4rem / marges bas et droite 2.4rem, `gap: 2.4rem` sur `.hero__text` et `.hero__buttons`. À vérifier dans le navigateur (non testé). Reste : ajouter les classes dans le hero de `a-propos.html`, puis les sections suivantes.
- **Hero de `a-propos.html` (21 nov.)** : classes ajoutées par Claude à la demande de Lucas : `hero__description` sur le paragraphe, `hero--apropos` (modificateur) sur la section ; `hero__badge` retiré du `<h1>` (le Figma n'a pas de pastille sur cette page : c'est un titre 72 px). **Différences desktop avec l'accueil** (Figma 82:64) : photo à **gauche** (pas de `order: 2`), `padding: 8rem` partout, `gap: 8rem` ; pas de lien CV souligné mais un bouton accent « Télécharger mon CV ». **À faire par Lucas** : règles `.hero--apropos` dans la `@media` pour annuler `order: 2` et ajuster padding/gap/marges de la photo.
- **Défilement horizontal à 768 px (21 nov.)** : à 768 px le hero en ligne ne laissait que ~160 px au texte (padding 160 + photo 384 + gap 64) → débordement, header « coupé » (il ne fait que la largeur de la fenêtre). Corrigé par Claude à la demande de Lucas : la `@media` du hero passe de `768px` à **`1000px`** (valeur estimée, à affiner en redimensionnant la fenêtre) ; `flex-wrap: wrap` sur `.hero__buttons` ; `white-space: nowrap` sur `.btn` et `.hero__cv`. Entre 768 et 999 px, le hero reste en colonne comme le mobile. Non testé dans un navigateur.
- **Hero tablette (21 nov.)** : à 768–999 px le hero en colonne laissait un grand vide à droite. Choix de Lucas : version **compacte en ligne dès 768 px** (option B). Réorganisé par Claude à sa demande : `@media (min-width: 768px)` = disposition en ligne (padding `6.4rem 4rem`, gap `4rem`, photo `28rem`, textes du mobile) ; `@media (min-width: 1000px)` = mesures Figma desktop (uniquement les valeurs qui changent). Valeurs calculées (~346 px pour le texte à 768 px), **non testées** : à vérifier à 768, 900, 999, 1000 et 1440 px.
- **Section « À propos de moi » de l'accueil (21 nov.)** : Claude a lu le Figma (mobile 142:184, desktop 79:46) et ajouté dans `index.html` les classes `about` (section = la carte), `about__text` (nouveau `<div>` autour du `h2` et du `p`), `about__title`, `about__description`. Mesures : mobile section `padding 1.6rem 2rem 6.4rem`, carte colonne `gap 2rem`, `padding 3.2rem 2.4rem`, rayon 2rem, texte `gap 1.2rem`, titre 32 px, paragraphe 16 px ; desktop section `padding 0 8rem 6.4rem`, carte en ligne `gap 4.8rem` `padding 4.8rem` rayon 2.4rem, texte `gap 1.6rem` `flex: 1`, titre 40 px, paragraphe 18 px. **À trancher par Lucas** : (1) fond de carte `#708299` dans le Figma vs mauve `#DDCBD7` de la charte (contraste ~3,9:1 estimé, sous AA) ; (2) paragraphe mobile 16 px (hero et cette section) vs 14 px charte. **À faire par Lucas** : le CSS `.about`.
- **Décisions de Lucas (21 nov.)** : (1) fond de la carte « à propos » = **`#708299` du Figma** (pas le mauve de la charte) → prévoir une variable `--color-carte: #708299` dans `:root` ; contraste bleu nuit/`#708299` estimé à ~3,9:1 (< 4,5:1 AA pour le paragraphe), **à contrôler avec un outil** et à reconsidérer si illisible ; (2) paragraphes mobile à **14 px (charte)**, donc `--fs-text-m-small`, « on avisera si ce n'est pas beau » (le Figma est à 16 px sur mobile).
- **CSS `.about` relu et corrigé (21 nov.)** : Claude a corrigé à la demande de Lucas : `display: flex` manquant sur `.about__text` (le `gap` ne marchait pas), `line-height: 1.5rem` du titre → `1.2`, règle `.about__description` ajoutée (14 px, Light, `1.25`), `border-radius: 2rem` en mobile, sélecteur `.btn btn--primary` → `.about .btn`, marges desktop `0 8rem 6.4rem` (Figma), espaces avant `{`. Non testé dans un navigateur. À faire : contrôler la lisibilité du texte sur `#708299`.
- **Captures de Lucas à 390 / 768 / 1440 px (21 nov.)** : mobile et desktop conformes au Figma ; à 768 px le titre de la carte « À propos » se coupait (« À propos de / moi ») et ses marges (80 px) n'étaient pas alignées avec le hero (40 px). Corrigé par Claude à la demande de Lucas : `.about` en deux paliers comme le hero : **768 px** = ligne, `margin: 0 4rem 6.4rem`, textes du mobile (32 px / 14 px) ; **1000 px** = `margin: 0 8rem 6.4rem`, `gap` texte 1.6rem, titre 40 px, paragraphe 18 px. À revérifier par Lucas à 768 et 1000 px. Lisibilité sur `#708299` jugée acceptable (à confirmer avec un outil de contraste).
- **Section « Mes compétences informatiques » : plan donné, rien d'écrit (arrêt de la session, 21 nov.)** — mesures Figma :
  - Mobile : section `padding 4rem 2rem 2.4rem`, `gap` titre/cartes 2.4rem, titre 32 px (`--fs-title-m`) ; cartes en **2 colonnes**, `gap 1.6rem`, fond `--color-carte`, rayon 1.2rem, `padding 2.4rem 1.2rem`, contenu en colonne centrée `gap 1.6rem` ; icône **96 px de haut** (`height: 9.6rem; width: auto`) ; nom Lexend Regular 21 px (`--fs-text-l-small`).
  - Desktop : section `padding 3.2rem 8rem 6.4rem`, `gap` 4rem, titre 40 px (`--fs-title-l`) ; **4 colonnes**, `gap 2.4rem`, carte `padding 3.2rem 2.4rem` ; nom 20 px dans le Figma.
  - Tablette : 4 colonnes ne tiennent pas à 768 px (~106 px utiles par carte, « Tailwind CSS » ~130 px) → **2 colonnes jusqu'à 999 px, 4 à partir de 1000 px** (`display: grid`, `grid-template-columns: repeat(2, 1fr)` puis `repeat(4, 1fr)`).
  - Classes HTML proposées (pas encore ajoutées) : `skills` (section), `skills__title` (h2), `skills__list` (ul), `skills__card` (li), `skills__icon` (img), `skills__name` (p).
  - **À décider par Lucas** : (1) nom de la carte à 20 px (Figma desktop) ou 21 px partout (conseillé, 20 n'est pas dans la charte) ; (2) titre « informatique » (Figma) ou « informatiques » (HTML, pluriel correct) ; (3) vérifier que `javascript.svg` contient bien les lettres « JS » (dans le Figma elles sont du texte posé sur le logo) ; (4) vérifier que les puces des `<ul>` sont retirées et que l'icône HTML5 (108 × 96) n'est pas déformée (HTML : `width="64" height="64"`).
  - **Reprise** : dire « fais-le » pour que Claude ajoute les classes dans `index.html`, puis Lucas écrit le CSS (`.skills`) et dit « j'ai fait, vérifie ».
- **Lien CV du hero (erreur de Claude corrigée)** : Claude avait conseillé `btn--accent` en se basant sur des textes du Figma, sans avoir vu la maquette. Lucas a constaté que, dans le Figma, « Mon CV » est **un simple texte souligné**, pas un bouton. Correction faite : le lien a maintenant `class="hero__cv"` (plus de `btn`). **À faire par Lucas** : écrire `.hero__cv` dans `style.css` (police, taille, couleur du Figma, `text-decoration: underline`, focus). À vérifier aussi : casse du dossier `cv`.

**Hero — plan donné (rappel des mesures Figma)**
- Mobile : photo 324 × 378 px (ratio 6:7) avec rectangle accent décalé de 21,6 px (`box-shadow` plein), texte dessous (gap 16 px), boutons en colonne (gap 20 px).
- Desktop : texte à gauche, photo 360 × 420 px à droite (`order: 2`), `padding` horizontal 8rem, hauteur d'environ 636 px, gap de 24 px, boutons en ligne.
- Tailles : h1 4rem (mobile) / 7.2rem (desktop) ; sous-titre 2.1rem / 2.8rem ; paragraphe Light 1.4rem / 1.8rem ; pastille 14 px, `padding: 0.8rem 1.6rem`.
- Classes proposées : `hero`, `hero__photo`, `hero__text`, `hero__badge`, `hero__buttons`. (Ajoutées depuis.)

---

## Reste à faire / points en attente

1. **Hero** : finir le mobile (écarts Figma ouverts ci-dessus, puis `.hero__buttons`), puis le desktop ; ajouter les classes dans le hero de `a-propos.html`.
2. **Images manquantes** pour 3 projets : `img/projets/flex-car.png`, `img/projets/ia-au-travail.png`, `img/projets/generateur-mdp.png`.
3. **Liens « Voir le site »** des pages projet : ils pointent vers `#` (mettre les vrais liens).
4. **Formulaire de contact** : `action="#"`, rien n'est envoyé. Prévoir un script PHP ou un service externe.
5. **Open Graph** : `og:url` et adresse complète de `og:image`.
6. **Mentions légales** : champs « [À compléter] » (hébergeur, cookies) à la mise en ligne.
7. **Burger / logo** : petits écarts de 5 px (marges internes des SVG), optionnel.
8. **Footer**, sections de l'accueil, pages secondaires : tout le CSS reste à écrire.
9. **Nettoyage** : lignes vides en trop dans `style.css`, commentaires du modèle dans `index.html` à supprimer à la fin.
10. `js/nav.js` : le script plante s'il n'y a pas de bouton dans le `<nav>` (c'est bon sur toutes les pages actuelles).
