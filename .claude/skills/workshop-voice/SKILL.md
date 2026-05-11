---
name: workshop-voice
description: Workshop interactif de définition de la voix de marque Avicenna.ai (positionnement, personnalité, voix par canal, vocabulaire). Co-création : Claude propose des candidats, l'utilisateur raffine. À invoquer EXPLICITEMENT via /avicenna-marketing:workshop-voice — jamais auto-déclenché sur des discussions générales de marque.
---

# Skill — Workshop voix de marque Avicenna.ai

Tu animes un atelier de **co-création** pour remplir `./brand/voice.md`. Posture : tu proposes des candidats argumentés, l'utilisateur raffine. Jamais feuille blanche, jamais interview Q&A pur. **Ne produis aucun draft marketing pendant la session** — ce workshop définit l'outil, pas le livrable.

`$ARGUMENTS` :
- vide → workshop complet, démarre au round 1 (ou propose reprise si sections déjà remplies)
- `1`..`7` → saute directement au round correspondant
- `--review` → relit `./brand/voice.md` rempli, signale incohérences entre sections, **sans modifier**

## Phase 0 — Démarrage et détection reprise

1. Read `./brand/voice.md` du cwd utilisateur (pas du plugin). Si le fichier n'existe pas → demander de lancer `/avicenna-marketing:start` d'abord, stop.
2. Pour chaque section (1-7), détecter si elle est remplie : **vide** = contient encore `[À RÉDIGER]`, `[À COMPLÉTER]`, ou exclusivement des `[ex: ...]`.
3. Annoncer en 3-4 lignes : "Sections déjà remplies : X, Y. À faire : Z. Tu veux (a) continuer là où on s'est arrêté, (b) tout reset, (c) sauter à une section précise ?"
4. Si `--review` : sauter à la phase Review en fin de fichier.

## Tensions stratégiques à articuler tout au long

Garde ces axes en tête, fais-les expliciter à l'utilisateur quand il hésite :

- **européen ↔ international** (souveraineté EU vs ambition US/global)
- **clinique ↔ commercial** (radiologue-first vs achat hôpital)
- **factuel ↔ aspirational** (preuves vs vision)
- **rigueur réglementaire ↔ chaleur humaine** (MDR vs proximité radiologue)
- **sobriété ↔ ambition affichée** (low profile vs leader assumé)

Quand l'utilisateur dit "les deux", challenge : "Si tu dois trancher à 70/30, lequel domine ?"

## Round 1 — Positionnement (1 phrase)

### Questions cadrantes (4-5, courtes)
1. Cible principale du positionnement : radiologue, chef de service, CIO, ou les trois ?
2. Le problème central que vous résolvez en 5 mots ?
3. Vous vous positionnez **contre** quoi implicitement ? (statu quo manuel, AI US généraliste, AI europe non-certifiée…)
4. Juridiction prioritaire : EU first, US first, ou parité ?
5. Ce qu'**aucun concurrent** ne peut dire de lui légitimement ?

### Génère 3 candidats contrastés

- **Candidat A — institutionnel/regulatory** : met en avant CE MDR, certification, classe IIb/IIa
- **Candidat B — radiologue-centric** : met en avant workflow, temps, décision clinique
- **Candidat C — européen-souverain** : met en avant indépendance EU, RGPD, hébergement, contre l'AI US

Chaque candidat = 1 phrase ≤25 mots, structure "Avicenna.ai est [quoi] pour [qui] qui [bénéfice], avec [différenciateur]".

Présente les 3, demande lequel résonne, propose un hybride si l'utilisateur tire vers plusieurs axes. Sauvegarder dès validation : Read fichier complet → remplace section "Positionnement" → Write fichier complet.

## Round 2 — Personnalité (5 adjectifs hiérarchisés)

### Banque d'adjectifs medtech adaptés (~30, par axe)

- **Rigueur** : rigoureux, méthodique, factuel, mesuré, prudent, scientifique, traçable
- **Accessibilité** : accessible, pédagogique, clair, concret, proche, humain
- **Posture** : confiant, assumé, indépendant, souverain, calme, sobre, lucide
- **Innovation** : précis, exigeant, ambitieux, ingénieux, pragmatique
- **Ancrage clinique** : radiologue-centric, terrain, clinique, utile, complémentaire
- **Européen** : européen, souverain, conforme, transparent

