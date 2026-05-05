# Guide d'entretien client pour produire une étude de cas

## Quand l'utiliser

Avant le rendez-vous d'interview du référent clinique partenaire. Te permet (ou à la marketeuse) de structurer une visio de 45-60 min qui produira ensuite des inputs riches pour le skill `case-study`.

## Préparation (avant l'interview)

- [ ] Vérifier qu'un accord écrit existe pour publier
- [ ] Préparer un NDA inversé si l'hôpital demande à valider tout le contenu avant publication
- [ ] Demander quelles données chiffrées sont déjà disponibles (volumétrie, KPIs, période)
- [ ] Préparer un script d'autorisation enregistrement (si transcription souhaitée)
- [ ] Bloquer 60 min minimum, prévoir 75 min pour ne pas couper

## Structure d'interview (45-60 min)

### Bloc 1 — Contexte hôpital (10 min)
- Quelle est votre fonction exacte ? Depuis quand ?
- Pouvez-vous décrire votre service en 3-4 chiffres clés (lits, équipe radio, volumétrie scans/an, types de gardes) ?
- Quels sont les 2-3 défis majeurs auxquels votre service fait face en 2026 ?
- Sur quelles indications cliniques avez-vous le plus de pression (volume, urgence, sécurité diagnostique) ?

### Bloc 2 — Avant Avicenna (10 min)
- Comment fonctionnait le workflow sur [indication] avant le déploiement ?
- Quels étaient les problèmes concrets que vous viviez (pas les "il paraît que", les vrais) ?
- Aviez-vous regardé d'autres solutions AI ? Pourquoi celles-là n'ont pas été retenues ?
- Quels étaient les KPIs que vous mesuriez déjà ?

### Bloc 3 — Le déploiement (10 min)
- Comment s'est passée l'intégration technique (PACS, RIS, durée, blockers) ?
- Qui a été impliqué côté hôpital (DSI, biomed, radiologues, direction) ?
- Comment avez-vous formé / accompagné les radiologues à l'usage ?
- Y a-t-il eu des résistances ? Comment ont-elles été levées ?

### Bloc 4 — Les résultats (15 min)
- Quels KPIs ont changé ? Avant / après / sur quelle période ?
- Avez-vous observé des bénéfices que vous n'aviez pas anticipés ?
- Y a-t-il eu des points de friction qui persistent ?
- Comment les radiologues utilisent-ils l'outil aujourd'hui (en routine, en backup, en double lecture) ?

### Bloc 5 — Citations et perspectives (10 min)
- Si vous deviez recommander Avicenna à un confrère, que diriez-vous en 2-3 phrases ?
- Quel conseil donneriez-vous à un service qui s'apprête à déployer une AI radiologique ?
- Qu'attendez-vous d'Avicenna pour les 12 prochains mois ?

## Après l'interview

- [ ] Envoyer dans les 24h un récapitulatif des points clés et demander confirmation des chiffres
- [ ] Faire valider 2-3 propositions de citation verbatim par écrit
- [ ] Demander quelles données sont publiables sans autorisation supplémentaire vs nécessitant validation hôpital / direction
- [ ] Prendre note des photos / captures que l'hôpital autorise

## Prompt pour générer l'étude de cas après l'interview

```
Charge brand/voice.md, brand/regulatory-guard.md, brand/audiences.md.
Active le skill case-study.

Voici les inputs de l'interview client :

[Coller le résumé structuré bloc par bloc]

Citations validées par écrit (exactes) :
1. "..."  — [Nom, fonction, hôpital]
2. "..."

Données chiffrées validées avec accord de publication :
- [...]

Format final : [PDF 2 pages / 4 pages]
Audience cible : [...]
Confidentialités : [...]

Génère le draft + les notes de validation requises avant publication.
```
