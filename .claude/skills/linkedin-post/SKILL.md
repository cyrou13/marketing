---
name: linkedin-post
description: Drafte un post LinkedIn pour Avicenna.ai (corporate ou voix CEO Cyril) en respectant la voice, le regulatory-guard et les contraintes par persona. À utiliser dès qu'il s'agit de produire un post LinkedIn structurel — annonce, lancement, milestone, prise de position, cas client. Pour une simple réaction à une news, préférer le prompt `prompts/linkedin-reactive-news.md`.
---

# Skill — LinkedIn Post

## Avant de rédiger

Charger systématiquement :
- `brand/voice.md` (section canal LinkedIn corporate ou CEO selon compte)
- `brand/audiences.md` (persona prioritaire)
- `brand/regulatory-guard.md` (mots interdits, claims autorisés)
- `brand/proof-points.md` si un chiffre est cité
- `brand/glossary.md` si un produit / terme technique est cité

## Inputs requis (sinon : poser les questions, ne pas deviner)

1. **Compte cible** : Avicenna corporate / Cyril CEO / autre voix (préciser)
2. **Objectif business** du post (notoriété, recrutement, support sales, thought leadership, annonce)
3. **Audience prioritaire** parmi les personas d'`audiences.md`
4. **Angle / thèse** en une phrase
5. **Claims spécifiques** à inclure (avec source si performance produit)
6. **CTA** : lien démo / page produit / candidature / aucun

Inputs optionnels :
- Personnes à @-mentionner (max 5)
- Hashtags imposés
- Visuel disponible (photo équipe, schéma, screenshot)
- Embargo / date de publication

## Contraintes de format par compte

### Corporate Avicenna
- Longueur : 1200-1800 caractères
- Personne : "nous" / "Avicenna"
- Émojis : 0 ou 1 max, jamais "🚀" "🎉" "✨"
- Hashtags : 2-3 ciblés (ex : `#RadiologyAI`, `#MedTech`, `#MDR`)
- Hook : 2 lignes max avant le "voir plus"

### Cyril CEO
- Longueur : 800-1500 caractères
- Personne : "je"
- Émojis : 0 (ne jamais en mettre)
- Hashtags : 0-2, sobres
- Hook : observation, opinion ou question — pas une annonce produit
- Sujets de prédilection : AI souveraine européenne, MDR vs FDA, intégration AI dans le workflow radiologue, recrutement tech medical

## Structure recommandée

1. **Hook** (1-2 lignes) : observation, chiffre, paradoxe, question — jamais "Nous sommes ravis…"
2. **Tension / contexte** (2-4 lignes) : pourquoi le sujet existe
3. **Ce qu'on apporte** (2-4 lignes) : factuel, pas de superlatif
4. **Preuve** (1-2 lignes) : chiffre sourcé, paper, déploiement réel
5. **Clôture** : invitation, question ouverte, CTA discret

## Vérifications avant livraison

Checklist tirée de `regulatory-guard.md` :
- [ ] Aucun mot interdit présent (`diagnostic` hors usage validé, `remplace`, `100% précis`, `approuvé FDA`…)
- [ ] Tout claim de performance est traçable à `proof-points.md` ou à un paper cité
- [ ] L'indication mentionnée correspond à l'IFU du produit cité
- [ ] La juridiction (EU/US) est cohérente avec le claim
- [ ] AKILA n'est pas présenté comme produit clinique
- [ ] Aucune comparaison nominative dénigrante d'un concurrent
- [ ] Aucune donnée patient identifiable

## Livrables systématiques

Pour chaque post demandé, fournir :
1. **Le post** (formaté, prêt à coller)
2. **2 hooks alternatifs** (le rédacteur choisit)
3. **Notes** :
   - claims utilisés et leur source
   - vérifications regulatory-guard effectuées
   - suggestion visuelle (photo, schéma, screenshot)
   - hashtags retenus + alternatives
4. **Flag si revue requise** selon `regulatory-guard.md` §7

## Anti-patterns à refuser

- Hook "We're excited to announce…" / "Nous sommes ravis…"
- Liste à puces "we offer / you bring"
- Émojis décoratifs en début de ligne
- Affirmation de leadership non substantiée ("leader", "premier", "#1")
- Comparaison "contrairement à nos concurrents"
- Slogans hype ("révolutionner", "disruptive", "game changer")
- Plus de 4 hashtags
- Claim de performance sans source

## Si un input critique manque

NE PAS deviner. Poser 2-3 questions de clarification ciblées et attendre.

Si le rédacteur insiste pour un draft sans inputs : produire avec `[CHECK: …]` à chaque endroit où une donnée manque, et le signaler explicitement en tête.
