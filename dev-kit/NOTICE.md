# NOTICE

Ce plugin assemble des travaux tiers, tous sous licence MIT. Copie des licences dans `licenses/`.

| Contenu | Source | Licence |
|---|---|---|
| `skills/design-taste-frontend` (règles dans `references/taste-full.md`) | https://github.com/Leonxlnx/taste-skill (v2 expérimentale) | MIT © 2026 Leonxlnx |
| `skills/web-design-guidelines` (règles dans `references/rules.md`, copie figée du 2026-10-06) | https://github.com/vercel-labs/web-interface-guidelines | MIT © 2025 Vercel Labs |
| 25 skills, 9 commandes, 4 agents, 7 checklists | https://github.com/addyosmani/agent-skills (v0.6.12) | MIT © 2025 Addy Osmani |
| 6 skills `ponytail*` | https://github.com/DietrichGebert/ponytail (v4.13.0) | MIT © 2026 DietrichGebert |
| `skills/image-to-code` | adaptation condensée de `image-to-code-skill` (Leonxlnx/taste-skill, MIT), enrichie d'après VoltAgent/awesome-design-md (MIT, format DESIGN.md) et microsoft/playwright-cli (Apache-2.0, commandes citées depuis son README) | MIT / Apache-2.0 |

## Modifications

- Les préfixes `agent-skills:` et `ponytail:` dans les commandes et skills ont été remplacés par `dev-kit:` pour correspondre au nom de ce plugin.
- `skills/idea-refine/SKILL.md` : le chemin du script utilise `${CLAUDE_SKILL_DIR}` au lieu d'un chemin relatif à la racine du dépôt.
- `image-to-code` : sans génération d'image obligatoire (non disponible dans ce contexte) ; ajout du catalogue DESIGN.md et de la recette playwright-cli.
- Ajout de la commande `commands/audit-ui.md`.

## Exclus volontairement

- **Hooks de ponytail** (`SessionStart`, `SubagentStart`, `UserPromptSubmit`) : exécutent du code Node à chaque session, écrivent des fichiers d'état hors du plugin et proposent de modifier `settings.json` (statusLine).
- **Hooks d'agent-skills** (`sdd-cache`, `simplify-ignore`) : optionnels et non activés par le plugin d'origine.
- **graphify** (Graphify-Labs/graphify) : outil Python (PyPI `graphifyy`), pas un skill autonome. Son skill peut lancer `pip install` à l'exécution et se déclenche sur « toute question sur un codebase ».
- **OmniRoute** (diegosouzapw/OmniRoute) : passerelle auto-hébergée vers des centaines de fournisseurs d'IA, ce n'est pas un composant de plugin.
