---
name: design-taste-frontend
description: Anti-slop frontend rules for landing pages, portfolios and redesigns. Reads the brief, picks a coherent design direction, avoids templated AI looks, ends with a pre-flight check.
---

# design-taste-frontend

Règles pour produire des interfaces web (landing pages, portfolios, redesigns) qui ne ressemblent pas à du code généré par défaut. Hors périmètre : dashboards, tableaux de données, produit multi-étapes (voir §13 du fichier de référence).

Les règles complètes (≈1200 lignes, copie du dépôt Leonxlnx/taste-skill, v2 expérimentale, MIT) sont dans `references/taste-full.md`. Ne les charge pas en entier : lis seulement ce qui sert.

## Workflow

1. **Lire le brief** (§0 de `references/taste-full.md`). Avant tout code, écrire une ligne : « Reading this as : <type de page> for <audience>, with a <vibe> language, leaning toward <système de design ou famille esthétique>. » Si le brief est vraiment ambigu, poser **une seule** question ; sinon ne pas demander.
2. **Régler les trois dials** (§1, définitions en §7) : variance de design, intensité de motion, densité visuelle.
3. **Choisir le système** (§2, commandes d'installation en annexe A) : design system existant (shadcn, Radix, Material, GOV.UK…) ou CSS natif, selon le brief.
4. **Construire** en respectant les conventions (§3), les directives d'ingénierie (§4), l'accessibilité et la performance (§6), et le mode sombre si pertinent (§8).
5. **Chasser les « AI tells »** (§9) : motifs interdits (dégradés violets par défaut, hero centré sur fond sombre, trois cartes identiques, glassmorphism partout…).
6. **Redesign d'un site existant** : audit d'abord, puis §11 (ce qu'on préserve, ce qu'on modernise).
7. **Pre-flight** (§14) : chaque case doit réellement passer avant de livrer.

## Carte des sections (`references/taste-full.md`)

| § | Contenu | Quand lire |
|---|---------|------------|
| 0 | Inférence du brief, « Design Read » | toujours |
| 1, 7 | Dials et définitions | toujours |
| 2 | Brief → système de design | au choix de la stack |
| 3, 4 | Architecture et directives | pendant la construction |
| 5 | Proactivité contextuelle | si le brief est ouvert |
| 6, 8 | Perf, accessibilité, dark mode | toujours / si thème sombre |
| 9 | AI tells (interdits) | toujours |
| 10 | Vocabulaire de patterns | pour nommer précisément une idée |
| 11 | Protocole de redesign | si site existant |
| 12 | Bibliothèque de blocs | si ajout itératif de blocs |
| 14 | Pre-flight | toujours, en dernier |
| Annexes A–C | Installation, sources, Liquid Glass | à la demande |

## Skills complémentaires

- `web-design-guidelines` : audit d'accessibilité / UX d'un code existant.
- `image-to-code` : construire à partir d'une capture, d'une maquette ou d'un DESIGN.md.

Source et licence : voir l'en-tête de `references/taste-full.md` et `references/LICENSE-taste-skill.txt`.
