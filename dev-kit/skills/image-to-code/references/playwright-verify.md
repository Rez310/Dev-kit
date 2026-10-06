# Vérification visuelle avec playwright-cli

Source : https://github.com/microsoft/playwright-cli (Apache-2.0). CLI conçue pour les agents : économe en tokens, elle n'injecte pas la page entière dans le contexte.

## Prérequis

Node.js 18+ puis :

```bash
npm install -g @playwright/cli@latest
playwright-cli --help
# optionnel : installer le skill officiel complet (tests, mocks, traces, vidéo…)
playwright-cli install --skills
```

Si `playwright-cli` n'est pas global : `npx playwright cli <commande>` (versions locales). Dans un environnement à réseau restreint, le téléchargement du navigateur peut échouer : le dire, ne pas insister (voir §5 de `SKILL.md`).

## Servir la page

Playwright bloque `file://` par défaut. Servir le dossier en local :

```bash
python3 -m http.server 8000   # dans le dossier du site, en arrière-plan
```

## Recette : capturer et contrôler

```bash
playwright-cli open http://localhost:8000
playwright-cli resize 1280 720
playwright-cli screenshot --filename=shots/desktop-1280x720.png
playwright-cli resize 390 844
playwright-cli screenshot --filename=shots/mobile-390x844.png
playwright-cli console warning                     # erreurs et avertissements console
playwright-cli eval "document.documentElement.scrollWidth > window.innerWidth"   # true = débordement horizontal
playwright-cli close
```

Variantes utiles :

```bash
playwright-cli open --device="iPhone 15"            # émulation d'un appareil
playwright-cli screenshot --hires                   # pleine densité de pixels
playwright-cli screenshot <ref> --filename=hero.png # un seul élément (ref issue du snapshot)
playwright-cli snapshot --depth=4                   # structure et refs, profondeur limitée
playwright-cli find "Commencer"                     # chercher du texte dans le snapshot
playwright-cli eval "el => getComputedStyle(el).fontSize" e5   # valeur calculée d'un élément
playwright-cli open <url> --headed                  # voir le navigateur
```

`playwright-cli show --annotate` ouvre le tableau de bord en mode revue UI (retours de design) : à proposer à l'utilisateur plutôt qu'à lancer seul.

## Capturer un site de référence

```bash
playwright-cli open https://exemple.com
playwright-cli resize 1280 720
playwright-cli screenshot --filename=ref/home-1280x720.png
playwright-cli eval "el => getComputedStyle(el).fontFamily" e12   # typographie réellement utilisée
playwright-cli close
```

N'extraire que ce qui sert l'analyse (tokens, mise en page). Ne pas copier les textes, logos ni images protégés.

## Garde-fous

- Sessions isolées par défaut (profil en mémoire). Ne pas utiliser `--persistent`, `--profile`, ni `attach` sur le navigateur personnel de l'utilisateur sans demande explicite : ces options donnent accès à ses cookies et à son stockage local.
- `-s=<nom>` permet de séparer plusieurs sessions ; `playwright-cli close-all` les ferme toutes.
- Pour limiter les domaines joignables : `network.allowedOrigins` / `blockedOrigins` dans `.playwright/cli.config.json`.
