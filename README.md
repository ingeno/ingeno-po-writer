# Ingeno PO Writer

Plugin Claude Code dont le skill rédige des epics, des user stories et des découpages d'epics (story maps) selon les pratiques d'Ingeno. Il fonctionne en français et en anglais.

## Ce que le skill fait

- Rédiger une epic ou une user story à partir de notes brutes ou de zéro.
- Écrire les critères d'acceptation d'un ticket.
- Découper une epic en stories ou préparer un sprint.
- Questionner l'auteur sur une epic ou une story (mode « grill me ») pour en trouver les angles morts.

## Contenu

- `.claude-plugin/plugin.json` : le manifeste du plugin.
- `skills/ingeno-po-writer/SKILL.md` : les instructions du skill.
- `skills/ingeno-po-writer/references/epic-template.md` : le gabarit d'epic.

## Installation

Avec Claude Code, depuis la marketplace d'Ingeno ([ingeno/ingeno-claude-marketplace](https://github.com/ingeno/ingeno-claude-marketplace)) :

```
/plugin marketplace add ingeno/ingeno-claude-marketplace
/plugin install ingeno-po-writer@ingeno
```

Dans l'app Claude, ouvre les paramètres des skills et téléverse le dossier `skills/ingeno-po-writer` sous forme de fichier ZIP.

Une nouvelle version n'atteint l'équipe qu'après une PR dans la marketplace qui avance le `sha` épinglé de ce plugin.
