# Module 4 — Fonctionnalités avancées de GitHub Copilot

## Objectifs du module

- Utiliser l'agent de codage Copilot pour des tâches autonomes
- Exploiter Copilot dans le terminal via la CLI GitHub
- Intégrer Copilot dans les workflows GitHub Actions et la revue de code
- Personnaliser Copilot avec des instructions et des extensions

---

## 4.1 L'agent de codage Copilot (*Copilot Coding Agent*)

### Qu'est-ce que l'agent de codage ?

L'agent de codage Copilot est une fonctionnalité qui permet à Copilot de **travailler de manière autonome** sur une tâche GitHub : résoudre une issue, corriger un bug, ajouter une fonctionnalité. Il crée une Pull Request avec les modifications proposées.

### Comment ça marche ?

1. Vous assignez une issue GitHub à **Copilot** (comme vous le feriez avec un collègue)
2. L'agent analyse l'issue, le dépôt et le code existant
3. Il crée une branche, effectue les modifications nécessaires
4. Il ouvre une Pull Request avec une description détaillée
5. Vous revoyez et mergez (ou refusez)

### Assigner une issue à Copilot

**Via l'interface GitHub :**
1. Ouvrez une issue
2. Dans le panneau "Assignees", sélectionnez **Copilot**
3. L'agent commence à travailler

**Via GitHub CLI :**
```bash
gh issue edit 42 --add-assignee "@copilot"
```

### Suivre la progression

L'agent communique sa progression via des commentaires dans l'issue et la PR. Vous pouvez interagir avec lui en commentant.

### Cas d'usage idéaux pour l'agent

- ✅ Corrections de bugs bien décrits
- ✅ Ajout de tests manquants
- ✅ Refactorisation simple et documentée
- ✅ Mise à jour de dépendances
- ✅ Amélioration de la documentation
- ⚠️ Nouvelles fonctionnalités complexes (superviser de près)
- ❌ Décisions architecturales importantes

---

## 4.2 Copilot dans le terminal (GitHub CLI)

GitHub CLI (`gh`) intègre Copilot directement dans le terminal.

### Installation de GitHub CLI

```bash
# macOS
brew install gh

# Windows (avec winget)
winget install --id GitHub.cli

# Linux (Ubuntu/Debian)
sudo apt install gh
```

Puis authentifiez-vous :
```bash
gh auth login
```

### `gh copilot suggest`

Obtenez une suggestion de commande à partir d'une description en langage naturel :

```bash
gh copilot suggest "Trouver tous les fichiers modifiés dans les 24 dernières heures"
# → find . -mtime -1 -type f

gh copilot suggest "Créer une archive tar.gz du dossier src en excluant les fichiers .log"
# → tar -czf src.tar.gz --exclude="*.log" src/

gh copilot suggest "Afficher les 10 processus qui consomment le plus de mémoire"
# → ps aux --sort=-%mem | head -11
```

### `gh copilot explain`

Obtenez une explication d'une commande complexe :

```bash
gh copilot explain "find . -name '*.py' -exec grep -l 'TODO' {} \;"
# Copilot explique chaque partie de la commande
```

---

## 4.3 Copilot pour la revue de code

### Résumé automatique de Pull Request

Lorsque vous ouvrez une Pull Request sur GitHub, Copilot peut générer automatiquement un **résumé** de vos modifications.

- Dans une PR, cherchez le bouton **Copilot summary** en haut de la description
- Copilot analyse le diff et génère un résumé structuré

### Suggestions de revue

Copilot peut suggérer des améliorations lors de la revue :
- Cliquez sur un fichier dans la PR
- Utilisez le bouton **Copilot review** pour obtenir des suggestions automatiques

---

## 4.4 Copilot et GitHub Actions

### Générer des workflows

Dans le chat Copilot :

```
@workspace Génère un workflow GitHub Actions pour :
- Lancer les tests Python avec pytest
- Vérifier le style de code avec flake8
- Se déclencher sur chaque push et pull request
```

### Déboguer des workflows échoués

Si un workflow échoue, copiez les logs dans Copilot Chat :

```
Ce workflow GitHub Actions échoue avec cette erreur :
[collez les logs ici]
Explique l'erreur et propose une correction.
```

### Exemple de workflow généré par Copilot

```yaml
name: CI

on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

jobs:
  test:
    runs-on: ubuntu-latest
    
    steps:
    - uses: actions/checkout@v4
    
    - name: Set up Python
      uses: actions/setup-python@v5
      with:
        python-version: '3.11'
    
    - name: Install dependencies
      run: |
        pip install -r requirements.txt
        pip install pytest flake8
    
    - name: Lint with flake8
      run: flake8 . --max-line-length=100
    
    - name: Run tests
      run: pytest --verbose
```

---

## 4.5 Instructions personnalisées avancées

Le fichier `.github/copilot-instructions.md` permet de contextualiser Copilot pour votre projet.

### Exemple complet

```markdown
# Instructions Copilot — Projet MonApp

## Stack technique
- Backend : FastAPI (Python 3.11)
- Base de données : PostgreSQL avec SQLAlchemy
- Tests : pytest avec fixtures
- Frontend : React 18 + TypeScript

## Conventions de code
- Suivre PEP 8 et utiliser des type hints Python
- Nommer les variables et fonctions en snake_case (Python) ou camelCase (TypeScript)
- Longueur de ligne maximale : 100 caractères
- Commenter le code complexe en français

## Conventions de tests
- Utiliser des fixtures pytest pour les données de test
- Un fichier de test par module (`test_module.py`)
- Couvrir les cas nominaux ET les cas d'erreur

## Ce qu'il faut éviter
- Ne pas utiliser `print()` dans le code de production (utiliser `logging`)
- Ne pas commiter de clés API ou mots de passe
- Ne pas utiliser `SELECT *` dans les requêtes SQL
```

### Portées des instructions

Il existe plusieurs niveaux d'instructions :

| Niveau | Fichier | Portée |
|--------|---------|--------|
| Dépôt | `.github/copilot-instructions.md` | Tout le dépôt |
| Personnel | Paramètres Copilot sur github.com | Tous vos dépôts |
| Session | Dans le chat, début de conversation | Conversation en cours |

---

## 4.6 Extensions Copilot (*Copilot Extensions*)

Les extensions Copilot permettent d'intégrer des outils tiers directement dans le chat.

Exemples d'extensions disponibles :
- **@docker** — aide pour les Dockerfiles et Docker Compose
- **@sentry** — analyse des erreurs Sentry
- **@datadog** — monitoring et alertes

Pour installer une extension :
1. Allez sur le [GitHub Marketplace](https://github.com/marketplace?type=apps&copilot_app=true)
2. Recherchez des extensions Copilot
3. Installez et autorisez l'extension
4. Utilisez `@nom-extension` dans le chat

---

## 4.7 Points clés à retenir

- L'agent de codage peut résoudre des issues de manière autonome — idéal pour les tâches bien définies
- `gh copilot suggest` et `gh copilot explain` sont très utiles dans le terminal
- Copilot peut générer et déboguer des workflows GitHub Actions
- Les instructions personnalisées permettent d'adapter Copilot à votre stack et vos conventions
- Les extensions Copilot étendent ses capacités à des outils tiers

---

[← Module 3](module-03-utilisation-de-base.md) | [Retour au plan de cours](../PLAN_DE_COURS.md) | [Module 5 →](module-05-bonnes-pratiques.md)
