# Module 2 — Installation et configuration de GitHub Copilot

## Objectifs du module

- Activer GitHub Copilot sur un compte GitHub
- Installer l'extension dans Visual Studio Code
- Configurer Copilot pour un usage optimal

---

## 2.1 Prérequis

Avant de commencer, assurez-vous de disposer de :

- Un **compte GitHub** (gratuit ou payant) — [créer un compte](https://github.com/join)
- **Visual Studio Code** installé — [télécharger VS Code](https://code.visualstudio.com/)
- Une connexion Internet active

---

## 2.2 Activer GitHub Copilot

### Abonnements disponibles

| Plan | Public cible | Prix indicatif |
|------|-------------|---------------|
| Copilot Free | Tout utilisateur GitHub | Gratuit (limité) |
| Copilot Pro | Développeurs individuels | ~10 $/mois |
| Copilot Business | Équipes et entreprises | ~19 $/utilisateur/mois |
| Copilot Enterprise | Grandes organisations | ~39 $/utilisateur/mois |

> 💡 **Étudiants et enseignants :** GitHub Education offre Copilot Pro gratuitement via le [GitHub Student Developer Pack](https://education.github.com/pack).

### Activation

1. Connectez-vous à [github.com](https://github.com)
2. Allez dans **Settings** → **Copilot**
3. Cliquez sur **Start free trial** ou activez votre plan
4. Acceptez les conditions d'utilisation

---

## 2.3 Installer l'extension VS Code

1. Ouvrez Visual Studio Code
2. Cliquez sur l'icône **Extensions** dans la barre latérale (ou `Ctrl+Shift+X`)
3. Recherchez **"GitHub Copilot"**
4. Cliquez sur **Install** sur l'extension officielle de GitHub

> L'extension **GitHub Copilot Chat** est automatiquement installée en complément.

### Authentification

Après l'installation :

1. VS Code vous invite à vous connecter à GitHub
2. Cliquez sur **Sign in to GitHub**
3. Un navigateur s'ouvre — autorisez l'accès
4. Revenez dans VS Code : l'icône Copilot apparaît dans la barre d'état

---

## 2.4 Vérifier l'installation

Pour vérifier que tout fonctionne :

1. Créez un nouveau fichier `test.py`
2. Tapez le commentaire suivant :
   ```python
   # fonction qui calcule la somme des éléments d'une liste
   ```
3. Appuyez sur `Entrée` — Copilot devrait proposer une suggestion en gris

Si la suggestion apparaît, l'installation est réussie ! ✅

---

## 2.5 Raccourcis clavier essentiels

| Action | Raccourci (Windows/Linux) | Raccourci (macOS) |
|--------|--------------------------|-------------------|
| Accepter une suggestion | `Tab` | `Tab` |
| Rejeter une suggestion | `Échap` | `Échap` |
| Suggestion suivante | `Alt + ]` | `Option + ]` |
| Suggestion précédente | `Alt + [` | `Option + [` |
| Ouvrir Copilot Chat | `Ctrl + Alt + I` | `Ctrl + Cmd + I` |
| Inline chat | `Ctrl + I` | `Ctrl + I` |

---

## 2.6 Paramètres recommandés

### Activer / désactiver par langage

Dans VS Code, ouvrez les paramètres (`Ctrl+,`) et recherchez `copilot.enable`. Vous pouvez désactiver Copilot pour certains types de fichiers (ex : fichiers `.env` contenant des secrets) :

```json
{
  "github.copilot.enable": {
    "*": true,
    "plaintext": false,
    "markdown": true,
    "scminput": false,
    "dotenv": false
  }
}
```

### Activer les suggestions dans les commentaires

```json
{
  "editor.inlineSuggest.enabled": true
}
```

---

## 2.7 Instructions personnalisées (optionnel)

Vous pouvez guider Copilot avec des instructions spécifiques à votre projet en créant le fichier `.github/copilot-instructions.md` à la racine de votre dépôt :

```markdown
# Instructions Copilot pour ce projet

- Utiliser Python 3.11+
- Suivre PEP 8 pour le style de code
- Toujours ajouter des docstrings aux fonctions publiques
- Utiliser pytest pour les tests
- Commenter le code en français
```

Ces instructions sont transmises automatiquement à Copilot à chaque requête dans ce dépôt.

---

## 2.8 Points clés à retenir

- Copilot Free est disponible gratuitement ; les étudiants bénéficient de Copilot Pro gratuit
- L'installation dans VS Code se fait via le marketplace d'extensions
- Pensez à désactiver Copilot pour les fichiers sensibles (`.env`, secrets)
- Les instructions personnalisées permettent d'adapter Copilot à votre projet

---

[← Module 1](module-01-introduction.md) | [Retour au plan de cours](../PLAN_DE_COURS.md) | [Module 3 →](module-03-utilisation-de-base.md)
