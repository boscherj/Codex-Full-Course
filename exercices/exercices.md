# Exercices pratiques — Cours GitHub Copilot Codex

Ces exercices accompagnent les 5 modules du cours. Ils sont conçus pour être réalisés avec GitHub Copilot activé dans Visual Studio Code.

---

## Exercice 1 — Première prise en main (Module 1 & 2)

**Objectif :** Vérifier l'installation et découvrir les suggestions de base.

**Durée estimée :** 15 minutes

### Instructions

1. Créez un fichier `exercice1.py`
2. Tapez les commentaires suivants, un par un, et observez les suggestions de Copilot :

```python
# Fonction qui vérifie si un nombre est premier
```

```python
# Fonction qui convertit une température de Celsius en Fahrenheit et en Kelvin
```

```python
# Classe Personne avec les attributs nom, prénom et date de naissance
# et une méthode pour calculer l'âge
```

3. Acceptez les suggestions et **lisez attentivement le code généré**
4. Naviguez entre plusieurs suggestions avec `Alt+]` / `Alt+[`

**Questions de réflexion :**
- La suggestion est-elle correcte ?
- Auriez-vous écrit le code différemment ?
- Y a-t-il des cas limites non gérés ?

---

## Exercice 2 — Guider Copilot avec des commentaires précis (Module 3)

**Objectif :** Apprendre à rédiger des commentaires efficaces pour obtenir de meilleures suggestions.

**Durée estimée :** 20 minutes

### Partie A — Comparez deux approches

Créez un fichier `exercice2.py`. Testez d'abord avec un commentaire vague, puis avec un commentaire précis :

**Commentaire vague :**
```python
# Traiter les données
def traiter(data):
```

**Commentaire précis :**
```python
# Prend une liste de dictionnaires représentant des produits avec les clés
# 'nom' (str), 'prix' (float) et 'stock' (int).
# Retourne une liste filtrée avec uniquement les produits en stock (stock > 0),
# triée par prix croissant, sous forme de liste de tuples (nom, prix).
def filtrer_produits_disponibles(produits):
```

Observez la différence de qualité entre les deux suggestions.

### Partie B — À vous de jouer

Écrivez un commentaire détaillé pour une fonction qui :
- Lit un fichier CSV
- Calcule des statistiques (min, max, moyenne) pour chaque colonne numérique
- Retourne un dictionnaire avec les résultats

---

## Exercice 3 — Copilot Chat (Module 3)

**Objectif :** Explorer Copilot Chat pour expliquer, corriger et refactoriser du code.

**Durée estimée :** 25 minutes

### Partie A — Expliquer du code

Copiez le code suivant dans un fichier `exercice3_a.py` :

```python
def mystery(lst):
    if not lst:
        return []
    pivot = lst[len(lst) // 2]
    left = [x for x in lst if x < pivot]
    middle = [x for x in lst if x == pivot]
    right = [x for x in lst if x > pivot]
    return mystery(left) + middle + mystery(right)
```

1. Sélectionnez tout le code
2. Dans Copilot Chat, tapez `/explain`
3. Posez ensuite : *"Quelle est la complexité temporelle de cet algorithme ?"*

### Partie B — Corriger un bug

Créez un fichier `exercice3_b.py` avec ce code bugué :

```python
def calculer_moyenne(notes):
    total = 0
    for note in notes:
        total += note
    return total / len(notes)

# Test
print(calculer_moyenne([15, 12, 18]))  # OK
print(calculer_moyenne([]))  # BUG : division par zéro !
```

1. Sélectionnez la fonction
2. Dans Copilot Chat, tapez `/fix`
3. Examinez la correction proposée

### Partie C — Refactoriser

Créez un fichier `exercice3_c.py` :

```python
def traiter_commande(commande):
    if commande['statut'] == 'nouvelle':
        if commande['montant'] > 0:
            if commande['client'] != '':
                if commande['produits']:
                    commande['statut'] = 'validée'
                    total = 0
                    for p in commande['produits']:
                        total = total + p['prix'] * p['quantite']
                    commande['total'] = total
                    return True
    return False
```

Demandez à Copilot Chat de refactoriser ce code pour le rendre plus lisible.

---

## Exercice 4 — Génération de tests (Module 3)

**Objectif :** Utiliser Copilot pour générer une suite de tests complète.

**Durée estimée :** 20 minutes

### Instructions

1. Créez un fichier `calculatrice.py` avec ce code :

