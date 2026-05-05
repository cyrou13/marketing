# Skills Claude Code — Avicenna Marketing

Skills disponibles automatiquement quand Claude Code est lancé à la racine du repo.

## Index

| Skill | Quand l'invoquer |
|-------|-------------------|
| **linkedin-post** | Post LinkedIn structurel (annonce, lancement, milestone, prise de position). Pour une réaction news rapide, préférer `prompts/linkedin-reactive-news.md`. |
| **blog-article** | Article 1000-2500 mots — clinical, technical, regulatory/scientific update, strategic, ou SEO pillar. |
| **case-study** | Étude de cas hôpital — sensible, ne démarre que si prérequis collecte + accords signés. |
| **regulatory-comm** | Communiqué presse de clearance, IFU update, statement régulatoire. Refuse de travailler sans document officiel + claims pré-validés RA. |
| **newsletter** | Newsletter mensuelle complète ou section autonome. |

## Comment invoquer

Trois manières :

1. **Implicite** : décrire la tâche — Claude détecte le bon skill via la `description` du frontmatter.
   > *"Drafte un post LinkedIn corporate annonçant que nous serons à RSNA 2026."*
2. **Explicite** : nommer le skill.
   > *"Use the linkedin-post skill pour drafter…"*
3. **Via workflow** : un workflow dans `workflows/` chaîne plusieurs skills.
   > *"Exécute le workflow new-clearance avec les inputs suivants…"*

## Format

Chaque skill est dans son dossier `.claude/skills/<skill-name>/SKILL.md` avec frontmatter :

```yaml
---
name: skill-name
description: Quand l'invoquer (utilisé par Claude pour la détection)
---
```

## Dépendances communes

Tous les skills lisent automatiquement :
- `brand/voice.md`
- `brand/regulatory-guard.md`
- `brand/audiences.md`
- `brand/glossary.md`
- `brand/proof-points.md`

**Si le brand pack est encore vide** (champs `[À COMPLÉTER]`), les skills le signalent et refusent de produire un draft à l'aveugle sur les points critiques.

## Process de validation

Tous les drafts générés passent par revue humaine avant publication. Le niveau de revue dépend du type de contenu — voir `brand/regulatory-guard.md` §7.

## Évolution

Pour ajouter un skill :
1. Créer `.claude/skills/<nouveau-skill>/SKILL.md` avec frontmatter `name` + `description`
2. Documenter ici
3. Si le skill est utilisé par un workflow, mettre à jour le workflow

Tag la version (commit) et notez l'impact attendu.
