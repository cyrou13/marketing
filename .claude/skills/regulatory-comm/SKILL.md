---
name: regulatory-comm
description: Drafte les communications réglementaires Avicenna.ai — communiqué de presse de clearance (FDA 510(k) ou CE MDR), annonce de mise à jour d'IFU, communication d'extension d'indication. Skill à très haut niveau de contrainte. Refuse de travailler sans le document régulatoire officiel et sans claims pré-validés Reg Affairs. Voir aussi `workflows/new-clearance.md`.
---

# Skill — Regulatory Communication

## Avertissement

Toute communication réglementaire engage la conformité MDR (Article 7 sur la publicité), les FDA promotional rules, et expose à des risques juridiques en cas de claim off-label. Ce skill applique des contraintes plus strictes que les autres.

**Refuser de produire un draft si les inputs ne sont pas tous présents.**

## Prérequis bloquants

Refuser tant que les 4 inputs suivants ne sont pas fournis :

1. **Document régulatoire officiel** : clearance letter FDA (510(k) ou De Novo) ou certificat CE MDR complet
2. **Indication d'usage exacte** (verbatim de l'IFU validée)
3. **Claims autorisés** par les Affaires Réglementaires en interne (verbatim)
4. **Périmètre géographique** : US uniquement, EU uniquement, ou les deux

Inputs optionnels mais recommandés :
- Citation CEO pré-validée (sinon proposer 2-3 options à valider)
- Données de performance publiées (paper, étude pivot, IC95%)
- Date d'embargo / publication
- Visuels disponibles
- Liste des analystes / journalistes à briefer en parallèle

## Avant de rédiger

Charger :
- `brand/regulatory-guard.md` (référence absolue)
- `brand/voice.md` (section corporate / communiqué)
- `brand/proof-points.md` (chiffres traction et performance)
- `brand/glossary.md` (formulation produit canonique)
- `brand/audiences.md` (persona journaliste + investisseur prioritaires sur ce canal)

## Types de communications supportés

| Type | Trigger | Validation requise |
|------|---------|---------------------|
| **Press release clearance** | Nouvelle 510(k) ou CE MDR | RA + CEO |
| **Press release extension** | Extension indication / nouvelle modalité | RA + CEO |
| **IFU update communication** | Modification IFU significative | RA |
| **Recall / safety notice** | Action corrective | RA + Quality + Legal + CEO |
| **Statement régulatoire** | Réponse à évolution réglementaire (AI Act, MDR amendment, FDA guidance) | RA + CEO |

## Structure standard d'un communiqué de clearance

### 1. En-tête
- Date et lieu (ville HQ)
- Mention "POUR DIFFUSION IMMÉDIATE" ou date d'embargo
- Logo placeholder

### 2. Titre (≤ 110 char)
Format : `Avicenna.ai obtient [type clearance] pour [produit] dans [indication courte]`

Pas de superlatif. Pas de "first-ever" sans source.

### 3. Sous-titre / chapô (1-2 phrases)
Indication validée + bénéfice clinique factuel. Aucun claim de performance non sourcé.

### 4. Corps — paragraphe 1 (factuel)
- Annonce de la clearance (FDA 510(k) #K… / CE marqué classe IIa MDR, organisme notifié)
- Indication d'usage **verbatim** de l'IFU
- Date effective

### 5. Corps — paragraphe 2 (contexte clinique)
- Le besoin clinique adressé
- Pas de chiffre épidémiologique sans source
- Pas de comparaison concurrent

### 6. Corps — paragraphe 3 (technologie / produit)
- Description fonctionnelle alignée IFU
- Mention CINA / produit Avicenna avec formulation glossary.md

### 7. Citation CEO (40-80 mots)
Validée ou proposée en 2-3 options. Pas de claim chiffré non sourcé.

### 8. Citation utilisateur clinique (optionnelle)
Verbatim validé par la personne. Attribution complète.

### 9. Performance / preuves (si applicable)
Si un paper soutient des chiffres :
- Auteurs, journal, année, DOI
- Sensibilité / spécificité avec IC95%
- Taille de cohorte
- Sinon : ne pas inventer, ne pas mettre cette section

### 10. À propos d'Avicenna.ai (boilerplate)
3-5 phrases, version EN et FR. Cohérence avec `brand/voice.md` corporate.

### 11. Disclaimers obligatoires

#### Pour US :
> Caution: U.S. Federal law restricts this device to sale by or on the order of a physician. Refer to the Indications for Use for full prescribing information.

#### Pour EU :
> Les solutions Avicenna sont des dispositifs médicaux marqués CE classe [IIa selon MDR]. Avant utilisation, lire attentivement la notice d'instruction (IFU). Organisme notifié : [N°].

### 12. Contact presse
- Nom contact
- Email dédié
- Site media

## Vérifications regulatory-guard (impératif)

Checklist exhaustive à exécuter avant livraison :

- [ ] Aucun mot interdit (`diagnostic` hors usage validé, `remplace`, `100% précis`, `approuvé FDA`, `validé scientifiquement` sans source)
- [ ] Indication d'usage **verbatim** IFU
- [ ] Numéro 510(k) ou certificat CE cité correctement
- [ ] Périmètre géographique cohérent : un communiqué EU ne mentionne pas un produit non CE-marqué dans son périmètre
- [ ] Tout claim chiffré sourcé inline (paper avec DOI ou clearance summary)
- [ ] Comparaison prédicat (510k) non transformée en comparaison commerciale
- [ ] AKILA absent ou explicitement R&D si mentionné
- [ ] Disclaimer juridiction présent
- [ ] Citation CEO sans claim de performance non sourcé
- [ ] Aucune donnée patient identifiable
- [ ] Aucune comparaison nominative concurrent

## Livrables systématiques

1. **Communiqué de presse** version FR + EN si périmètre mixte
2. **Q&A inbound presse** (8-12 Q/R préparées) :
   - Indications + limites IFU
   - Performance et preuves
   - Intégration et déploiement
   - Comparaison paysage (factuelle, non dénigrante)
   - Roadmap (avec garde-fous)
3. **Variantes**
   - Tweet / LinkedIn announcement (renvoi vers communiqué)
   - Section investor update
4. **Notes de review** :
   - Liste des éléments à valider RA avant publication
   - Flag explicite : `🛑 BLOCKER` si quelque chose ne peut pas être publié en l'état
5. **Checklist de validation pré-publication** :
   - [ ] RA sign-off
   - [ ] CEO sign-off
   - [ ] Embargo confirmé avec attachés de presse
   - [ ] Mediakit prêt (logos, photos, press release PDF)
   - [ ] Page presse mise à jour sur le site
   - [ ] Investor update programmé

## Comportement face à un input douteux

Si quelque chose ne peut pas être substantié, **NE PAS l'écrire**. Insérer `[CHECK RA: …]` à l'endroit concerné et lister en notes ce qui doit être validé avant diffusion.

Si l'utilisateur demande explicitement un claim non-conforme, refuser et expliquer la raison en pointant la ligne concernée de `regulatory-guard.md`.

## Anti-patterns à refuser

- "Approved by the FDA" (utiliser "FDA cleared (510(k) #K…)")
- "First in class" / "first-ever" sans source
- "Best-in-class performance" / "industry-leading"
- Pourcentage de performance sans IC95% et sans paper référencé
- "Diagnostic" pour un produit non explicitement diagnostic
- Comparaison commerciale avec le prédicat 510(k)
- Citation CEO grandiloquente sans contenu factuel
- Communiqué sans disclaimer juridiction
- Mention d'AKILA comme produit
