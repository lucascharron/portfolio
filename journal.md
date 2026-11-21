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
| **Hero** (photo, pastille, titre, texte, boutons) | 🔜 **prochaine étape** |
| Sections accueil (à propos, compétences, projets, contact) | ⏳ à faire |
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

**Hero — plan donné (à faire par Lucas)**
- Mobile : photo 324 × 378 px (ratio 6:7) avec rectangle accent décalé de 21,6 px (`box-shadow` plein), texte dessous (gap 16 px), boutons en colonne (gap 20 px).
- Desktop : texte à gauche, photo 360 × 420 px à droite (`order: 2`), `padding` horizontal 8rem, hauteur d'environ 636 px, gap de 24 px, boutons en ligne.
- Tailles : h1 4rem (mobile) / 7.2rem (desktop) ; sous-titre 2.1rem / 2.8rem ; paragraphe Light 1.4rem / 1.8rem ; pastille 14 px, `padding: 0.8rem 1.6rem`.
- Classes proposées : `hero`, `hero__photo`, `hero__text`, `hero__badge`, `hero__buttons`. **Pas encore ajoutées dans le HTML** (Claude a proposé de le faire, en attente de la réponse de Lucas).

---

## Reste à faire / points en attente

1. **Hero** : ajouter les classes dans `index.html` et `a-propos.html`, puis écrire le CSS.
2. **Images manquantes** pour 3 projets : `img/projets/flex-car.png`, `img/projets/ia-au-travail.png`, `img/projets/generateur-mdp.png`.
3. **Liens « Voir le site »** des pages projet : ils pointent vers `#` (mettre les vrais liens).
4. **Formulaire de contact** : `action="#"`, rien n'est envoyé. Prévoir un script PHP ou un service externe.
5. **Open Graph** : `og:url` et adresse complète de `og:image`.
6. **Mentions légales** : champs « [À compléter] » (hébergeur, cookies) à la mise en ligne.
7. **Burger / logo** : petits écarts de 5 px (marges internes des SVG), optionnel.
8. **Footer**, sections de l'accueil, pages secondaires : tout le CSS reste à écrire.
9. **Nettoyage** : lignes vides en trop dans `style.css`, commentaires du modèle dans `index.html` à supprimer à la fin.
10. `js/nav.js` : le script plante s'il n'y a pas de bouton dans le `<nav>` (c'est bon sur toutes les pages actuelles).
