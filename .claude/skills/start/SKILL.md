---
name: start
description: Démarrage du plugin avicenna-marketing — scaffolde le workspace (brand pack éditable, knowledge bundle pour claude.ai, dossier outputs) la première fois, puis audite l'état du brand pack et liste les skills disponibles. À invoquer explicitement via /avicenna-marketing:start après installation du plugin.
disable-model-invocation: true
---

# Skill — Démarrage Avicenna Marketing

Tu accompagnes l'utilisateur dans la mise en route du plugin avicenna-marketing. Argument éventuel : `$ARGUMENTS` (peut contenir `--force` pour ré-écraser un workspace existant, ou un canal cible : `linkedin`, `blog`, `case-study`, `regulatory`, `newsletter`).

Procède dans l'ordre, en restant concis. **Ne JAMAIS produire de draft marketing pendant cette skill** — c'est de l'onboarding/scaffolding, pas de la production.

## Phase 0 — Détection du mode

Vérifier la présence de `./brand/` dans le cwd via Bash (`test -d brand && echo exists`) :

- **Workspace vierge** (`./brand/` n'existe pas) → **Mode SCAFFOLD** (Phase 1 + 2 + 3 + 5)
- **Workspace déjà setup** (`./brand/` existe) → **Mode AUDIT** (Phase 3 + 5 uniquement)
- **`--force` dans `$ARGUMENTS`** → **Mode SCAFFOLD** quoi qu'il en soit, mais demander confirmation avant d'écraser (lister les fichiers existants qui seront remplacés)

Annoncer le mode détecté à l'utilisateur en une phrase.

## Phase 1 — Scaffold du brand pack (mode SCAFFOLD)

Copier les 5 templates du brand pack depuis le plugin vers le cwd. Utiliser la variable `${CLAUDE_PLUGIN_ROOT}` pour pointer le plugin installé :

```bash
mkdir -p ./brand
cp --update=none "${CLAUDE_PLUGIN_ROOT}/brand/voice.md" ./brand/
cp --update=none "${CLAUDE_PLUGIN_ROOT}/brand/regulatory-guard.md" ./brand/
cp --update=none "${CLAUDE_PLUGIN_ROOT}/brand/glossary.md" ./brand/
cp --update=none "${CLAUDE_PLUGIN_ROOT}/brand/audiences.md" ./brand/
cp --update=none "${CLAUDE_PLUGIN_ROOT}/brand/proof-points.md" ./brand/
```

Le flag `--update=none` (équivalent moderne de `-n`, sans warning) protège un éventuel travail en cours. En mode `--force` confirmé, retirer `--update=none`. Fallback sur les anciennes versions de coreutils (BSD/macOS) : `[ -f ./brand/voice.md ] || cp "${CLAUDE_PLUGIN_ROOT}/brand/voice.md" ./brand/`.

Si `${CLAUDE_PLUGIN_ROOT}` n'est pas résolu dans l'environnement, fallback : demander à l'utilisateur le path de son plugin installé (`~/.claude/plugins/cache/<marketplace>/<plugin>/<version>/`) ou utiliser Read+Write pour copier fichier par fichier en lisant depuis le path absolu du plugin.

Créer aussi le dossier outputs et un .gitignore minimal :

```bash
mkdir -p ./outputs && touch ./outputs/.gitkeep
```

Si `.gitignore` n'existe pas dans le cwd, créer un .gitignore minimal qui ignore `outputs/` (les drafts ne sont pas source de vérité).

## Phase 2 — Scaffold du knowledge bundle pour claude.ai (mode SCAFFOLD)

Créer un dossier `./_claude-ai-knowledge/` avec les fichiers prêts à uploader sur claude.ai/projects :

```bash
mkdir -p ./_claude-ai-knowledge
cp "${CLAUDE_PLUGIN_ROOT}/brand/voice.md" ./_claude-ai-knowledge/
cp "${CLAUDE_PLUGIN_ROOT}/brand/regulatory-guard.md" ./_claude-ai-knowledge/
cp "${CLAUDE_PLUGIN_ROOT}/brand/glossary.md" ./_claude-ai-knowledge/
cp "${CLAUDE_PLUGIN_ROOT}/brand/audiences.md" ./_claude-ai-knowledge/
cp "${CLAUDE_PLUGIN_ROOT}/brand/proof-points.md" ./_claude-ai-knowledge/
```

Puis générer `./_claude-ai-knowledge/UPLOAD_CHECKLIST.md` via Write avec ce contenu :

```markdown
# Upload Checklist — Avicenna Marketing Studio (claude.ai Project)

## Étapes manuelles (claude.ai web)

- [ ] Aller sur claude.ai → Projects → New Project
- [ ] Nom : **Avicenna Marketing Studio**
- [ ] Description : *Création de contenu marketing aligné voix de marque, contraintes MDR/FDA, positionnement Avicenna.*
- [ ] Coller le contenu de `CLAUDE_PROJECT_SYSTEM_PROMPT.md` (à la racine du repo plugin) dans les custom instructions du Project
- [ ] Uploader dans le project knowledge les fichiers ci-dessous (drag-and-drop depuis ce dossier)

## Fichiers à uploader

- [ ] voice.md
- [ ] regulatory-guard.md
- [ ] glossary.md
- [ ] audiences.md
- [ ] proof-points.md

## À ajouter manuellement après remplissage du brand pack

- [ ] 3-5 meilleurs posts LinkedIn passés (à mettre dans `references/past-content/linkedin-best/`)
- [ ] 3-5 meilleurs articles blog passés (`references/past-content/blog-best/`)
- [ ] 2-3 papers scientifiques clés (`references/papers/`)
- [ ] `references/competitors/landscape.md`

Limite recommandée : 20 fichiers max dans le knowledge claude.ai. Sélectionner, pas tout uploader.

## Note

Ces fichiers sont une **copie figée** au moment du scaffold. Si tu édites `./brand/*.md` après remplissage, **re-uploade** les versions à jour dans le claude.ai Project.
```

## Phase 3 — Audit du brand pack (toujours, en mode SCAFFOLD comme AUDIT)

Lire les 5 fichiers `./brand/*.md` via Read et signaler pour chacun :

- Combien de marqueurs `[À COMPLÉTER]`, `[TODO]`, `<remplir>`, `[à valider]`, `[XX]` sont encore présents
- Si **plus de 30 %** du fichier est en placeholder → drapeau rouge
- Si `regulatory-guard.md` est en grande partie vide → **bloquant absolu** pour toute production (le signaler en gras, expliquer pourquoi : sans claims validés Quality + Reg Affairs, aucune skill ne peut produire un draft fiable)

Restituer un tableau bref :

| Fichier | Placeholders restants | État | Bloque |
|---|---|---|---|
| voice.md | N | ✅/⚠️/❌ | — |
| regulatory-guard.md | N | ✅/⚠️/❌ | toutes les skills si ❌ |
| glossary.md | N | ✅/⚠️/❌ | skills techniques |
| audiences.md | N | ✅/⚠️/❌ | targeting persona |
| proof-points.md | N | ✅/⚠️/❌ | tout claim chiffré |

## Phase 4 — (réservée)

Numéro libre pour évolution future (workflow setup, etc.).

## Phase 5 — Tour des skills et next steps

Lister les 5 skills de production avec une phrase chacune :

- `linkedin-post` — post LinkedIn structurel (annonce, milestone, prise de position)
- `blog-article` — article 1000-2500 mots (clinical, technical, regulatory, strategic, SEO pillar)
- `case-study` — étude de cas hôpital (prérequis stricts : consentement, sign-off Quality + Legal)
- `regulatory-comm` — communiqué de clearance FDA/CE, update IFU
- `newsletter` — newsletter mensuelle ou section autonome

Invocation : par description naturelle (auto-détection) ou explicite via `/avicenna-marketing:<nom-skill>`.

Si mode SCAFFOLD : conclure par les 3 next steps concrets :

1. Atelier brand pack (2-4h avec marketeur⋅euse) pour remplir les `[À COMPLÉTER]` de `./brand/*.md` — **priorité absolue à `regulatory-guard.md`** (validation Quality + Reg Affairs).
2. Setup claude.ai Project en suivant `./_claude-ai-knowledge/UPLOAD_CHECKLIST.md`.
3. Premier test Claude Code : *"Récapitule la voix de marque Avicenna et liste les 5 mots interdits du regulatory-guard."* (vérifie que le brand pack est correctement chargé).

Si mode AUDIT : conclure par un seul next step contextualisé selon l'état du brand pack :

- Si tout est ✅ : *"Brand pack OK. Tu peux invoquer une skill de production."*
- Si regulatory-guard est ❌ : *"Bloquer toute production tant que regulatory-guard.md n'est pas validé."*
- Sinon : pointer le fichier le plus critique à compléter en premier.

## Rappels critiques (toujours en clôture, 3 lignes max)

- Aucun chiffre non sourcé dans un draft publié (source = ligne dans `proof-points.md` ou paper avec DOI).
- AKILA = R&D, jamais présenté comme produit clinique.
- Tout draft passe par revue humaine selon `regulatory-guard.md` §7.

## Anti-patterns à éviter

- Ne PAS produire de draft marketing pendant cette skill.
- Ne PAS écraser silencieusement des fichiers existants en mode SCAFFOLD — utiliser `cp -n` ou demander confirmation.
- Ne PAS reformuler toute la stratégie marketing — rester sur l'opérationnel "comment je démarre / où j'en suis".
- Ne PAS lister les workflows multi-étapes (`new-clearance`, `new-paper`, `case-study-pipeline`) sauf si l'utilisateur les demande explicitement.