```python
class Calculatrice:
    """Calculatrice simple supportant les 4 opérations de base."""
    
    def additionner(self, a, b):
        return a + b
    
    def soustraire(self, a, b):
        return a - b
    
    def multiplier(self, a, b):
        return a * b
    
    def diviser(self, a, b):
        if b == 0:
            raise ValueError("Impossible de diviser par zéro")
        return a / b
    
    def puissance(self, base, exposant):
        return base ** exposant
```

2. Sélectionnez toute la classe
3. Dans Copilot Chat, tapez `/tests`
4. Examinez les tests générés :
   - Couvrent-ils tous les cas nominaux ?
   - Les cas d'erreur sont-ils testés ?
   - Les tests sont-ils bien nommés ?
5. Modifiez les tests si nécessaire et exécutez-les avec `pytest`

---

## Exercice 5 — Copilot CLI (Module 4)

**Objectif :** Utiliser `gh copilot suggest` et `gh copilot explain` dans le terminal.

**Durée estimée :** 15 minutes

**Prérequis :** GitHub CLI installé et authentifié

### Partie A — Suggérer des commandes

Utilisez `gh copilot suggest` pour trouver les commandes permettant de :

1. Lister les 5 fichiers les plus volumineux dans le répertoire courant
2. Compter le nombre de lignes de code Python dans un projet (ignorer les fichiers vides)
3. Trouver tous les fichiers contenant "TODO" dans un projet
4. Créer un backup compressé d'un dossier avec la date dans le nom du fichier

### Partie B — Expliquer des commandes

Utilisez `gh copilot explain` pour comprendre ces commandes :

```bash
git log --oneline --graph --all --decorate
```

```bash
awk '{sum += $1} END {print sum}' fichier.txt
```

---

## Exercice 6 — Instructions personnalisées (Module 4)

**Objectif :** Créer un fichier d'instructions personnalisées pour un projet fictif.

**Durée estimée :** 15 minutes

### Instructions

1. Créez un nouveau dépôt (ou dossier de projet) fictif
2. Créez le fichier `.github/copilot-instructions.md`
3. Rédigez des instructions personnalisées pour un projet de votre choix (API web, application mobile, script d'analyse de données, etc.)

Votre fichier d'instructions doit couvrir :
- [ ] La stack technique utilisée
- [ ] Les conventions de nommage
- [ ] Le style de commentaires/documentation
- [ ] Les frameworks de test
- [ ] Au moins 3 règles spécifiques à votre projet

4. Testez en demandant à Copilot de générer une fonction et vérifiez qu'il respecte vos instructions

---

## Exercice Final — Projet intégré

**Objectif :** Réaliser un mini-projet complet en utilisant toutes les fonctionnalités de Copilot.

**Durée estimée :** 45 minutes

### Description du projet

Créez une **API de gestion de bibliothèque** (bibliothèque de livres) avec les fonctionnalités suivantes :

- Ajouter un livre (titre, auteur, année, ISBN)
- Lister tous les livres
- Rechercher un livre par titre ou auteur
- Marquer un livre comme emprunté / disponible
- Supprimer un livre

### Contraintes

Utilisez Copilot pour :
1. **Générer le squelette** de l'API (FastAPI ou Flask)
2. **Compléter** les fonctions une par une avec les suggestions inline
3. **Générer les tests** avec `/tests`
4. **Documenter** le code avec `/doc`
5. **Corriger** les éventuels bugs avec `/fix`

### Livrable

- Le code de l'API fonctionnel
- Les tests unitaires qui passent
- Un README généré par Copilot (que vous aurez relu et complété)

### Critères d'évaluation

| Critère | Points |
|---------|--------|
| Fonctionnalité complète | 4 |
| Tests unitaires couvrant les cas nominaux et d'erreur | 3 |
| Code lisible et bien documenté | 2 |
| Bonnes pratiques (gestion d'erreurs, pas de secrets, etc.) | 1 |
| **Total** | **10** |

---

## 💡 Conseils généraux

- **Relisez toujours** le code avant d'accepter une suggestion
- Si une suggestion ne vous convient pas, tapez `Échap` et **reformulez votre commentaire**
- N'hésitez pas à utiliser Copilot Chat pour **comprendre** le code généré
- Gardez un œil sur la **sécurité** : pas de secrets en dur, validation des entrées

---

[← Module 5](../modules/module-05-bonnes-pratiques.md) | [Retour au plan de cours](../PLAN_DE_COURS.md)
