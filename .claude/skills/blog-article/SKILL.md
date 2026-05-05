---
name: blog-article
description: Drafte un article de blog Avicenna.ai (1000-2500 mots) selon un archétype défini — clinical, technical, regulatory/scientific update, strategic. Charge le brand pack, applique le regulatory-guard, structure pour SEO si demandé. À utiliser pour toute production blog au-delà de 800 mots ; en deçà, utiliser un prompt ponctuel.
---

# Skill — Blog Article

## Archétypes supportés

| Archétype | Audience | Longueur | Quand l'utiliser |
|-----------|----------|----------|------------------|
| **clinical** | Radiologue, chef de service | 1200-2000 mots | Vulgarisation rigoureuse d'un paper, étude de cas raccourcie, deep-dive indication |
| **technical** | Talent ML, CIO, radiologue tech-savvy | 1500-2500 mots | Stack, architecture, intégration PACS, foundation model |
| **regulatory / scientific update** | Mixte radiologue + investisseur + chef de service | 1000-1500 mots | Annonce d'une clearance, contextualisation d'un paper publié |
| **strategic** | Chef de service, CIO, investisseur | 1500-2500 mots | Position de marché, paysage AI radiologie, souveraineté européenne |
| **SEO pillar** | Lecteur Google sur mot-clé stratégique | 2000-3000 mots | Référencement organique long terme — voir aussi `prompts/blog-seo-pillar.md` |

## Avant de rédiger

Charger :
- `brand/voice.md` (section corporate)
- `brand/audiences.md` (persona principal + secondaires)
- `brand/regulatory-guard.md`
- `brand/glossary.md` (vocabulaire produit, niveaux d'explication par audience)
- `brand/proof-points.md` (chiffres citables)
- Tout paper / document fourni par le rédacteur

## Inputs requis

1. **Archétype** parmi la liste ci-dessus
2. **Sujet** en 1-2 phrases
3. **Audience principale** + audiences secondaires
4. **Angle différenciant** : qu'est-ce que cet article apporte qu'on ne trouve pas ailleurs
5. **Claims à inclure** (avec source si performance produit)
6. **Liens internes** disponibles (pages produit, autres articles, ressources)
7. **CTA principal** : whitepaper, démo, contact, abonnement newsletter
8. **Langue** : français / anglais / les deux (si bilingue, livrer FR d'abord)

Inputs optionnels :
- Mots-clés SEO si l'article est SEO-ciblé
- Auteur signataire (Cyril, équipe clinique, équipe ML, marketing)
- Date de publication souhaitée
- Visuels disponibles (figures de paper, schémas archi, captures produit)

## Process en 2 temps

### Temps 1 — Plan détaillé (validation avant rédaction)

Livrer :
- **Title tag** (≤ 60 char) + **H1** + **slug** + **meta-description** (≤ 160 char)
- **8-12 H2** avec H3 si pertinent
- **Pour chaque H2** : 1 phrase de contenu prévu + claims/sources qui y figureront
- **Visuels suggérés** par section
- **Liens internes** placés
- **Bloc FAQ final** : 3-5 questions (style "people also ask")
- **CTA double** si possible : ressource gratuite + page produit

Demander validation au rédacteur avant rédaction.

### Temps 2 — Rédaction

Une fois le plan validé :
- Respecter strictement la structure validée
- Phrases 15-25 mots en moyenne
- Paragraphes 3-5 phrases max
- Acronymes développés à la première occurrence (sauf CT, IRM, AI)
- Limiter les anglicismes en français (préférer "apprentissage profond" à "deep learning")
- Citations des papers : auteur, journal, année, DOI

## Vérifications regulatory-guard

Pour chaque article :
- [ ] Aucun mot interdit (`diagnostic`, `remplace`, `100% précis`, `approuvé FDA`…)
- [ ] Chaque claim de performance est sourcé inline (paper avec DOI, ou pointeur `proof-points.md`)
- [ ] Indication mentionnée = IFU produit (par juridiction)
- [ ] AKILA présenté comme R&D, pas comme produit clinique
- [ ] Aucune comparaison nominative dénigrante de concurrent
- [ ] Disclaimer juridiction adapté (CE / FDA) si claim de performance produit
- [ ] Pas de donnée patient identifiable

## Livrables systématiques

1. **L'article** complet (markdown ou format demandé)
2. **Méta-données SEO** : title tag, meta-description, slug, schema markup recommandé (Article, MedicalWebPage, FAQ), Open Graph
3. **Notes** :
   - claims utilisés + sources
   - vérifications regulatory-guard
   - visuels suggérés (à briefer au designer)
   - 5-10 propositions de title alternatifs (A/B)
4. **Recommandation review** : qui doit signer-off avant publication selon `regulatory-guard.md` §7

## Si l'article cite un paper

Format obligatoire : auteur·e principal·e, journal, année, DOI.
Si le paper a une limite ou une nuance importante, la mentionner explicitement — pas de cherry-picking.

## Anti-patterns à refuser

- Hagiographie produit ("la solution la plus avancée")
- Listes à puces partout (réserver à la vraie énumération)
- "Révolutionner", "disruptive", "game changer"
- Comparaison "vs concurrent X"
- Claims chiffrés sans source
- Article qui ne sert aucun objectif business clair (notoriété SEO / lead gen / thought leadership / recrutement)
