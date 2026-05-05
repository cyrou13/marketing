# Workflows agentiques

Pipelines multi-étapes qui chaînent plusieurs skills pour produire en une commande tout l'amplification d'un événement majeur.

## Quand un workflow vaut le coup

Un workflow remplace un Skill quand :
- Plusieurs livrables doivent être produits cohérents entre eux (ex: post LinkedIn + article blog + section newsletter)
- Le matériel source est complexe (ex: extraire les claims autorisés d'un 510(k) summary avant de rédiger)
- Une étape de review automatique a du sens (ex: passer tous les drafts par regulatory-guard.md avant de livrer)

## Workflows disponibles

- `new-clearance.md` — nouvelle clearance FDA ou CE → tous les canaux
- `new-paper.md` — publication d'un paper → blog + LinkedIn + newsletter
- `case-study-pipeline.md` — interview client → étude de cas finale prête à diffuser

## Comment exécuter

Dans Claude Code, depuis la racine du repo :

```bash
claude
```

Puis donne la commande équivalente : *"Exécute le workflow new-clearance avec les inputs suivants : [...]"*. Claude lit le fichier `workflows/new-clearance.md` et enchaîne les étapes.

À terme, on peut passer ces workflows en commandes slash custom Claude Code ou en agents dédiés du framework BMAD-MD.
