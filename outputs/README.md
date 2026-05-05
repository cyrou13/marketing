# Outputs

Dossier de destination des contenus générés par les skills et workflows.

## Convention de nommage

```
outputs/YYYY-MM-DD-<type>-<short-name>/
```

Exemples :
- `outputs/2026-05-12-clearance-cina-aspects/`
- `outputs/2026-06-paper-stroke-validation/`
- `outputs/2026-07-case-chu-bordeaux/`
- `outputs/2026-09-newsletter/`

## Structure type d'un dossier workflow

Voir les workflows pour la structure exacte. Exemple `new-clearance` :

```
outputs/2026-05-12-clearance-cina-aspects/
├── 00-regulatory-extract.md
├── 01-message-matrix.md
├── 02-press-release.md
├── 03a-linkedin-corporate.md
├── 03b-linkedin-ceo.md
├── 04-newsletter-section.md
├── 05-blog-article.md
├── 06-inbound-faq.md
└── 07-review-report.md
```

## Versioning

Les outputs sont **ignorés par Git** par défaut (cf. `.gitignore` local) — ce sont des drafts en cours, pas la source de vérité.

Si un output mérite d'être archivé (audit, réutilisation, post-perfs), le déplacer vers `references/past-content/` après publication.
