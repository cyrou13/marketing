# Workflow — New Clearance Amplification

## Objectif

Quand Avicenna obtient une nouvelle clearance FDA (510(k)) ou un nouveau marquage CE, produire en une session :
- Le communiqué presse
- Le post LinkedIn corporate
- Le post LinkedIn CEO
- Une section pour la prochaine newsletter
- Un draft d'article blog d'approfondissement
- Une FAQ inbound presse / clients

Le tout cohérent narrativement, conforme aux contraintes régulatoires, et prêt à être validé par les affaires réglementaires en une revue groupée.

## Inputs requis (à fournir avant exécution)

Sans ces 4 inputs, NE PAS lancer le workflow :

1. **Document régulatoire officiel** : la clearance letter (FDA) ou certificat CE complet
2. **Indication d'usage exacte** (verbatim de l'IFU validée)
3. **Claims autorisés** par les affaires réglementaires en interne
4. **Périmètre géographique** : US uniquement, EU uniquement, ou les deux

Inputs optionnels mais recommandés :
- Citation CEO pré-validée (sinon Claude proposera 2-3 options à valider)
- Données de performance publiées (paper, étude pivot)
- Date d'embargo / publication

## Étapes

### Étape 1 — `regulatory-extractor`
Extraction structurée du document de clearance : numéro, indication verbatim, limitations, comparateur prédicat, claims autorisés vs interdits implicites, date effective.
➡️ `outputs/[date]-clearance-[product]/00-regulatory-extract.md`

### Étape 2 — `message-architect`
Matrice de messages : 1 phrase pour radiologue / CIO / journaliste / investisseur / talent.
➡️ `outputs/[date]-clearance-[product]/01-message-matrix.md`

### Étape 3 — `regulatory-comm` (skill)
Communiqué presse complet selon périmètre FDA / CE.
➡️ `outputs/[date]-clearance-[product]/02-press-release.md`

### Étape 4 — `linkedin-post` (skill) × 2
- Variante corporate (factuel + enthousiasme contrôlé)
- Variante Cyril CEO (angle "ce que ça change pour…")
➡️ `03a-linkedin-corporate.md`, `03b-linkedin-ceo.md`

### Étape 5 — `newsletter` (skill, partiel)
Section "Nouveautés" intégrable dans la prochaine newsletter mensuelle.
➡️ `04-newsletter-section.md`

### Étape 6 — `blog-article` (skill, archétype "regulatory / scientific update")
1000-1500 mots qui contextualisent la clearance.
➡️ `05-blog-article.md`

### Étape 7 — `inbound-faq`
8-12 Q/R préparées pour sales / support / press : cliniques, intégration, concurrentielles, roadmap (avec garde-fous).
➡️ `06-inbound-faq.md`

### Étape 8 — `reviewer` (étape critique)
Pass des outputs 3-7 contre `brand/regulatory-guard.md`. Verdict par livrable :
- ✅ READY FOR REVIEW
- ⚠️ REQUIRES FIXES (avec liste précise)
- 🛑 BLOCKING ISSUE
➡️ `07-review-report.md`

## Commande d'exécution Claude Code

```
Exécute le workflow new-clearance.

Inputs :
- Document régulatoire : [path ou contenu collé]
- Indication d'usage exacte : [verbatim]
- Claims autorisés : [...]
- Périmètre géographique : [US / EU / both]
- Citation CEO pré-validée : [oui : "..." / non : proposer 3 options]
- Données de performance : [paper référence ou n/a]
- Date d'embargo : [date]

Crée le dossier outputs/[YYYY-MM-DD]-clearance-[product]/ et exécute les
étapes 1 à 8 dans l'ordre. Ne passe à l'étape suivante que si la précédente
est terminée. Si une étape bloque (input manquant), demande avant de continuer.
```

## Délais typiques

- Étapes 1-2 : 5 min
- Étapes 3-7 : 30-45 min
- Étape 8 : 5 min
- **Total Claude** : ~1h
- **Review humaine ensuite** : 1-2h équipe RA + Marketing + CEO

À comparer aux 2-3 jours typiquement nécessaires sans workflow.
