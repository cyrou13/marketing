# Glossary — Avicenna.ai

> Vocabulaire produit et technique avec définitions canoniques et niveaux d'explication selon audience.
> À mettre à jour quand un nouveau produit ou concept est introduit.

## Convention

Pour chaque terme :
- **One-liner** : phrase de 10-15 mots pour audience non-experte
- **Pour radiologue** : version technique correcte
- **Pour CIO/IT hôpital** : angle intégration / déploiement
- **Pour investisseur** : angle marché / différenciation

---

## AKILA (Avicenna foundation model)

- **One-liner** : modèle de fondation d'Avicenna entraîné sur des millions de scanners pour démultiplier la création d'applications cliniques.
- **Pour radiologue** : [À COMPLÉTER — architecture, modalités couvertes, performance attendue]
- **Pour CIO** : [À COMPLÉTER — implications déploiement, mise à jour]
- **Pour investisseur** : actif stratégique sous-tendant la roadmap produit, accélérant le time-to-clearance des nouvelles indications.

## CINA / Cinaria (plateforme produit)
[À COMPLÉTER]

## CT Perfusion (CTP)

- **One-liner** : technique d'imagerie qui mesure le flux sanguin cérébral pour identifier les zones de tissu cérébral encore récupérables après un AVC.
- **Pour radiologue** : acquisition CT dynamique avec injection de produit de contraste, permettant le calcul de cartes paramétriques (CBF, CBV, MTT, Tmax) via déconvolution. Avicenna fournit [préciser indication exacte].
- **Pour CIO** : [intégration PACS / RIS, modalités CT compatibles]
- **Pour investisseur** : marché AVC en forte croissance, indication clé pour les centres de neuroradiologie interventionnelle.

## Jarvis Stack (technique interne — NE PAS confondre avec le produit Jarvis personnel)

> ⚠️ Communication externe : éviter d'introduire "Jarvis" auprès des audiences externes sauf contexte technique B2B précis. Préférer "stack technologique Avicenna" ou termes des couches.

- **Ectopia** : [À COMPLÉTER — couche 1]
- **Warehouse** : [À COMPLÉTER — couche 2]
- **Jarvis Forge** : [À COMPLÉTER — couche 3]

## Indications cliniques couvertes

| Indication | Produit Avicenna | CE | FDA | Notes |
|-----------|------------------|----|----|-------|
| Embolie pulmonaire (CT thorax) | CINA-CHEST / CINA-iPE | ? | ? | [À VÉRIFIER avec affaires réglementaires] |
| LVO (occlusion gros vaisseau cérébral) | CINA-LVO | ? | ? | |
| ASPECTS (score AVC) | CINA-ASPECTS | ? | ? | |
| ICH (hémorragie intracrânienne) | ? | ? | ? | |
| Anévrisme aortique / EVAR follow-up | ? | ? | ? | Cf. RFI Medtronic |
| ... | | | | |

[À COMPLÉTER de manière exhaustive — c'est la table de référence pour ne pas faire de claim hors indication]

## Termes du marché à connaître

- **MDR** : Medical Device Regulation (UE) 2017/745
- **510(k)** : voie de clearance FDA pour dispositifs équivalents à un prédicat
- **De Novo** : voie FDA pour dispositifs sans prédicat
- **CADx vs CADt vs CADe** : Computer-Aided Diagnosis / Triage / Detection — distinction régulatoire importante
- **PACS / RIS / VNA** : systèmes hospitaliers d'imagerie
- **DICOM** : standard d'échange d'images médicales
- **HL7 / FHIR** : standards d'échange de données cliniques

## Concurrents (vocabulaire pour les évoquer correctement)

> Cf. `references/competitors/` pour la veille détaillée.

- **Aidoc** : positionner par rapport à Avicenna sans dénigrer ; à mentionner uniquement si comparaison demandée
- **RapidAI** : idem
- **Harrison.ai** : idem
- **viz.ai** : idem
- [À COMPLÉTER]

## Ce qu'on ne dit pas (anti-patterns vocabulaire)

- Pas "produits" dans la communication corporate, préférer "solutions"
- Pas "users" en français, préférer "radiologues" ou "professionnels de santé"
- Pas "deal" ou "client" en B2B medtech corporate, préférer "site clinique", "centre partenaire", "hôpital"
