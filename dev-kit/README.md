# Dev Kit

Un plugin qui regroupe 34 skills, 10 commandes et 4 agents pour le développement, assemblés à partir de dépôts open source. Il ne contient ni hooks ni connecteurs : uniquement des fichiers Markdown (et un petit script shell inoffensif, `skills/idea-refine/scripts/idea-refine.sh`, qui crée un dossier `docs/ideas`).

## Contenu

**Frontend**
- `design-taste-frontend` : règles anti-« slop » pour landing pages, portfolios et redesigns (d'après Leonxlnx/taste-skill, v2 expérimentale).
- `web-design-guidelines` : audit d'interface selon les Web Interface Guidelines de Vercel, règles embarquées. Commande `/dev-kit:audit-ui <fichier>`.
- `image-to-code` : construire à partir d'une capture, d'un site ou d'un DESIGN.md, puis vérifier avec des captures (playwright-cli si disponible).

**Cycle d'ingénierie** (d'après addyosmani/agent-skills) : 25 skills (spec, plan, TDD, revue de code, sécurité, performance, CI/CD, etc.), les commandes `/spec`, `/plan`, `/build`, `/test`, `/constraints`, `/review`, `/webperf`, `/code-simplify`, `/ship`, 4 agents (code-reviewer, test-engineer, security-auditor, web-performance-auditor) et 7 checklists dans `references/`.

**Code minimal** (d'après DietrichGebert/ponytail) : 6 skills (`ponytail`, `-review`, `-audit`, `-debt`, `-gain`, `-help`). Le skill principal pousse la solution la plus courte qui fonctionne et se déclenche sur toute tâche de code ; pour le désactiver, supprimer `skills/ponytail/`. Les hooks de ponytail ne sont pas inclus : le mode n'est donc pas réinjecté à chaque tour.

## Utilisation

- claude.ai : Customize > Plugins > Add > Upload plugin, puis choisir le ZIP. Demander ensuite à Claude quels skills il a depuis les plugins.
- Claude Code : `claude --plugin-dir ./dev-kit`, puis `/dev-kit:audit-ui src/`.
- Les commandes se lancent par leur nom dans Cowork et Claude Code ; dans le chat, elles se chargent comme des skills.
- Les agents ne se chargent que dans Cowork et Claude Code.

## Données

Le plugin n'envoie rien nulle part et ne stocke rien : il n'a ni connecteur, ni hook, ni serveur MCP. Seul `image-to-code` mentionne des outils externes (`playwright-cli`, `web_fetch` vers getdesign.md) et ne les utilise que si tu le demandes.

## Sources et licences

Tout le contenu est sous licence MIT. Détails, modifications apportées et ce qui a été volontairement exclu : `NOTICE.md`. Textes de licence : `licenses/`.
