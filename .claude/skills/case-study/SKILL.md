---
name: case-study
description: Produit une étude de cas hôpital Avicenna.ai à partir de transcripts d'interview client + données quantitatives validées. Format long (PDF 4 pages ou page web 1500-2500 mots). Skill sensible — ne démarre que si les prérequis (accord écrit hôpital, citations validées, Quality + Legal sign-off) sont confirmés. Voir aussi le workflow `workflows/case-study-pipeline.md`.
---

# Skill — Case Study (étude de cas hôpital)

## Avertissement

C'est le skill le plus sensible du repo. Une étude de cas mal cadrée peut :
- Violer un accord client (citation non validée, donnée confidentielle)
- Enfreindre RGPD / HIPAA (donnée patient identifiable)
- Créer un claim de performance produit non substantiable

**Ne pas démarrer la rédaction sans les prérequis ci-dessous.**

## Prérequis bloquants

Refuser de produire le draft si l'un manque :
- [ ] **Accord écrit hôpital** pour publication (PDF référencé)
- [ ] **Transcript ou notes** d'interview du référent clinique
- [ ] **Données quantitatives** validées par l'hôpital (avant/après, période, méthode de mesure)
- [ ] **Citations verbatim** validées par écrit par les personnes citées
- [ ] **Liste des éléments confidentiels** à NE PAS divulguer
- [ ] **Sign-off Quality + Legal Avicenna** sur le scope

Si l'un manque : refuser et lister ce qui manque. Pointer vers `prompts/case-study-interview-questions.md` pour structurer la collecte.

## Avant de rédiger (chargements)

- `brand/voice.md` (corporate, ton clinique)
- `brand/audiences.md` (persona radiologue + chef de service + CIO selon angle)
- `brand/regulatory-guard.md`
- `brand/proof-points.md` (cohérence des chiffres avec le reste de la communication)
- `brand/glossary.md` (vocabulaire produit, niveaux d'explication)

## Inputs requis du rédacteur

1. **Hôpital / centre** : nom, ville, type (CHU, clinique, GHT, teleradio…)
2. **Périmètre publication** : externe public / externe restreint / interne seulement
3. **Format final** : PDF 2 pages / PDF 4 pages / page web / les trois
4. **Audience principale** : radiologue / chef de service / CIO / mixte
5. **Indication clinique** déployée (avec produit Avicenna, IFU, juridiction)
6. **KPIs avant/après** avec méthode et période
7. **Citations validées** (verbatim, attribution complète)
8. **Données techniques** : PACS, RIS, durée d'intégration, ressources mobilisées
9. **Éléments confidentiels** à exclure

## Structure standard

### 1. Bandeau de tête
- Hôpital, ville, type
- Indication clinique
- Produit Avicenna concerné
- Période d'observation
- 1 chiffre headline (issu des KPIs validés)

### 2. Contexte (200-300 mots)
- Profil du service : volumétrie, spécialité, équipe
- Défis cliniques 2026 sur l'indication
- Situation initiale (factuelle, sans dénigrer l'existant)

### 3. La décision Avicenna (200-300 mots)
- Critères d'évaluation
- Pourquoi Avicenna a été retenu (factuel, pas hagiographique)
- Décideurs impliqués

### 4. Le déploiement (200-400 mots)
- Intégration technique : PACS, RIS, durée, jalons
- Formation et adoption radiologues
- Résistances levées (honnête)

### 5. Résultats (300-500 mots)
- KPIs quantitatifs avec méthode et période
- Bénéfices qualitatifs observés
- Points de friction qui persistent (honnêteté = crédibilité)

### 6. Citations (1-2 pull quotes)
- Verbatim validés
- Attribution complète : Nom, fonction, hôpital
- Pas de retouche

### 7. Perspectives (100-200 mots)
- Ce que l'hôpital prévoit ensuite avec Avicenna
- Sans s'engager sur du non-publié côté Avicenna

### 8. Encadré "À retenir"
- 3-5 takeaways factuels

### 9. Signaux régulatoires
- Disclaimer juridiction (CE / FDA selon le cas)
- Mention IFU
- Mention dispositif médical

## Vérifications regulatory-guard

- [ ] Aucun mot interdit
- [ ] Tous les chiffres tracés à un input validé hôpital
- [ ] Toutes les citations sont verbatim et attribuées
- [ ] Aucune donnée patient identifiable (zéro tolérance)
- [ ] L'indication mentionnée = IFU du produit cité
- [ ] Disclaimer juridiction présent
- [ ] AKILA absent ou explicitement R&D si mentionné
- [ ] Aucun élément de la liste confidentielle n'apparaît
- [ ] Aucune comparaison concurrent

## Livrables systématiques

1. **L'étude de cas** au format demandé (markdown structuré, prêt pour design ou web)
2. **Variantes courtes** (sur demande) :
   - Résumé 1 paragraphe pour newsletter
   - Bullet 3 lignes pour deck commercial
3. **Notes de validation** :
   - Liste des éléments à re-valider hôpital
   - Liste des éléments à valider Quality / Legal Avicenna
   - Suggestions visuelles
4. **Process de validation post-pipeline** rappelé :
   1. Marketing : revue éditoriale
   2. Quality : claims produit
   3. Legal : conformité RGPD/HIPAA, citations
   4. CSM en charge du compte
   5. **Hôpital** : validation finale (non-négociable)
   6. CEO ou CMO : sign-off final

## Anti-patterns à refuser

- Triomphalisme ("Avicenna a transformé…")
- Comparaison nominative avec un autre éditeur
- Chiffres "approximatifs" sans méthode
- Citations reformulées ou paraphrasées
- Tout détail patient (âge précis, pathologie spécifique, dates examen)
- Promesse roadmap implicite ("Avicenna va déployer X chez nous bientôt")
- Disclaimer manquant
