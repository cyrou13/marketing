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

## Setup pour un nouveau collaborateur

Deux profils d'usage :

| Profil | Installation | Pour qui |
|--------|--------------|----------|
| **A — Consommateur de contenu** | Plugin Claude Code via marketplace | Marketing, sales, équipe contenu (la plupart) |
| **B — Mainteneur du brand pack** | Clone du repo (édition `brand/`, skills) | Tech + responsable marketing (1-2 personnes) |

### Prérequis communs

- **Claude Code** installé : https://claude.com/claude-code
- Compte GitHub avec accès au repo `cyrou13/marketing` (privé)
- (Optionnel) accès au Project Claude.ai « Avicenna Marketing Studio »

### Profil A — Installer le plugin (5 min, une fois)

Dans Claude Code :

```
/plugin marketplace add cyrou13/marketing
/plugin install avicenna-marketing@avicenna-marketing
```

Puis **redémarrer Claude Code** (l'install demande un restart pour activer les skills).

Les 6 skills (`linkedin-post`, `blog-article`, `case-study`, `regulatory-comm`, `newsletter`, `start`) sont alors disponibles dans toutes tes sessions Claude Code, partout sur ta machine.

Pour mettre à jour quand le plugin évolue :

```
/plugin marketplace update avicenna-marketing
/plugin update avicenna-marketing
```
Puis restart.

### Profil B — Cloner le repo (pour éditer le brand pack et les skills)

```bash
git clone git@github.com:cyrou13/marketing.git avicenna-marketing
cd avicenna-marketing
claude
```

Claude Code détecte automatiquement :
- Le `CLAUDE.md` racine (briefing + règles non-négociables)
- Les skills dans `.claude/skills/`
- Le brand pack dans `brand/`
- Les workflows dans `workflows/`
- Les prompts dans `prompts/`

Modifications éventuelles → PR + review (le brand pack est source de vérité, cf. section *Maintenance*).

### Settings locaux

`.claude/settings.local.json` est gitignoré : chacun configure ses permissions / hooks à sa guise sans polluer les autres.

---

## Démarrage en 4 étapes

### Étape 1 — Installer le plugin Claude Code (5 min)

Voir section *Setup pour un nouveau collaborateur > Profil A* ci-dessus :
`/plugin marketplace add cyrou13/marketing` puis
`/plugin install avicenna-marketing@avicenna-marketing` puis restart.

### Étape 2 — Scaffolder un workspace (1 min)

Créer un dossier vide pour bosser ton contenu marketing, puis y lancer Claude Code :

```bash
mkdir ~/avicenna-content-2026
cd ~/avicenna-content-2026
claude
```

Puis taper **exactement** la commande suivante (sans autocomplete — la skill est volontairement masquée de la liste `/` pour ne pas être déclenchée par erreur) :

```
/avicenna-marketing:start
```

La skill détecte que le workspace est vide → mode SCAFFOLD :
- copie les 5 templates `brand/*.md` dans `./brand/` (éditables localement)
- crée `./_claude-ai-knowledge/` avec `UPLOAD_CHECKLIST.md` (à utiliser pour l'Étape 4)
- crée `./outputs/.gitkeep` (où les drafts iront)
- audite l'état du brand pack et signale ce qui bloque

Aux invocations suivantes (workspace déjà setup), la même commande passe en mode AUDIT seul — utile pour faire le point sur l'état du brand pack.

### Étape 3 — Remplir le brand pack (CRITIQUE, 2-4 heures avec ta marketeuse)

Sans ça, tout le reste génère de la soupe générique. À faire ensemble en atelier, dans l'ordre de priorité signalé par `/avicenna-marketing:start` :

1. `brand/regulatory-guard.md` — **priorité absolue**, à valider avec Quality + Reg Affairs (bloque toutes les autres skills tant qu'il est vide)
2. `brand/voice.md` — la voix de marque par canal
3. `brand/audiences.md` — relire et adapter les 5 personas
4. `brand/proof-points.md` — collecter tous les chiffres citables avec source
5. `brand/glossary.md` — un terme à la fois, avec les 3 niveaux d'audience

Tant que ces fichiers contiennent des `[À COMPLÉTER]` sur des points critiques, les skills le signaleront et ne produiront pas de drafts à l'aveugle.

### Étape 4 — (Optionnel) Setup Claude.ai Project pour le travail quotidien

Suivre la checklist auto-générée dans `./_claude-ai-knowledge/UPLOAD_CHECKLIST.md`. En résumé :

1. claude.ai → Projects → New Project nommé « Avicenna Marketing Studio »
2. Coller le contenu de `CLAUDE_PROJECT_SYSTEM_PROMPT.md` dans les custom instructions
3. Drag-and-drop les fichiers de `./_claude-ai-knowledge/` dans le knowledge du Project
4. Ajouter manuellement : 3-5 meilleurs posts/articles passés, 2-3 papers clés, `competitors/landscape.md` (limite 20 fichiers indicative)

Le claude.ai Project est utile pour le draft rapide sans cérémonie ; les skills Claude Code restent l'outil de référence pour les contenus structurants (case-study, regulatory-comm, blog pillar).

### Étape 5 — Premier essai

Test simple avant un vrai workflow :

```
Drafte un post LinkedIn corporate annonçant que nous serons à RSNA 2026.
Stand prévu n°XXXX, on présentera la roadmap CT Perfusion.
```

Si Claude pose 2-3 questions de clarification AVANT de rédiger, l'install est OK. Si la sortie te paraît off, c'est probablement que le brand pack est encore trop vide — relancer `/avicenna-marketing:start` pour l'audit.

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
