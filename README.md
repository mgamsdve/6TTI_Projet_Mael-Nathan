# Projet Mael & Nathan

## Binôme et rôles

- **Mael Dayani Poty** — Dieu du dépôt GitHub
- **Nathan Beaujean** — Dieu du temps

- mardi 08/09/26

## Conventions Git

- `main` contient les versions validées du projet.
- `dev` rassemble le travail du binôme avant validation pour `main`.
- Pour chaque issue, créer une branche depuis `dev` : `codex/<numero>-<description>`, par exemple `codex/11-initialisation-codeigniter`.
- Faire des commits courts, avec un message en français : `type: description`. Types utilisés : `feat` (fonctionnalité), `fix` (correction), `docs` (documentation), `chore` (configuration). Exemple : `docs: ajouter les conventions Git`.
- Ouvrir une pull request vers `dev` lorsque le travail de l’issue est prêt. Mentionner l’issue concernée et expliquer comment le résultat a été vérifié.
- L’autre membre du binôme relit la pull request avant la fusion.
- Après fusion, supprimer la branche de travail. `main` et `dev` restent les deux branches permanentes.
- Pour une version validée ensemble, ouvrir une pull request de `dev` vers `main`.
- Ne jamais ajouter de clé API, de mot de passe ou de données personnelles au dépôt.

### Démarrer une tâche

```bash
git switch dev
git pull --ff-only origin dev
git switch -c codex/8-test-ocr
```

Après les modifications :

```bash
git add <fichiers-modifies>
git commit -m "feat: ajouter le test OCR"
git push -u origin codex/8-test-ocr
```

Sur GitHub, créer ensuite une pull request avec `dev` comme branche de destination et demander la relecture de l’autre membre : Nathan relit le travail de Maël, Maël relit celui de Nathan. Avant de commencer, se répartir les issues dans GitHub Project pour éviter de modifier les mêmes fichiers en même temps.

La mise en place initiale de ces conventions (issue #12) est publiée directement sur `main` et `dev`. Les tâches suivantes suivent le processus de pull request décrit ci-dessus.
