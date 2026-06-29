# Module 3 — Utilisation de base de GitHub Copilot

## Objectifs du module

- Utiliser les suggestions de code en ligne (inline suggestions)
- Maîtriser Copilot Chat pour poser des questions et générer du code
- Générer automatiquement des tests et de la documentation

---

## 3.1 Les suggestions en ligne (*inline suggestions*)

### Principe

Copilot analyse en permanence le code et les commentaires présents dans votre fichier pour proposer des complétions. Les suggestions apparaissent en **gris** dans l'éditeur.

### Déclencher une suggestion

Copilot se déclenche automatiquement lorsque vous :
- Tapez du code ou des commentaires
- Appuyez sur `Entrée` après une ligne
- Placez le curseur après une déclaration de fonction

### Exemple — Python

```python
# Calcule la factorielle d'un nombre entier positif
def factorielle(n):
    # Copilot va proposer le corps de la fonction ici
```

Copilot proposera typiquement :

```python
def factorielle(n):
    if n == 0:
        return 1
    return n * factorielle(n - 1)
```

### Exemple — JavaScript

```javascript
// Fonction qui inverse une chaîne de caractères
function inverserChaine(str) {
    // suggestion ici
}
```

---

## 3.2 Naviguer dans les suggestions

Lorsque Copilot propose plusieurs suggestions :

| Action | Raccourci |
|--------|-----------|
| Voir toutes les suggestions | `Ctrl+Entrée` (ouvre un panneau dédié) |
| Suggestion suivante | `Alt + ]` / `Option + ]` |
| Suggestion précédente | `Alt + [` / `Option + [` |
| Accepter | `Tab` |
| Rejeter | `Échap` |
| Accepter mot par mot | `Ctrl + →` / `Cmd + →` |

---

## 3.3 Guider Copilot avec les commentaires

La qualité des suggestions dépend directement de la précision de vos commentaires. Plus le contexte est détaillé, meilleures sont les suggestions.

### ❌ Commentaire vague

```python
# faire quelque chose avec la liste
def traiter(liste):
```

### ✅ Commentaire précis

```python
# Filtre une liste de dictionnaires pour ne garder que les éléments
# dont la clé 'actif' est True, puis trie par ordre alphabétique du 'nom'
def filtrer_et_trier(utilisateurs):
```

### Bonnes pratiques pour les commentaires

- Décrire **ce que fait** la fonction, pas comment elle le fait
- Préciser les **types d'entrée/sortie** si possible
- Mentionner les **cas particuliers** (liste vide, valeurs nulles, etc.)
- Utiliser la langue de votre équipe (FR ou EN)

---

## 3.4 Copilot Chat

Copilot Chat est une interface conversationnelle intégrée à VS Code qui permet d'interagir avec Copilot en langage naturel.

### Ouvrir Copilot Chat

- Icône de bulle dans la barre latérale
- Raccourci : `Ctrl+Alt+I` / `Ctrl+Cmd+I`
- Ou via le menu **View → Copilot Chat**

### Usages principaux

#### Générer du code

```
@workspace Crée une API REST avec FastAPI qui gère des utilisateurs (CRUD)
```

#### Expliquer du code

Sélectionnez du code → clic droit → **Copilot → Explain This**

Ou dans le chat :
```
/explain
```

#### Corriger un bug

Sélectionnez le code problématique, puis :
```
/fix
```

#### Refactoriser

```
/refactor Améliore la lisibilité de cette fonction sans changer son comportement
```

### Variables de contexte dans le chat

| Variable | Description |
|----------|-------------|
| `@workspace` | Contexte du projet entier |
| `@vscode` | Questions sur VS Code |
| `#file` | Référencer un fichier spécifique |
| `#selection` | Le code actuellement sélectionné |
| `#terminalLastCommand` | Dernière commande exécutée dans le terminal |

---

## 3.5 Génération de tests unitaires

Copilot excelle dans la génération de tests. Sélectionnez une fonction et utilisez :

```
/tests
```

### Exemple

Fonction à tester :

```python
def diviser(a, b):
    if b == 0:
        raise ValueError("Division par zéro impossible")
    return a / b
```

Copilot génère :

```python
import pytest
from mon_module import diviser

def test_diviser_normal():
    assert diviser(10, 2) == 5.0

def test_diviser_nombres_negatifs():
    assert diviser(-6, 3) == -2.0

def test_diviser_par_zero():
    with pytest.raises(ValueError, match="Division par zéro impossible"):
        diviser(5, 0)

def test_diviser_resultat_decimal():
    assert diviser(1, 3) == pytest.approx(0.333, rel=1e-3)
```

---

## 3.6 Génération de documentation

### Docstrings Python

Sélectionnez une fonction sans docstring et tapez `"""` — Copilot complétera :

```python
def calculer_imc(poids_kg, taille_m):
    """
    Calcule l'Indice de Masse Corporelle (IMC).

    Args:
        poids_kg (float): Poids en kilogrammes.
        taille_m (float): Taille en mètres.

    Returns:
        float: L'IMC calculé (poids / taille²).

    Raises:
        ValueError: Si la taille est nulle ou négative.
    """
    if taille_m <= 0:
        raise ValueError("La taille doit être positive.")
    return poids_kg / (taille_m ** 2)
```

### JSDoc (JavaScript / TypeScript)

Tapez `/**` au-dessus d'une fonction pour déclencher la génération de JSDoc.

### Générer un README

Dans le chat :
```
@workspace Génère un README.md pour ce projet avec les sections : Description, Installation, Usage, Contribution
```

---

## 3.7 L'Inline Chat

L'**Inline Chat** permet d'interagir avec Copilot directement dans l'éditeur, sans quitter le fichier.

1. Placez le curseur là où vous souhaitez intervenir (ou sélectionnez du code)
2. Appuyez sur `Ctrl+I` / `Cmd+I`
3. Tapez votre instruction, ex : `"Ajoute la gestion des erreurs"`
4. Copilot modifie le code directement, avec un diff pour accepter/rejeter

---

## 3.8 Points clés à retenir

- Les suggestions s'améliorent avec des commentaires précis et détaillés
- Copilot Chat permet de générer, expliquer, corriger et refactoriser du code
- `/tests` et `/docs` sont des commandes rapides très utiles
- L'Inline Chat (`Ctrl+I`) permet d'éditer sans sortir du fichier
- **Vérifiez toujours** les suggestions avant de les accepter

---

[← Module 2](module-02-configuration.md) | [Retour au plan de cours](../PLAN_DE_COURS.md) | [Module 4 →](module-04-fonctionnalites-avancees.md)
