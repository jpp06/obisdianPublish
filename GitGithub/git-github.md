# Git - Workflow avec GitHub

## Table des matières
- [Workflow de base](#workflow-de-base)
- [Workflow avec Issues](#workflow-avec-issues)
- [Bonnes pratiques](#bonnes-pratiques)

## Workflow de base

### 1. Cloner un repository
```bash
git clone https://github.com/user/repo.git
cd repo
```

### 2. Créer une branche de feature
```bash
git checkout -b feature/nouvelle-fonctionnalite
```

### 3. Développer et commiter
```bash
git add fichier.py
git commit -m "ajouter nouvelle fonctionnalité"
git push origin feature/nouvelle-fonctionnalite
```

### 4. Créer une Pull Request
- Aller sur GitHub
- Cliquer sur "Compare & pull request"
- Remplir la description
- Assigner des reviewers

### 5. Fusionner après review
```bash
git checkout main
git fetch origin
git merge origin/main
git branch -d feature/nouvelle-fonctionnalite
```

## Workflow avec Issues

### 1. Créer une Issue
- Aller sur GitHub → onglet "Issues"
- Cliquer "New issue"
- Remplir titre et description
- Ajouter des labels (bug, enhancement, etc.)

### 2. Créer la branche depuis l'Issue
- Sur GitHub, dans l'issue
- Cliquer "Create a branch" (en bas à droite)
- GitHub crée automatiquement une branche nommée `issue-123-description`

### 3. Travailler sur l'Issue
```bash
git fetch origin
git checkout issue-123-description
# ... développement ...
git add .
git commit -m "fix: corriger le bug de connexion utilisateur"
git push
```

### 4. Créer la Pull Request
- Retourner sur GitHub → onglet "Code"
- GitHub propose automatiquement "Compare & pull request"
- Remplir le titre de la PR (souvent pré-rempli)
- Assigner des reviewers si nécessaire
- La PR est automatiquement connectée à l'issue
- GitHub fermera l'issue au merge

### 5. Fusionner via GitHub
- Attendre l'approbation des reviewers
- Cliquer "Merge pull request" sur GitHub
- Choisir le type de merge :
  - **Create a merge commit** : préserve l'historique des branches
  - **Squash and merge** : combine tous les commits en un seul
  - **Rebase and merge** : historique linéaire sans commit de merge
- Confirmer le merge
- Supprimer la branche (optionnel, GitHub le propose)

### 6. Suivi des Issues
- **assigner** des personnes
- **ajouter** des labels
- **créer** des milestones
- **commenter** pour donner des infos

## Bonnes pratiques

### Messages de commit
- **format** : `type: description courte`
- **types** : `feat`, `fix`, `docs`, `style`, `refactor`, `test`
- **exemple** : `feat: ajouter authentification utilisateur`

### Nommage des branches
- **feature** : `feature/nom-descriptif`
- **fix** : `fix/numero-issue`
- **hotfix** : `hotfix/description-urgence`

### Workflow recommandé
1. **toujours** partir de `main` à jour
2. **une branche** = une fonctionnalité
3. **tester** avant de push
4. **review** obligatoire avant merge
5. **nettoyer** les branches après merge
