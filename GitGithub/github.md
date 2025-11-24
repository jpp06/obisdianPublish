# GitHub - Plateforme de collaboration

## Qu'est-ce que GitHub ?

GitHub est une plateforme web qui héberge des repositories Git et facilite la collaboration entre développeurs.

### Avantages de GitHub
- **Hébergement gratuit** pour les projets publics
- **Interface web intuitive** pour gérer les repositories
- **Outils de collaboration** : Issues, Pull Requests, Discussions
- **Intégration continue** avec GitHub Actions
- **Gestion des permissions** et de la sécurité
- **Réseau social** pour les développeurs

## Fonctionnalités principales

### 1. Issues - Gestion des tâches

Les Issues permettent de :
- **Décrire des bugs** à corriger
- **Proposer des améliorations** nouvelles fonctionnalités
- **Organiser le travail** en équipe
- **Suivre l'avancement** des tâches

#### Création d'une Issue
1. Aller sur l'onglet "Issues" du repository
2. Cliquer "New issue"
3. Remplir le titre et la description détaillée
4. Ajouter des labels (bug, enhancement, documentation, etc.)
5. Assigner la tâche à une personne
6. Créer des milestones pour organiser les versions

#### Interface approximative de création d'Issue
```
┌─────────────────────────────────────────────────────────────┐
│ GitHub > Repository > Issues > New issue                   │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  Title                                                      │
│  ┌─────────────────────────────────────────────────────┐   │
│  │ Ajouter authentification utilisateur               │   │
│  └─────────────────────────────────────────────────────┘   │
│                                                             │
│  Leave a comment                                            │
│  ┌─────────────────────────────────────────────────────┐   │
│  │ ## Description                                      │   │
│  │                                                     │   │
│  │ Il faut ajouter un système d'authentification      │   │
│  │ pour permettre aux utilisateurs de se connecter.   │   │
│  │                                                     │   │
│  │ ## Critères d'acceptation                          │   │
│  │ - [ ] Formulaire de connexion                      │   │
│  │ - [ ] Gestion des sessions                         │   │
│  │ - [ ] Protection des routes                        │   │
│  └─────────────────────────────────────────────────────┘   │
│                                                             │
│  Labels: [bug] [enhancement] [documentation] [+]           │
│  Assignees: [@username] [+]                                │
│  Projects: [Project Board] [+]                            │
│  Milestone: [v2.0] [+]                                    │
│                                                             │
│  [Cancel]                                    [Submit new issue] │
└─────────────────────────────────────────────────────────────┘
```

#### Labels utiles
- `bug` : Problème à corriger
- `feature` : Nouvelle fonctionnalité
- `documentation` : Amélioration de la doc
- `mise à jour` : ajout d'un camping
- `priority: high` : Urgent

### 2. Pull Requests - Review du code

Les Pull Requests (PR) permettent de :
- **Proposer des changements** avant de les intégrer
- **Faire des reviews** de code en équipe
- **Discuter des modifications** avant merge (review)
- **Maintenir la qualité** du code

#### Workflow d'une Pull Request
1. **Créer une branche** pour la fonctionnalité
2. **Développer** et commiter les changements
3. **Pousser** la branche vers GitHub
4. **Créer une PR** depuis l'interface GitHub pour cette branche
5. **Attendre la review** des collègues
6. **Corriger** si nécessaire
7. **Merger** après approbation

#### Interface approximative de création de Pull Request
```
┌───────────────────────────────────────────────────────────┐
│ GitHub > Repository > Pull requests > New pull request    │
├───────────────────────────────────────────────────────────┤
│                                                           │
│  Compare changes                                          │
│  ┌─────────────────────────────────────────────────────┐  │
│  │ base: main ← compare: feature/auth-system           │  │
│  └─────────────────────────────────────────────────────┘  │
│                                                           │
│  Able to merge. These branches can be automatically       │
│  merged.                                                  │
│                                                           │
│  Write                                                    │
│  ┌─────────────────────────────────────────────────────┐  │
│  │ ## Description                                      │  │
│  │                                                     │  │
│  │ Ajoute un système d'authentification complet        │  │
│  │                                                     │  │
│  │ ## Changements                                      │  │
│  │ - [x] Formulaire de connexion                       │  │
│  │ - [x] Gestion des sessions                          │  │
│  │ - [x] Protection des routes                         │  │
│  │ - [x] Tests unitaires                               │  │
│  │                                                     │  │
│  │ ## Tests                                            │  │
│  │ - [x] Tests passent localement                      │  │
│  │ - [x] Tests passent sur CI                          │  │
│  └─────────────────────────────────────────────────────┘  │
│                                                           │
│  Reviewers: [@username] [+]                               │
│  Assignees: [@username] [+]                               │
│  Labels: [enhancement] [+]                                │
│  Projects: [Project Board] [+]                            │
│  Milestone: [v2.0] [+]                                    │
│                                                           │
│  [Create pull request]                                    │
└───────────────────────────────────────────────────────────┘
```

