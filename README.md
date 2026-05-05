# Avicenna Marketing — pack contenu

Repository de production de contenu marketing pour Avicenna.AI, structuré
pour fonctionner avec **Claude Code**, **Claude.ai Projects**, et un
catalogue de prompts réutilisables.

Conçu pour : posts LinkedIn, articles blog, études de cas hôpitaux,
communiqués réglementaires (FDA / CE), newsletters.

---

## Structure

```
avicenna-marketing/
├── brand/                    # SOURCE DE VÉRITÉ — à remplir en priorité
│   ├── voice.md              # voix de marque
│   ├── glossary.md           # vocabulaire produit + métier
│   ├── regulatory-guard.md   # claims interdits / autorisés (CRITIQUE)
│   ├── audiences.md          # 5 personas + matrice canal × audience
│   └── proof-points.md       # bibliothèque centralisée des chiffres
├── references/
│   ├── papers/               # publications scientifiques
│   ├── past-content/         # contenus passés qui ont bien marché
│   └── competitors/          # veille concurrentielle
├── prompts/                  # prompts ponctuels (non-skills)
│   ├── linkedin-reactive-news.md
│   ├── conference-participation.md
│   ├── hire-announcement.md
│   ├── blog-seo-pillar.md
│   └── milestone-celebration.md
├── .claude/skills/           # skills Claude Code
│   ├── linkedin-post/
│   ├── blog-article/
│   ├── case-study/
│   ├── regulatory-comm/
│   └── newsletter/
├── workflows/                # pipelines multi-agents (BMAD-style)
│   ├── new-clearance.md
│   ├── new-paper.md
│   └── case-study-pipeline.md
├── outputs/                  # contenu généré, daté
└── CLAUDE_PROJECT_SYSTEM_PROMPT.md  # à coller dans claude.ai
```

---

## Setup pour un nouveau collaborateur (clone sur une nouvelle machine)

### Prérequis

- **Git** + un compte GitHub avec accès au repo `cyrou13/marketing`
- **Claude Code** installé : https://claude.com/claude-code
- (Optionnel mais recommandé) accès au Project Claude.ai « Avicenna Marketing Studio »

### Installation

```bash
# 1. Cloner le repo
git clone git@github.com:cyrou13/marketing.git avicenna-marketing
cd avicenna-marketing

# 2. Lancer Claude Code à la racine
claude
```

Claude Code détecte automatiquement :
- Le `CLAUDE.md` racine (briefing + règles non-négociables)
- Les skills dans `.claude/skills/` (linkedin-post, blog-article, case-study, regulatory-comm, newsletter)
- Le brand pack dans `brand/`

### Premier message recommandé pour vérifier l'install

```
Liste les skills disponibles et explique ce que chacun fait.
```

Puis un test simple :

```
Drafte un post LinkedIn corporate annonçant que nous serons à RSNA 2026.
Stand prévu n°XXXX, on présentera la roadmap CT Perfusion.
Use the linkedin-post skill.
```

Si Claude pose des questions de clarification AVANT de rédiger, l'install est OK.

### Settings locaux

`.claude/settings.local.json` est gitignoré : chacun configure ses permissions / hooks à sa guise sans polluer les autres.

### Mises à jour

```bash
git pull
```

Le brand pack est versionné — toute modif passe par PR + review (cf. section *Maintenance*).

---

## Démarrage en 4 étapes

### Étape 1 — Remplir le brand pack (CRITIQUE, 2-4 heures avec ta marketeuse)

Sans ça, tout le reste génère de la soupe générique. À faire ensemble en
atelier :

1. `brand/voice.md` — la voix de marque
2. `brand/regulatory-guard.md` — **à valider avec Quality + Reg Affairs**
3. `brand/glossary.md` — un terme à la fois, avec les 3 niveaux d'audience
4. `brand/audiences.md` — relire et adapter les personas
5. `brand/proof-points.md` — collecter tous les chiffres citables

Tant que ces fichiers contiennent des « à compléter » sur des points
critiques, les skills le signaleront et ne produiront pas de drafts à
l'aveugle.

### Étape 2 — Setup Claude.ai Project (15 min)

Pour le travail quotidien fluide de ta marketeuse :

