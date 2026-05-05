# Avicenna Marketing — briefing Claude Code

Ce repo est un pack de production de contenu marketing pour Avicenna.ai.
Il fonctionne avec **Claude Code** (skills + workflows) et **Claude.ai Projects** (rédaction quotidienne).

## Contexte

Avicenna.ai est une medtech européenne en AI radiologique CT (triage, analyse vasculaire, auto-reporting). Audiences principales : radiologues, chefs de service, CIO/DSI hospitaliers, investisseurs, talents tech medical.

## Avant toute production de contenu

Charger systématiquement le brand pack :
- `brand/voice.md` — voix de marque par canal
- `brand/regulatory-guard.md` — **CRITIQUE** : mots interdits MDR/FDA, claims autorisés
- `brand/glossary.md` — vocabulaire produit
- `brand/audiences.md` — 5 personas + matrice canal × audience
- `brand/proof-points.md` — chiffres substantiables

Si un fichier du brand pack contient encore des `[À COMPLÉTER]` sur des points critiques pour la tâche, **ne pas produire de draft à l'aveugle** : signaler les manques et demander.

## Règles non-négociables

1. **Aucun chiffre non sourcé** dans un contenu publié. Source = ligne dans `proof-points.md` ou paper cité avec DOI.
2. **Aucun claim hors `regulatory-guard.md`**. Tout claim de performance produit doit être traçable à un document réglementaire ou un paper publié.
3. **AKILA est R&D**, jamais présenté comme produit clinique.
4. **Aucune comparaison nominative** dénigrant un concurrent.
5. **Aucune donnée patient identifiable**, jamais.
6. **Tout draft passe par revue humaine** avant publication. Niveau de revue = `regulatory-guard.md` §7.

## Skills disponibles (auto-détectés)

| Skill | Usage |
|-------|-------|
| `linkedin-post` | Post LinkedIn structurel (annonce, milestone, prise de position) |
| `blog-article` | Article 1000-2500 mots — clinical, technical, regulatory, strategic, SEO pillar |
| `case-study` | Étude de cas hôpital — sensible, prérequis stricts |
| `regulatory-comm` | Communiqué presse clearance, IFU update, statement régulatoire |
| `newsletter` | Newsletter mensuelle ou section autonome |

Voir `.claude/skills/README.md` pour détails.

## Workflows multi-étapes

Dans `workflows/` :
- `new-clearance.md` — pipeline complet pour annoncer une clearance FDA/CE
- `new-paper.md` — pipeline pour publication scientifique
- `case-study-pipeline.md` — interview client → pack multi-canal

Invocation : *"Exécute le workflow new-clearance avec les inputs suivants…"*

## Prompts ponctuels

Dans `prompts/` — copier-coller pour cas qui ne méritent pas un Skill complet (réaction news, recap congrès, recrutement, etc.).

## Comportement attendu

- **Concis, factuel, sans hype.** Pas de "révolutionner", "disruptive", "game changer".
- **Phrases courtes à moyennes** (15-25 mots).
- **Pas d'émojis** sauf demande explicite. **Jamais** sur la voix CEO Cyril.
- **Pas de listes à puces** sauf vraie énumération.
- **Avant de rédiger**, poser 2-3 questions de clarification si manquent : objectif business, audience, angle, claims spécifiques, deadline. Sauf si déjà fournis.
- **Langue par défaut** : français pour contenu institutionnel France et conversations équipe ; anglais pour international, US, investisseurs anglophones. Demander en cas de doute.

## Outputs

Les drafts vont dans `outputs/YYYY-MM-DD-<type>-<short-name>/`.
Ce dossier est **gitignoré** (drafts ≠ source de vérité).

## Confidentialité

- Roadmap confidentielle : `brand/roadmap-confidential.md` (gitignoré). Ne jamais y faire référence dans un contenu externe.
- Accords clients : dans `references/case-studies/*-consent.pdf` (gitignorés).
- Si une demande implique de divulguer un élément potentiellement confidentiel, demander confirmation avant de produire.

## Ce que tu ne fais pas

- Pas de modification du brand pack sans validation explicite (c'est la source de vérité, modifs = PR + review).
- Pas d'invention de chiffre, citation client, ou performance clinique.
- Pas de claim de produit sur indication non couverte par sa clearance CE/FDA selon la juridiction du contenu.
- Pas de publication de contenu — on produit des drafts, l'humain publie.
