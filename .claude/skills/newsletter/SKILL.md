---
name: newsletter
description: Drafte une newsletter mensuelle Avicenna.ai (audience radiologues + chefs de service + CIO partenaires) ou une section dédiée de newsletter (nouveautés, customer spotlight, paper highlight, regulatory update). Charge le brand pack, applique le regulatory-guard, structure pour lecture rapide. À utiliser pour la newsletter mensuelle complète ou pour livrer une section autonome insérable dans un email plus large.
---

# Skill — Newsletter

## Audiences

La newsletter mensuelle Avicenna est lue par :
- **Audience principale** : radiologues utilisateurs et prospects, chefs de service partenaires
- **Audience secondaire** : CIO / DSI hospitaliers, partenaires industriels
- **Pas la cible** : investisseurs (utiliser `prompts/email-investor-monthly-template.md`), grand public

Adapter le ton en conséquence : factuel, concret, orienté valeur clinique et opérationnelle.

## Avant de rédiger

Charger :
- `brand/voice.md` (section newsletter)
- `brand/audiences.md` (radiologues + chefs de service + CIO existants)
- `brand/regulatory-guard.md`
- `brand/proof-points.md` (chiffres du mois)
- `brand/glossary.md` (vocabulaire produit)

## Modes d'usage

### Mode 1 — Newsletter mensuelle complète

Inputs requis :
1. **Mois / année** de l'édition
2. **Liste des éléments du mois** (raw, à structurer) :
   - Clearances / mises à jour produit
   - Papers publiés (Avicenna ou évaluant Avicenna)
   - Customer spotlights (avec accord)
   - Présence congrès / événements
   - Roadmap publique (court terme)
   - Hires stratégiques
3. **Hero story** : l'élément le plus fort du mois (1 seul, hiérarchiser)
4. **CTA principal** : démo, ressource, page produit, événement
5. **Visuels disponibles** par section

### Mode 2 — Section autonome

Inputs requis :
1. **Type de section** :
   - "Nouveautés produit" (post-clearance) — voir aussi workflow `new-clearance.md`
   - "Customer spotlight" — voir aussi workflow `case-study-pipeline.md`
   - "Paper highlight" — voir aussi workflow `new-paper.md`
   - "Regulatory update" / "AI Act / MDR corner"
   - "Équipe" (hire, milestone interne)
2. **Inputs spécifiques au type** (cf. workflows)
3. **Longueur cible** : 100-300 mots typiquement

## Structure newsletter mensuelle

### En-tête
- Sujet email (≤ 60 char)
- Pré-header (≤ 100 char) — le hook de prévisualisation
- Date édition

### 1. Hero story (200-300 mots)
- L'élément fort du mois
- Hook factuel, pas de "ce mois-ci…"
- 1 visuel
- 1 CTA contextuel

### 2. Nouveautés (3-5 items × 2-3 lignes)
- Bullets très courts, factuels
- Chaque item avec lien vers page produit / ressource / blog
- Pas de hype

### 3. Au cœur du métier (variable)
Une rubrique parmi :
- Customer spotlight (extrait étude de cas)
- Paper highlight (vulgarisation 150 mots + DOI)
- Coulisses tech (R&D, sans révéler la roadmap confidentielle)
- Regulatory corner (AI Act, MDR, FDA guidance)

### 4. Avicenna sur le terrain
- Congrès / événements à venir
- Webinaires / workshops
- Lieux de rencontre du mois prochain

### 5. Roadmap publique (concis)
- Ce qu'on peut dire selon `brand/proof-points.md` section "Roadmap publique"
- **Jamais** la roadmap confidentielle

### 6. Pied
- Liens utiles (site, démo, contact CSM)
- Mentions légales (dispositif médical, IFU disclaimer si claim produit dans la newsletter)
- Lien désinscription
- Adresse postale (compliance email FR / CAN-SPAM US)

## Contraintes de format

- Longueur totale : ~600-1000 mots, lecture 4-6 min max
- Sujet email A/B testable : proposer 2-3 sujets
- Pré-header complémentaire au sujet (pas redondant)
- 1 émoji max dans le sujet, 0-1 dans le corps (pas de feu d'artifice)
- Phrases courtes, paragraphes courts (mobile-first)
- Liens : ancres descriptives, jamais "cliquez ici"
- Compatible mode sombre

## Vérifications regulatory-guard

- [ ] Aucun mot interdit
- [ ] Tout claim de performance produit sourcé inline (lien paper, mention clearance)
- [ ] Indication mentionnée = IFU produit selon juridiction destinataire
- [ ] Si la newsletter est multi-juridiction : utiliser formulations neutres, ou faire 2 versions (US / EU)
- [ ] AKILA absent ou explicitement R&D
- [ ] Aucune comparaison nominative concurrent
- [ ] Aucune donnée patient identifiable (même dans customer spotlight)
- [ ] Disclaimer dispositif médical si claim produit

## Livrables systématiques

1. **Newsletter complète** (markdown structuré + HTML si demandé)
2. **2-3 sujets email A/B** avec pré-headers correspondants
3. **Version mobile-friendly** vérifiée (longueur ligne, pas de tableaux complexes)
4. **Notes** :
   - claims utilisés + sources
   - vérifications regulatory-guard
   - suggestions visuelles par section
   - alternatives de hero story si l'item principal est faible

## Process de review

Selon `regulatory-guard.md` §7 :
- Newsletter sans claim produit : Marketing seul
- Newsletter avec claim produit : Marketing + Affaires Réglementaires
- Newsletter avec customer spotlight : Marketing + accord client écrit déjà obtenu (revérifier)

## Anti-patterns à refuser

- "Ce mois-ci chez Avicenna…" (banal, ne donne pas envie de lire)
- "Nous sommes ravis de vous présenter…" (creux)
- Émojis décoratifs en début de chaque section
- 5 CTAs concurrents (en garder un principal + secondaires discrets)
- Hero story faible "remplie" parce que la newsletter doit sortir (préférer décaler ou raccourcir)
- Roadmap confidentielle qui fuit
- Listing exhaustif de tout ce qu'a fait Avicenna (sélectionner)
