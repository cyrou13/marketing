# Workflow — Publication d'un paper scientifique

> Pipeline pour transformer la publication d'un paper (Avicenna auteur ou
> co-auteur, ou paper évaluant un produit Avicenna) en pack de contenu
> multi-canal.

---

## Quand le déclencher

- Paper accepté avec date de publication confirmée
- Paper publié en preprint (arXiv, medRxiv) avec stratégie de pré-annonce
- Communication post-conférence (RSNA, ECR) si présentation associée

## Prérequis

- [ ] PDF final du paper (ou preprint)
- [ ] DOI ou lien permanent
- [ ] Résumé en français (si paper en EN)
- [ ] Liste des co-auteurs et leurs accords pour communication
- [ ] Figures principales (avec droits de reproduction confirmés)
- [ ] Validation Reg Affairs : ce paper soutient-il un claim de
      performance ? Si oui, formulation autorisée.

## Pipeline

```
AGENT 1 — paper-summarizer
  Output : 01-paper-summary.md
    - Question de recherche
    - Méthode (dataset, taille, métriques)
    - Résultats principaux
    - Limites mentionnées par les auteurs
    - Implications cliniques
    - Quote citable des auteurs (si présent dans la discussion)

AGENT 2 — claim-extractor
  Input : 01-paper-summary + brand/regulatory-guard.md
  Output : 02-claims-validated.md
    - Liste des claims chiffrés que le paper supporte
    - Formulation exacte autorisée pour communication
    - Claims tentants mais NON supportés par le paper

AGENT 3 — blog-deep-dive
  (skill blog-article type technical ou clinical)
  Output : 03-blog-article.md (1500-2500 mots)
    - Vulgarisation rigoureuse
    - Pas de cherry-picking
    - Limites discutées honnêtement

AGENT 4 — linkedin-thread
  (skill linkedin-post)
  Output :
    - 04-linkedin-CEO-announcement.md (post lancement)
    - 04-linkedin-corporate-deepdive.md (J+3, focus méthode)
    - 04-linkedin-team-perspective.md (J+7, voix d'un auteur Avicenna)

AGENT 5 — newsletter-section
  Output : 05-newsletter-paper-highlight.md

AGENT 6 — academic-channels
  Output : 06-academic-content.md
    - Texte court pour ResearchGate
    - Thread Twitter / X (5-7 tweets) si stratégie X active
    - Texte pour profil Hugging Face si modèle associé

AGENT 7 — investor-update
  Output : 07-investor-brief-paper.md
    - Pourquoi ce paper compte pour la thèse business
    - Predicate pour futures clearances ?

AGENT 8 — reviewer
  Output : 08-review-report.md
```

## Différence avec le workflow new-clearance

- Pas de communiqué de presse formel par défaut (sauf paper majeur dans
  une revue très visible : Radiology, Nature Medicine, NEJM AI…)
- Plus de place pour la nuance scientifique et les limites
- Voix plus académique sur les canaux dédiés
- Cible secondaire forte : recrutement (ML engineers lisent les papers
  avant de candidater)

## Output

Dossier daté `outputs/YYYY-MM-paper-<short-title>/` avec la même structure
que pour les clearances.
