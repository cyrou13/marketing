# Regulatory Guard — Avicenna.ai

> ⚠️ **CRITIQUE** — Ce fichier protège Avicenna contre des violations MDR (Article 7 sur la publicité), FDA promotional rules, et claims off-label.
> À chaque génération de contenu marketing, Claude DOIT vérifier le contenu contre ce fichier avant de proposer un draft.
> À mettre à jour à chaque nouvelle clearance, à chaque évolution d'IFU, et à chaque review affaires réglementaires.

## Principe directeur

Tout claim marketing doit être :
1. **Cohérent avec l'indication d'usage validée** (CE / FDA selon la cible)
2. **Sourcé** (paper publié, données de clearance, étude clinique référencée)
3. **Géographiquement adapté** (un claim FDA-cleared ne peut pas être avancé en Europe sans CE équivalent)

---

## Mots et tournures INTERDITS dans tout contenu marketing

| Terme | Pourquoi | Alternative validée |
|-------|----------|---------------------|
| "diagnostic" / "diagnostique" | Indication régulatoire spécifique, claim non couvert sauf produits explicitement diagnostic | "aide à la décision", "quantification", "détection (selon IFU)" |
| "remplace le radiologue" | FAUX et interdit | "assiste le radiologue", "soutient l'interprétation" |
| "100 % précis" / "infaillible" | Aucun dispositif ne l'est | citer la sensibilité/spécificité publiée avec IC95 % |
| "guérit" / "traite" | Avicenna n'est pas thérapeutique | "documente", "quantifie", "détecte" |
| "approuvé par la FDA" | Confusion approval/clearance | "FDA cleared (510(k) #K…)" |
| "validé scientifiquement" sans référence | Vague, non-substantiable | "validé dans [paper, journal, année]" |

[À COMPLÉTER selon retours affaires réglementaires]

## Mots SENSIBLES — usage conditionnel

| Terme | Condition d'usage |
|-------|-------------------|
| "AI" / "intelligence artificielle" | OK partout, mais éviter d'isoler "AI seule" : toujours "AI + radiologue" |
| "automatique" / "automatisé" | OK pour quantification, attention pour détection (vérifier l'IFU produit) |
| "temps réel" | OK seulement si latence < X secondes mesurée et documentée |
| "première solution" / "leader" | Substantier avec source ou retirer |

## Claims AUTORISÉS par produit (à compléter par produit)

### CINA-CHEST (exemple — à valider/corriger)
- ✅ "Triage et notification d'embolie pulmonaire suspectée sur CT thoracique avec injection"
- ✅ "FDA cleared (K…)" / "CE marqué classe IIa MDR"
- ✅ Performance : "Sensibilité X %, spécificité Y % sur cohorte de N patients" + référence paper
- ❌ Ne pas dire : "diagnostique l'EP", "détecte toutes les EP"

### CINA-ASPECTS
[À COMPLÉTER]

### CINA-LVO
[À COMPLÉTER]

### CINA-iPE
[À COMPLÉTER]

### CT Perfusion
[À COMPLÉTER — attention indication exacte]

### AKILA (foundation model)
- ⚠️ Pas de claim clinique direct si non encore cleared
- ✅ Communication "research" / "technologie de pointe" autorisée
- ❌ Pas de claim de performance sur des indications non couvertes par une clearance dédiée

## Disclaimers obligatoires par juridiction

### Europe (CE)
> Les solutions Avicenna sont des dispositifs médicaux marqués CE. Avant utilisation, lire attentivement la notice d'instruction (IFU). [Numéro de notification corps notifié].

### USA (FDA)
> Caution: U.S. Federal law restricts this device to sale by or on the order of a physician. Refer to the Indications for Use for full prescribing information.

### Pays sans clearance locale
> Ne pas mentionner le produit comme disponible. Communications limitées à "en cours d'évaluation" / "bientôt disponible".

## Mentions obligatoires

- **Article scientifique cité** : auteur, journal, année + DOI si disponible
- **Performance clinique mentionnée** : source + taille de cohorte + IC95 %
- **Comparatif concurrent** : à éviter sauf benchmark publié et défendable

## Process de review

| Type de contenu | Review obligatoire avant publication |
|-----------------|--------------------------------------|
| Communiqué presse | Affaires réglementaires + CEO |
| Article blog avec claim de performance | Affaires réglementaires |
| Post LinkedIn corporate annonçant clearance | Affaires réglementaires |
| Post LinkedIn CEO opinion / thought leadership | CEO seul (sauf claim produit) |
| Newsletter | Marketing seul (sauf claim produit) |
| Étude de cas client | Marketing + Clinical + accord client écrit |

## Checklist Claude (à exécuter avant chaque output)

- [ ] Aucun mot interdit présent
- [ ] Tout mot sensible utilisé est conforme à sa condition d'usage
- [ ] Tout claim de performance est sourcé
- [ ] L'indication mentionnée correspond à l'IFU du produit cité
- [ ] La juridiction (EU/US/autre) est cohérente avec le claim
- [ ] Si un point est incertain, FLAGGER avec `[CHECK: raison]` plutôt que de générer un claim risqué
