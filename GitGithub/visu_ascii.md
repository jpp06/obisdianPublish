# Visualisation Git et Branches (ASCII)

## Schéma des branches

```
main
  ├── feature/login
  │   ├── commit 1
  │   ├── commit 2
  │   └── commit 3 ─┐
  │                 └─ merge ┐
  ├─←────────────────────────┘
  │
  ├── feature/payment
  │   ├── commit A
  │   └── commit B ─┐
  │                 └─ merge ┐
  ├─←────────────────────────┘
  │
  ...
```

## Vue locale vs origin

```
Local Repository                                 Remote Repository (origin)
│                                                ├── main
├── main        ←─  (git pull)                   |
│                                                | (création branche via issue sur GitHub)
│                                                ├── feature/login
├── feature/login ←─ (git checkout f../l..)      |   |
│   |   (boulot 1)                               |   |
|   ├─→ commit 1  ─→ (git commit ...; git push;) ──→─┼── commit 1
│   |   (boulot 2)                               |   |
│   ├─→ commit 2  ─→ (git commit ...; git push;) ──→─┼── commit 2
│   |   (boulot 3)                               |   |
│   └─→ commit 3  ─→ (git commit ...; git push;) ──→─┴── commit 3 ───────→──────────┐
|                                                ├─←───  merge/delete (via GitHub) ─┘
├─←─  git checkout main; git fecth; git pull ─←──┤
| main local et distant au même point de commit  |
```

## Et concrètement, chez nous

```
 Ma machine                                       ║ Partagée
                                                  ║ Compte JPP                        Compte partagé
==================================================╬============================================================
 Local repository                                 ║ Local repository                  Pas de Local repository
 │                                                ║ │
 ├── main                                         ║ ├── main (copie de production)
 │                                                ║ ├─────→ copie vers compte debian ─→
 ├── -0- feature/background-grisé                 ║ |
 │   ├── commit 1                                 ║ │
 │   ├── commit 2                                 ║ │
 │   └── commit 3                                 ║ │
 │                                                ║ │
 ├─→ -1- git push origin feature/background-grisé ║ |
 │                                                ║ │
 ├─← -3- git pull origin main                     ║ ├─← -4- git pull origin main (récupération des changements)
 │   commit id: abc123 (synchronisé partout)      ║ │   commit id: abc123 (synchronisé partout)
 |                                                ║ |
 │                                                ║ |   -5- copie vers compte debian ─→
 |                                                ║ |                                  -6- docker-compose up
===============================================================================================================
                                            Git / GitHub
                                            Remote repository (origin)
                                            ├── main
                                            ├── feature/background-grisé (supprimée après merge)
                                            │   ├── commit 1
                                            │   ├── commit 2
                                            │   └── commit 3 ───────────→──────────┐
                                            | -2- Pull Request + Merge sur GitHub ─┘
                                            | commit id: abc123
```

### Workflow concret

0. **Développement local** : travail sur ta machine
1. **Push vers GitHub** : `git push origin ma-branche`
2. **Pull Request et Merge** : création via GitHub pour review et fusion dans main via GitHub
3. **Synchronisation ma machine** : `git pull origin main` pour récupérer les changements
4. **Synchronisation Hector** : `git pull origin main` pour récupérer les changements en production
5. **Copie** : copie du repository vers le compte debian
6. **Mise en prod** : `docker-compose up` pour déployer en production 

## Caractères ASCII utiles

```
←
→
├
┤
┼
┴
║
╬ (croix double barre)
```

