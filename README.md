# Projet Mael & Nathan

## Démarrage local

Il faut PHP 8.2 ou plus récent, les extensions PHP `intl` et `mbstring`,
et Composer 2.0.14 ou plus récent. Aucune base de données n’est nécessaire
pour afficher la page d’accueil.

### Sur Windows

1. Ouvrir PowerShell et lancer `php -v`. Si PowerShell ne reconnaît pas
   `php`, ajouter le dossier qui contient `php.exe` à la variable
   d’environnement `Path`, puis rouvrir PowerShell.
2. Lancer `php -m` et vérifier que `intl`, `mbstring`, `openssl` et `zip`
   figurent dans la liste. Les deux dernières permettent à Composer de
   télécharger et d’extraire les dépendances. S’il manque une extension,
   lancer `php --ini` pour trouver le fichier `php.ini` chargé. Si aucun
   fichier n’est chargé, copier `php.ini-development` en `php.ini` à côté
   de `php.exe`. Dans `php.ini`, retirer le point-virgule devant les lignes
   `extension=...` correspondantes et vérifier que `extension_dir` pointe
   vers le dossier `ext` de PHP. Relancer `php -m` pour vérifier.
3. Installer Composer avec [l’installateur officiel pour Windows](https://getcomposer.org/doc/00-intro.md#installation-windows).
   Si l’installateur demande où est PHP, sélectionner le `php.exe` affiché en
   premier par `where.exe php`. Ouvrir un nouveau PowerShell et vérifier
   l’installation avec `composer --version`.
4. Récupérer le projet depuis GitHub. Avec Git, cloner le dépôt et basculer sur
   `dev` après la fusion. Sans Git, sélectionner la branche sur GitHub,
   cliquer sur **Code → Download ZIP**, puis extraire l’archive. Pour tester
   avant la fusion, utiliser la branche source de la pull request.
5. Ouvrir PowerShell dans le dossier qui contient `composer.json` et lancer
   ces commandes.

   ```powershell
   composer install --no-dev
   if (-not (Test-Path .env)) { Copy-Item .env.example .env }
   php spark serve
   ```

### Sur macOS ou Linux

Depuis le dossier du projet, avec PHP et Composer déjà installés, lancer les
commandes suivantes.

```sh
composer install --no-dev
test -f .env || cp .env.example .env
php spark serve
```

Ouvrir [http://localhost:8080](http://localhost:8080). La page de bienvenue
de CodeIgniter doit s’afficher. Arrêter le serveur avec `Ctrl+C`.

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
