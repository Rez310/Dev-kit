---
name: web-design-guidelines
description: Review UI code against Vercel's Web Interface Guidelines (accessibility, forms, focus, animation, typography, performance). Use for "review my UI", "audit design", "check accessibility", "review UX".
---

# web-design-guidelines

Audit de code d'interface selon les Web Interface Guidelines de Vercel (MIT). Les règles sont **embarquées** dans `references/rules.md` : ce skill ne télécharge rien au moment de l'audit.

## Workflow

1. Si l'utilisateur n'a pas indiqué de fichiers ou de motif, demander lesquels examiner (une seule question).
2. Lire les fichiers concernés.
3. Lire `references/rules.md` en entier, puis vérifier chaque fichier contre toutes les règles.
4. Répondre selon le format de sortie défini à la fin de `references/rules.md` : regroupé par fichier, une ligne par problème au format `fichier:ligne - problème`, `✓ pass` si rien à signaler, pas de préambule, pas d'explication sauf si le correctif n'est pas évident.

## Notes

- Les règles datent du 2026-10-06 (copie figée). Si l'utilisateur veut la dernière version, la source est `https://raw.githubusercontent.com/vercel-labs/web-interface-guidelines/main/command.md` ; relire les changements avant de remplacer `references/rules.md`.
- Pour une réponse en français, garder les citations de règles en anglais et formuler le problème en français, toujours en style télégraphique.
- Source et licence : `references/LICENSE-vercel.txt`.
