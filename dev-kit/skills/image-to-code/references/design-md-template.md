# Template DESIGN.md

Format des fichiers de VoltAgent/awesome-design-md, qui reprend le format DESIGN.md de Google Stitch : un document Markdown décrivant comment le projet doit **ressembler** (à la différence d'`AGENTS.md`, qui décrit comment le construire). Sert ici de support à l'étape d'analyse.

Remplir uniquement avec ce qui est observé dans la référence. Écrire « non visible » plutôt qu'inventer.

```markdown
# DESIGN.md — <nom du projet ou de la référence>

## 1. Visual Theme & Atmosphere
Ambiance, densité, philosophie en 3 à 5 phrases (clair/sombre, calme/dense, éditorial/produit…).

## 2. Color Palette & Roles
| Rôle | Nom | Hex | Usage |
|------|-----|-----|-------|
| Background | | #  | |
| Surface | | #  | |
| Text primary | | #  | |
| Text secondary | | #  | |
| Accent | | #  | CTA principal uniquement ? |
| Border | | #  | |

## 3. Typography Rules
Familles (titres / texte / mono), puis tableau : niveau | taille | graisse | interlignage | tracking | usage.

## 4. Component Stylings
Boutons (primaire, secondaire, états), cartes, champs, navigation : forme, rayon, remplissage, bordure, ombre.

## 5. Layout Principles
Échelle d'espacement, grille, largeur max, gouttières, rythme entre sections, ratios des médias.

## 6. Depth & Elevation
Ombres, niveaux de surface, flou/transparence éventuels.

## 7. Do's and Don'ts
Garde-fous propres à cette référence (ex. « un seul accent par écran », « pas de coins arrondis »).

## 8. Responsive Behavior
Points de rupture, tailles de cibles tactiles, comment les colonnes et la navigation se replient.

## 9. Agent Prompt Guide
Références rapides de couleurs et 2 ou 3 prompts prêts à l'emploi pour construire une section dans ce style.
```