#### Interface approximatiev de review de Pull Request
```
┌───────────────────────────────────────────────────────────┐
│ Pull Request #42: Add authentication system               │
├───────────────────────────────────────────────────────────┤
│                                                           │
│  Conversation  Files changed  Commits                     │
│                                                           │
│  ┌─────────────────────────────────────────────────────┐  │
│  │ @developer requested review from @reviewer          │  │
│  │                                                     │  │
│  │ ## Summary                                          │  │
│  │ This PR implements a complete authentication        │  │
│  │ system with login, session management, and          │  │
│  │ route protection.                                   │  │
│  │                                                     │  │
│  │ ## Files changed                                    │  │
│  │ - `src/auth/login.js` (new)                         │  │
│  │ - `src/auth/session.js` (new)                       │  │
│  │ - `src/middleware/auth.js` (new)                    │  │
│  │ - `tests/auth.test.js` (new)                        │  │
│  └─────────────────────────────────────────────────────┘  │
│                                                           │
│  ┌─────────────────────────────────────────────────────┐  │
│  │ @reviewer left a review                             │  │
│  │                                                     │  │
│  │ V Looks good! Just a few minor suggestions:         │  │
│  │                                                     │  │
│  │ - Consider adding input validation                  │  │
│  │ - Maybe add rate limiting for login attempts        │  │
│  │                                                     │  │
│  │ Overall, great implementation!                      │  │
│  └─────────────────────────────────────────────────────┘  │
│                                                           │
│  [Merge pull request] [Close pull request]                │
└───────────────────────────────────────────────────────────┘
```

#### Types de merge
- **Create a merge commit** : Préserve l'historique des branches
- **Squash and merge** : Combine tous les commits en un seul (MODE PRÉFÉRÉ)
- **Rebase and merge** : Historique linéaire sans commit de merge

### 3. GitHub Projects - Organisation

GitHub Projects permet de :
- **Organiser le travail** en tableaux Kanban
- **Suivre l'avancement** des tâches
- **Planifier les releases**
- **Gérer les sprints**

#### Structure minimale d'un projet
- **To Do** : Tâches à faire
- **In Progress** : En cours de développement
- **Review** : En attente de review
- **Done** : Terminé

### 4. GitHub Actions - CI/CD

GitHub Actions automatise :
- **Tests automatiques** à chaque commit
- **Déploiement** automatique
- **Génération de documentation**
- **Notifications** et rapports

#### Exemple de workflow
```yaml
name: Tests
on: [push, pull_request]
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Run tests
        run: npm test
```

## Workflows de collaboration

### Workflow basique sur fork
1. **Fork** le repository original
2. **Clone** ton fork localement
3. **Créer une branche** pour ta fonctionnalité
4. **Développer** et commiter
5. **Pousser** vers ton fork
6. **Créer une Pull Request** vers le repository original
7. **Attendre la review** et les corrections
8. **Merger** après approbation

### Workflow avec Issues
1. **Créer une Issue** pour décrire le besoin
2. **Créer une branche** depuis l'Issue (GitHub le fait automatiquement)
3. **Développer** la solution
4. **Créer une PR** liée à l'Issue
5. **Review** et corrections
6. **Merge** : l'Issue se ferme automatiquement

## Bonnes pratiques

### Messages de commit
- **Format** : `type: description courte`
- **Types** : `feat`, `fix`, `docs`, `style`, `refactor`, `test`, `chore`
- **Exemple** : `feat: ajouter authentification utilisateur`

### Nommage des branches
- **feature** : `feature/nom-descriptif`
- **fix** : `fix/numero-issue`
- **hotfix** : `hotfix/description-urgence`
- **docs** : `docs/description`

### Review de code
- **Vérifier** la logique et la lisibilité
- **Tester** les changements
- **Commenter** de manière constructive
- **Approuver** seulement si satisfait

### Gestion des Issues
- **Décrire clairement** le problème ou besoin
- **Ajouter des labels** appropriés
- **Assigner** aux bonnes personnes
- **Fermer** quand résolu

## Sécurité et permissions

### Niveaux d'accès
- **Read** : Peut voir le code
- **Write** : Peut modifier le code
- **Admin** : Peut gérer les paramètres
- **Owner** : Propriétaire du repository

### Bonnes pratiques de sécurité
- **Ne jamais** commiter de secrets (mots de passe, clés API)
- **Utiliser** des variables d'environnement
- **Configurer** des branches protégées
- **Activer** les reviews obligatoires
- **Utiliser** des tokens d'accès personnels

## Intégrations utiles

### Outils de développement
- **VS Code** : Extension GitHub
- **GitHub Desktop** : Interface graphique
- **GitKraken** : Client Git avancé

### Services externes
- **Travis CI** : Intégration continue
- **CircleCI** : CI/CD
- **Netlify** : Déploiement web
- **Heroku** : Déploiement d'applications

## Conseils pour débuter

### Première utilisation
1. **Créer un compte** GitHub
2. **Configurer** Git avec ton nom et email
3. **Générer** une clé SSH
4. **Créer** ton premier repository
5. **Cloner** et faire ton premier commit

### Apprentissage progressif
1. **Commencer** par les bases (clone, commit, push)
2. **Apprendre** les branches et merges
3. **Découvrir** les Issues et Pull Requests
4. **Explorer** GitHub Actions
5. **Contribuer** à des projets open source

GitHub est un outil puissant qui facilite énormément la collaboration en développement. Plus tu l'utilises, plus tu découvres ses possibilités !
