---
name: image-to-code
description: Build a frontend faithful to a visual reference (screenshot, mockup, URL or DESIGN.md). Analyze first, code second, verify with screenshots. Use for "reproduce this design" or image-to-code.
---

# image-to-code (version condensée)

Adaptation, pour Claude, de `image-to-code-skill` (Leonxlnx/taste-skill, MIT), complétée par les DESIGN.md de VoltAgent/awesome-design-md (MIT) et par `playwright-cli` de Microsoft (Apache-2.0) pour la vérification. Différence majeure avec l'original : **la génération d'images n'est pas obligatoire**. La référence peut être une image fournie, un DESIGN.md, un site existant ou un DESIGN.md écrit par toi.

Principe : la référence est la source de vérité visuelle, le code en est la traduction. Ordre imposé : **référence → analyse → implémentation → vérification**. Ne pas commencer par coder « au feeling ».

## 1. Obtenir la référence (dans cet ordre)

1. **Image de l'utilisateur** (capture, maquette) : la regarder pour de vrai, section par section.
2. **DESIGN.md d'une marque** : proposer une marque proche du ton voulu (`references/design-md-catalog.md`), puis lire son DESIGN.md via `web_fetch` si l'URL est disponible, ou demander à l'utilisateur de le coller. Ne jamais reconstituer ses valeurs de mémoire.
3. **URL d'un site** : captures avec `playwright-cli` si disponible (`references/playwright-verify.md`), sinon `web_fetch` et description honnête de ce qui n'a pas pu être vu.
4. **Rien de visuel** : si un outil de génération d'images existe, générer une référence **par section** (texte lisible, pas de planche compressée, jamais de recadrage d'une ancienne image). Sinon, écrire d'abord un DESIGN.md (`references/design-md-template.md`) et le faire valider en deux lignes avant de coder.

Si le texte ou un détail est illisible : demander une capture plus nette ou une section isolée. Ne pas combler au hasard.

## 2. Analyse avant code

Extraire, puis consigner dans un DESIGN.md court (9 sections, voir le template) ou un tableau :

- **Texte** : titres, sous-titres, libellés de boutons, navigation, tel que lisible.
- **Typographie** : famille et ambiance (grotesque, serif éditorial, display…), échelle, graisses, interlignage, tracking, nombre de lignes des titres.
- **Espacement** : gouttières, paddings, écarts titre/texte/bouton, marges haut et bas des sections, rythme général.
- **Boutons et composants** : taille, rayon, plein vs contour, hiérarchie primaire/secondaire, cartes, séparateurs, ombres, états implicites.
- **Couleurs** : fond, surfaces, accent, texte (hiérarchie), bordures, en hex.
- **Layout** : grille, ordre des sections, ratio image/texte, cadres média à ratios fixes.

Si un point reste flou, résoudre dans cet ordre : langage visuel, layout, famille de composants, ambiance, puis seulement le choix le plus simple à implémenter.

## 3. Règles de conception

- **Hero** : un seul point focal, titre de 1 à 3 lignes, texte d'appui court, CTA visible, lisible sur un petit laptop (1280×720). Pas de pilules, badges, fausses stats ni micro-libellés pseudo-techniques (« 00 orchestration layer »).
- **Pas de boîtes dans des boîtes** : pas de grands conteneurs arrondis autour de tout, pas de cartes dans des cartes. Un conteneur doit avoir une raison d'être ; préférer espace et alignement.
- **Peu de micro-UI** : pas de chips ni de métadonnées décoratives qui n'apportent aucune information.
- **Médias** : cadres à ratio fixe, rayon cohérent, mêmes traitements d'une section à l'autre.
- **Rythme** : faire varier densité, échelle et alignement d'une section à l'autre sans casser la cohérence ; garder un espacement généreux et régulier.
- **Anti-slop** : pas de dégradé violet/bleu par défaut, de halos partout, de glassmorphism empilé ; pas de copy creuse (« unleash », « elevate », « seamless », « next-gen ») ni de fausses marques (Acme, Nexus…).
- **Marques** : un DESIGN.md de marque sert à comprendre un langage visuel (tokens, rythme, ton). Ne pas reproduire ses logos, noms, visuels ou textes protégés dans le livrable.

## 4. Implémentation

- Traduire l'analyse en variables CSS (couleurs, échelle typographique, espacements, rayons) et s'y tenir.
- **Anti-dérive** : ne pas remplacer une section distinctive par une rangée générique, ne pas tasser un espacement généreux, ne pas aplatir la typographie, ne pas réintroduire de boîtes imbriquées.
- Responsive dès le départ ; accessibilité de base (contrastes, labels, focus visibles, `prefers-reduced-motion`).
- Si disponibles, s'appuyer sur `design-taste-frontend` (direction et anti-patterns) et passer `web-design-guidelines` sur le résultat.

## 5. Vérification (boucle courte)

1. Servir la page en local (Playwright bloque `file://` par défaut) et la capturer à 1280×720 puis en mobile avec `playwright-cli` : commandes dans `references/playwright-verify.md`.
2. Comparer à la référence : texte, hiérarchie typographique, espacements, couleurs, ordre des sections.
3. Corriger les écarts les plus visibles, recapturer. 2 ou 3 itérations suffisent.
4. Si aucun navigateur n'est utilisable dans l'environnement (installation ou téléchargement bloqués), ne pas insister : relire le code contre l'analyse et dire explicitement que le rendu n'a pas été vérifié visuellement.

## 6. Contrôle final

- L'analyse a-t-elle précédé le code, et le texte lisible a-t-il été repris ?
- Hero propre, court, lisible à 1280×720 ?
- Pas de boîtes imbriquées, de pilules ni de jargon décoratif ?
- Typographie, espacements et couleurs fidèles à la référence, sans dérive vers un template ?
- Rendu vérifié (captures) ou signalé comme non vérifié ?
