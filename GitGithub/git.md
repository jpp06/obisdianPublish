# Git - Concepts de base

## Table des matières
- [Qu'est-ce que git ?](#quest-ce-que-git-)
- [Concepts fondamentaux](#concepts-fondamentaux)
- [Workflow de base](#workflow-de-base)
- [Pourquoi git ?](#pourquoi-git-)
- [Configuration initiale](#configuration-initiale)
- [Commandes de base](#commandes-de-base)
- [Utilisation minimaliste des branches](#utilisation-minimaliste-des-branches)
- [Pour aller plus loin](#pour-aller-plus-loin)
- [Commandes à risques](#commandes-à-risques)

## Qu'est-ce que git ?

Git est un système de contrôle de version distribué. Il permet de :
- sauvegarder l'historique de tes fichiers
- travailler à plusieurs sur le même projet
- revenir en arrière si nécessaire
- créer des branches pour expérimenter ou cloisonner le travail

## Concepts fondamentaux

### Repository (dépôt)
Un dossier qui contient ton projet et tout son historique git (dans le réportoire .git).

### Commit
Une sauvegarde de l'état de tes fichiers à un moment donné. Chaque commit a :
- un identifiant unique (hash)
- un message descriptif
- une date et un auteur

### Branches
Des versions parallèles de ton code. Par défaut, tu travailles sur la branche `main`.

### Remote
Un repository distant (comme sur GitHub) avec lequel tu peux synchroniser ton travail local.

### Origin
`origin` est le nom par défaut du remote principal. Quand tu clones un repo, git crée automatiquement un remote appelé `origin` qui pointe vers l'URL d'origine.

### Working directory
Le dossier où tu travailles actuellement sur tes fichiers.

### Staging area
Une zone intermédiaire où tu prépares tes fichiers avant de les commiter.

## Workflow de base

1. **modifier** tes fichiers dans le working directory
2. **ajouter** les fichiers modifiés au staging area (`git add`)
3. **commiter** les changements (`git commit`)
4. **pousser** vers le remote si nécessaire (`git push`)

## Pourquoi git ?

- **sécurité** : tu ne perds jamais ton travail
- **collaboration** : plusieurs personnes peuvent travailler ensemble
- **flexibilité** : tu peux expérimenter sans risque
- **traçabilité** : tu sais qui a fait quoi et quand


## Configuration initiale

### Configuration de base
```bash
git config --global user.name "Ton Nom"
git config --global user.email "ton.email@example.com"
```

### Vérifier la configuration
```bash
git config --list
```

### Configuration de l'éditeur
```bash
git config --global core.editor "code --wait"  # pour VS Code
git config --global core.editor "nano"         # pour nano
# ...
```

### Clé SSH pour GitHub
1. Générer une clé SSH :
```bash
ssh-keygen -t ed25519 -C "ton.email@example.com"
```

2. Ajouter la clé à l'agent SSH :
```bash
ssh-add ~/.ssh/id_ed25519
```

3. Copier la clé publique :
```bash
cat ~/.ssh/id_ed25519.pub
```

4. Ajouter cette clé dans GitHub (`Settings` > `SSH and GPG keys`)

## Commandes de base

### Initialiser un repository
```bash
git init           # créer un nouveau repo dans le dossier actuel
git clone <url>    # cloner un repo existant
```

### Vérifier l'état
```bash
git status         # voir les fichiers modifiés/ajoutés
git log --oneline  # voir l'historique des commits
```

### Ajouter des fichiers
```bash
git add fichier.txt  # ajouter un fichier spécifique
git add .            # ⚠️ ajouter tous les fichiers modifiés (à utiliser avec précaution, voir plus bas)
git add -A           # ajouter tous les fichiers (y compris supprimés)
```

### Commiter
```bash
git commit -m "message"  # commiter avec un message
git commit -am "message" # ⚠️ ajouter et commiter en une fois (à utiliser avec précaution, voir plus bas)
```

### Synchroniser avec le remote
```bash
git push         # envoyer les commits vers le remote
git pull         # ⚠️ récupérer les changements du remote (à utiliser avec précaution, voir plus bas)
git fetch        # récupérer sans fusionner
git remote -v    # voir les remotes configurés
```

## Utilisation minimaliste des branches

### Créer et basculer entre branches
```bash
git branch nom-branche      # créer une nouvelle branche
git checkout nom-branche    # basculer vers une branche
git checkout -b nom-branche # créer et basculer en une fois
git branch                  # lister les branches locales
git branch -a               # lister toutes les branches (locales et distantes)
```

### Fusionner des branches
```bash
git checkout main          # revenir sur main
git merge nom-branche      # fusionner la branche dans main
git branch -d nom-branche  # supprimer la branche locale
```

### Workflow simple avec branches
1. **développement** : travailler sur une branche `feature/nouvelle-fonctionnalite`
2. **test** : tester tes changements
3. **fusion** : revenir sur `main` et fusionner
4. **nettoyage** : supprimer la branche de feature

### Bonnes pratiques
- **nommage** : utiliser des noms descriptifs (`feature/login`, `fix/bug-123`)
- **une branche = une fonctionnalité** : ne pas mélanger plusieurs features
- **main toujours stable** : ne jamais commiter directement sur main

## Pour aller plus loin

### Stash - Mettre de côté temporairement
```bash
git stash          # mettre de côté les changements non commités
git stash pop      # récupérer les changements mis de côté
git stash list     # voir la liste des stash
git stash drop     # supprimer le dernier stash
```

### Rebase - Réorganiser l'historique
```bash
git rebase main        # réorganiser les commits par rapport à main
git rebase -i HEAD~3   # rebase interactif sur les 3 derniers commits
```

### Merge - Fusionner des branches
```bash
git merge nom-branche          # fusionner une branche (créé un commit de merge)
git merge --no-ff nom-branche  # fusionner sans fast-forward
git merge --squash nom-branche # fusionner en un seul commit
```

### Quand utiliser quoi ?
- **stash** : quand tu veux changer de branche rapidement
- **rebase** : pour avoir un historique linéaire et propre
- **merge** : pour préserver l'historique des branches



## Commandes utiles
```bash
# Voir l'état du repository
git status

# Voir l'historique
git log --oneline

# Voir les différences
git diff

# Voir les branches
git branch -a

# Voir les remotes
git remote -v

# Annuler des changements non commités
git checkout -- fichier.txt

# Voir les changements d'un commit
git show commit-hash
```

### En cas de problème
- **Changements non désirés** : `git checkout -- fichier.txt`
- **Commit mal fait** : `git commit --amend`
- **Branche mal nommée** : `git branch -m ancien-nom nouveau-nom`
- **Fichier ajouté par erreur** : `git reset HEAD fichier.txt`
- **Dernier commit à annuler** : `git reset --soft HEAD~1`

## Commandes à risques

### `git add .` (dangereux)
```bash
git add .
```
**Pourquoi c'est risqué :**
- Ajoute **tous** les fichiers modifiés, même ceux non désirés
- Peut inclure des fichiers temporaires, logs, ou secrets
- Difficile de revenir en arrière une fois fait

**Exemples de fichiers non désirés :**
- `config.local.py` (configuration avec mots de passe)
- `debug.log` (fichiers de logs volumineux)
- `temp/` (dossier temporaire)
- `.env` (variables d'environnement sensibles)

**Alternative sécurisée :**
```bash
git add fichier1.py fichier2.js  # ajouter des fichiers spécifiques
git status                       # vérifier avant d'ajouter
```

### `git commit -am` (dangereux)
```bash
git commit -am "message"
```
**Pourquoi c'est risqué :**
- Ajoute **et** commite en une fois
- Pas de contrôle sur ce qui est ajouté
- Peut commiter des changements non voulus

**Exemples de changements non voulus :**
- Modifications de debug laissées par erreur
- Fichiers de configuration modifiés temporairement
- Changements expérimentaux non finalisés
- Fichiers de test avec des données sensibles

**Alternative sécurisée :**
```bash
git add fichier.py              # ajouter explicitement
git commit -m "message"         # commiter séparément
```

### Pourquoi éviter `git pull` ?

#### `git pull` (dangereux)
```bash
git pull
```
**Ce que ça fait :**
- Récupère les changements du remote
- **Fusionne automatiquement** avec ta branche locale
- Peut créer des commits de merge non désirés
- Tu n'as pas de contrôle sur le processus

#### `git fetch` + `git merge` (sécurisé)
```bash
git fetch              # récupère les changements sans fusionner
git merge origin/main  # fusionne de manière contrôlée
```

**Les gains :**
1. **Contrôle** : tu vois d'abord ce qui va changer avec `git fetch`
2. **Inspection** : tu peux vérifier les changements avant de fusionner
3. **Choix** : tu peux choisir entre `merge` ou `rebase`
4. **Sécurité** : pas de fusion automatique surprise

#### Exemple concret
```bash
git fetch                   # récupère les changements
git log HEAD..origin/main   # voir les nouveaux commits
git diff HEAD origin/main   # voir les différences
git merge origin/main       # fusionner en connaissance de cause
```
C'est plus de commandes mais beaucoup plus sûr !