1. Créer un Project nommé « Avicenna Marketing Studio » sur claude.ai
2. Coller le contenu de `CLAUDE_PROJECT_SYSTEM_PROMPT.md` dans les
   custom instructions
3. Uploader dans le project knowledge :
   - tous les fichiers de `brand/`
   - 3-5 meilleurs `references/past-content/linkedin-best/`
   - 3-5 meilleurs `references/past-content/blog-best/`
   - 2-3 papers clés de `references/papers/`
   - `references/competitors/landscape.md`

Limite de 20 fichiers indicative. Sélectionner, pas tout uploader.

### Étape 3 — Setup Claude Code (30 min, une fois pour toute l'équipe)

```bash
# Cloner le repo localement
git clone <repo-url> avicenna-marketing
cd avicenna-marketing

# Lancer Claude Code à la racine
claude
```

Claude Code détecte automatiquement les skills dans `.claude/skills/`.
Premier message recommandé pour vérifier :

```
Liste les skills disponibles et explique ce que chacun fait.
```

### Étape 4 — Premier essai

Test simple avant un vrai workflow :

```
Drafte un post LinkedIn corporate annonçant que nous serons à RSNA 2026.
Stand prévu n°XXXX, on présentera la roadmap CT Perfusion. Use the
linkedin-post skill.
```

Si la sortie te paraît off, c'est probablement que le brand pack est
encore trop vide. Itérer.

---

## Quand utiliser quoi

| Tâche | Outil approprié |
|---|---|
| Drafter rapidement un post sans cérémonie | Claude.ai Project |
| Drafter un post avec contraintes formelles strictes | Claude Code + skill |
| Article blog complet | Claude Code + skill blog-article |
| Cas clinique hôpital | Claude Code + skill case-study (sensible) |
| Pack complet pour une clearance | Claude Code + workflow new-clearance |
| Réagir à une news en 30 min | prompts/linkedin-reactive-news.md |
| Pack congrès | prompts/conference-participation.md |
| Quelque chose qui ne rentre dans aucune case | Claude.ai Project |

Ma reco : **80 % du temps quotidien sur Claude.ai Project**, **20 % sur
Claude Code** pour les pièces structurantes.

---

## Règles non-négociables (rappel)

1. **Aucun chiffre non sourcé** dans un contenu publié. Source = ligne
   dans `proof-points.md`.

2. **Aucun claim hors `regulatory-guard.md`** dans un contenu publié.
   Tout claim de performance produit doit être traçable à un document
   réglementaire ou un paper publié.

3. **AKILA est R&D**, jamais présenté comme produit clinique.

4. **Aucune comparaison nominative** dénigrant un concurrent.

5. **Aucune donnée patient identifiable**, jamais.

6. **Tout draft généré passe par revue humaine** avant publication. Le
   niveau de revue dépend du type de contenu — voir
   `brand/regulatory-guard.md` §7.

---

## Maintenance

| Fichier | Fréquence de mise à jour |
|---|---|
| `brand/voice.md` | Trimestrielle |
| `brand/regulatory-guard.md` | À chaque nouvelle clearance ou changement IFU |
| `brand/glossary.md` | À chaque nouveau produit ou changement de positionnement |
| `brand/audiences.md` | Annuelle ou si pivot stratégique |
| `brand/proof-points.md` | **Mensuelle** (chiffres traction) |
| `references/competitors/landscape.md` | Trimestrielle |
| `references/past-content/` | Quand un nouveau contenu performe bien |

---

## Versioning

- Le brand pack est versionné en Git. Toute modif passe par PR + review.
- Les workflows et skills aussi : si tu modifies un skill, tag la version
  et note l'impact attendu.
- Les outputs dans `outputs/` ne sont **pas versionnés** par défaut (à
  ajouter au `.gitignore`) sauf si vous voulez l'historique pour audit.

## Évolutions probables

- Migration vers Cortex quand le module Marketing sera prêt (le brand
  pack devient une table Supabase, les skills restent en fichiers).
- Intégration avec votre outil d'envoi newsletter (HubSpot/Brevo/...) via
  MCP server.
- Intégration LinkedIn API pour publication assistée (avec validation
  humaine systématique).
- Workflow inverse : analyser un contenu publié + ses perfs, et nourrir
  `references/past-content/`.

---

## Contact

Pour toute question sur ce repo : Cyril Di Grandi (Avicenna).
