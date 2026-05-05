# Workflow — Étude de cas hôpital

> Pipeline pour transformer un déploiement hospitalier réussi en pack de
> contenu multi-canal. Plus exigeant que les autres workflows : la matière
> première (interview client) doit être collectée hors-ligne d'abord.

---

## Phase 0 — Hors workflow : la collecte

Ce qui suit n'est **pas** automatisé. C'est du travail terrain :

- [ ] Identifier l'hôpital candidat (CSM + ventes)
- [ ] Demander accord de principe à la direction de l'hôpital
- [ ] Interview du référent radiologue (1h enregistrée si possible, avec
      accord)
- [ ] Interview du CIO ou IT lead (30 min)
- [ ] Collecte des données quantitatives (avant/après) avec validation
      hôpital
- [ ] Accord écrit final pour communication publique
- [ ] Validation Quality + Legal Avicenna sur le scope

Sans ces inputs, le workflow ne peut pas démarrer.

## Prérequis bloquants

- [ ] Accord écrit hôpital (`references/case-studies/<hospital>-consent.pdf`)
- [ ] Transcript ou notes d'interview référent clinique
- [ ] Transcript ou notes d'interview CIO (si applicable)
- [ ] Données quantitatives validées par l'hôpital
- [ ] Quotes proposées et validées par les personnes citées
- [ ] Liste des éléments confidentiels à NE PAS divulguer

## Pipeline

```
AGENT 1 — interview-extractor
  Input : transcripts + données quanti
  Output : 01-raw-facts.md
    - Métriques avec source et méthode de mesure
    - Quotes formatées (verbatim, avec attribution)
    - Anecdotes utilisables
    - Points sensibles / hors-scope

AGENT 2 — narrative-architect
  Input : 01 + brand/audiences.md
  Output : 02-story-arc.md
    - Avant : situation initiale honnête (sans dénigrer)
    - L'inflexion : ce qui a changé avec Avicenna
    - Après : résultats mesurés
    - Cliff-hanger : ce que l'hôpital prévoit ensuite

AGENT 3 — case-study-writer
  (skill case-study)
  Output : 03-case-study-long.md (format PDF design ou page web)

AGENT 4 — blog-summary
  (skill blog-article type clinical)
  Output : 04-blog-article.md (800-1200 mots, lien vers étude complète)

AGENT 5 — linkedin-set
  (skill linkedin-post)
  Output :
    - 05-linkedin-launch.md (J0, hook sur métrique principale)
    - 05-linkedin-quote.md (J+3, citation pull-quote sur image)
    - 05-linkedin-cio-angle.md (J+7, angle intégration technique)

AGENT 6 — sales-collateral
  Output :
    - 06-one-pager.md (livré au design)
    - 06-sales-deck-slide.md (1-2 slides à intégrer dans deck commercial)
    - 06-email-template-prospects.md (référer à ce cas dans nurturing)

AGENT 7 — newsletter-section
  Output : 07-newsletter-customer-spotlight.md

AGENT 8 — reviewer-with-customer-flag
  Special : flag tout élément qui devrait être re-validé par l'hôpital
  avant publication
  Output : 08-review-report.md
```

## Process de validation post-pipeline

1. Marketing : revue éditoriale
2. Quality : claims de performance produit
3. Legal : conformité RGPD/HIPAA, citations, données
4. **CSM en charge du compte** : alignement avec la relation client
5. **Hôpital lui-même** : validation finale du draft avant publication
6. CEO ou CMO : signe-off final

L'étape 5 (validation hôpital) est **systématique** et non-négociable.

## Output

`outputs/YYYY-MM-case-<hospital>/` avec la structure standard.