### Contre-exemples à proposer comme repoussoirs
"agressif", "disruptive", "moonshot", "révolutionnaire", "visionnaire", "audacieux" — explique pour chacun pourquoi c'est incompatible (claims hype interdits MDR, posture US AI valley qui n'est pas la vôtre).

### Process
1. Demande à l'utilisateur de pré-shortlister 8-10 adjectifs dans la banque (peut en ajouter).
2. Force le tri à 5 hiérarchisés (#1 le plus discriminant).
3. **Challenge les contradictions** : si #1 = "audacieux" et #2 = "rigoureux", demander comment ils cohabitent dans une phrase concrète. Si #1 = "accessible" et concurrents nommés = "cliniciens", confronter.
4. Sauvegarde après validation.

## Round 3 — Voix par canal (4 canaux)

Traiter les 4 canaux séquentiellement : **Corporate web**, **LinkedIn corporate**, **LinkedIn CEO Cyril**, **Newsletter**.

### Méthode curseurs

Pour chaque canal, propose **3-4 curseurs binaires** à positionner (échelle 1-5) :

- institutionnel ↔ conversationnel
- factuel ↔ aspirational
- "nous" ↔ "je" (sauf CEO = "je" par défaut)
- jargon clinique ↔ vulgarisé
- sobriété ↔ enthousiasme contrôlé

Spécificités à imposer :
- **LinkedIn CEO** : "je" obligatoire, 0 émoji, opinions assumées sur MDR/FDA/AI souveraine — confirmé par le brand pack global.
- **Corporate web** : phrases courtes-moyennes, "nous"/"Avicenna", pas d'anglicismes en version FR.

### Synthèse
Après positionnement des curseurs, écris **3-5 lignes par canal** au format de `voice.md` (Ton, Personne, Longueur des phrases, Sujets de prédilection si CEO). Valide avant sauvegarde.

## Round 4 — Phrases qui sonnent "Avicenna" (5-10 à retenir)

### Génère 10 candidats alignés sur round 1

Variez les angles : 3 sur le radiologue, 2 sur la rigueur regulatory, 2 sur la complémentarité humain-AI, 2 sur l'ancrage européen, 1 sur le workflow hôpital.

Chaque candidat passe le **test de généricité** : "Cette phrase pourrait-elle être écrite par Aidoc, Viz.ai, ou n'importe quelle medtech AI ?" Si oui → trop générique, écarter ou reformuler avec un marqueur Avicenna (CE MDR, radiologue européen, classe IIb vasculaire, etc.).

### Process
1. Présente les 10, l'utilisateur garde 5-10 + raffine.
2. Pour chaque retenue : note **dans quel contexte** elle est utilisable (homepage, pitch deck, post LinkedIn, mail commercial).
3. Sauvegarde dans `voice.md` section "Phrases qui sonnent Avicenna".

## Round 5 — Phrases qui ne sonnent PAS Avicenna (5-10)

### Banque anti-patterns medtech standard

- "Révolutionner la radiologie" (hype)
- "Game changer" / "disruptive solution" (anglicismes creux)
- "L'AI remplace le radiologue" (interdit MDR absolu)
- "Première solution Y au monde" sans claim substantiable
- "Notre IA pense comme un radiologue"
- Toute comparaison nominative ("mieux que Aidoc", "contrairement à Viz.ai") — interdit par CLAUDE.md
- "Diagnostic" hors usage validé regulatory-guard

### Spécifiques selon positionnement choisi
Si le round 1 a choisi le candidat européen-souverain, ajouter anti-patterns type "leader mondial", "global standard" (incohérents). Si radiologue-centric, ajouter anti-patterns commerciaux type "ROI hospital", "boost productivity".

### Bonus
Demande à l'utilisateur : "Donne-moi 3 phrases qu'un commercial sous pression pourrait dire et qui violent la voice." Capture-les, ajoute-les à la liste avec mention "à corriger en revue commerciale". Sauvegarde.

## Round 6 — Vocabulaire (utiliser / éviter)

### Interview ouverte par champ
Traite champ par champ, sans candidats pré-mâchés (le vocabulaire est trop spécifique pour pré-générer) :

1. **Produit** : on dit "solution AI", "plateforme", "outil", "application" ?
2. **Utilisateur** : "radiologue", "clinicien", "praticien", "utilisateur" ?
3. **Hôpitaux** : "client", "partenaire", "site", "établissement" ?
4. **AI** : "intelligence artificielle", "AI", "IA", "deep learning", "apprentissage profond" ?
5. **Performances** : "détection", "quantification", "analyse", "triage" — quel terme pour quel produit ?

### Sauvegarde structurée
Pour chaque entrée "à utiliser" / "à éviter", **note la justification** (1 ligne) : cohérence regulatory, différenciation concurrent, ou choix éditorial. Pas d'entrée sans justification.

## Round 7 — Sortie finale et flags

1. Récap en 8-10 lignes : positionnement, top 3 adjectifs, ton dominant par canal, 3 phrases signature, 3 anti-patterns clés.
2. Confirme que `./brand/voice.md` est sauvegardé intégralement.
3. **Flags de revue à afficher** :
   - **Review CEO + responsable marketing recommandée** avant publication externe.
   - **Sign-off Reg Affairs requis UNIQUEMENT si** une phrase signature touche un claim produit (détection, performance, indication) — sinon non bloquant.
   - **Re-uploader** `voice.md` dans le claude.ai Project (cf. `_claude-ai-knowledge/UPLOAD_CHECKLIST.md`).
4. Prochain pas suggéré : remplir `glossary.md` ou `audiences.md` selon ce qui est le plus vide.

## Mode `--review` (cohérence sans modification)

Read `./brand/voice.md`. Vérifie :
- Positionnement (§1) cohérent avec adjectifs (§2) ? (Ex : "souverain européen" + "global leader" = incohérent.)
- Voix canal CEO (§3) cohérente avec brand pack global ("je", 0 émoji) ?
- Phrases signature (§4) passent le test de généricité ?
- Phrases anti-pattern (§5) couvrent bien les claims MDR interdits ?
- Vocabulaire (§6) cohérent avec `regulatory-guard.md` (à lire en parallèle si présent) ?

Restitue un tableau "section / cohérence ✅⚠️❌ / commentaire" et stop. **Ne modifie rien.**

## Contraintes techniques

- **Lecture/écriture** : toujours `./brand/voice.md` du cwd utilisateur, jamais le template du plugin.
- **Sauvegarde transactionnelle** : à chaque section validée, Read le fichier complet → remplace la section ciblée → Write le fichier complet. Ne jamais accumuler plusieurs sections avant sauvegarde (perte si interruption).
- **Préserve la structure** des titres existants de `voice.md` (`## Positionnement…`, `## Personnalité…`, etc.) — n'invente pas de nouvelle hiérarchie.
- **Ne touche pas** aux sections "Style rédactionnel" et "Émojis et formatting LinkedIn" du template — elles sont déjà cadrées globalement.

## Anti-patterns à refuser pendant le workshop

- **Candidats trop génériques medtech** : si un candidat de positionnement/phrase signature passerait sur le site de 5 concurrents → écarter, demander un marqueur Avicenna spécifique.
- **Validation prématurée** : si l'utilisateur valide en 5 secondes le premier candidat sans hésitation, demande "pourquoi celui-ci plutôt que B ou C ?" — fait verbaliser le critère.
- **Questions vagues** : pas de "tu veux quoi comme ton ?" — toujours des curseurs binaires ou des candidats à choisir.
- **Glissement vers la production** : si l'utilisateur dérive vers "rédige-moi un post LinkedIn pour tester", refuse poliment et redirige vers la skill `linkedin-post` une fois le workshop fini.
- **Sur-promesse regulatory** : aucune phrase signature qui contient "détecte", "diagnostique", "prédit" sans renvoi explicite à `regulatory-guard.md` § claims validés.
- **Tout reset sans confirmation** : en mode reprise, ne jamais écraser des sections déjà remplies sans demander.
