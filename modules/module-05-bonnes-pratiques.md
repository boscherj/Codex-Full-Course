# Module 5 — Bonnes pratiques et éthique

## Objectifs du module

- Adopter les bonnes pratiques pour une utilisation efficace et sécurisée de Copilot
- Comprendre les enjeux de sécurité, de propriété intellectuelle et d'éthique
- Savoir identifier et corriger les erreurs du code généré

---

## 5.1 Toujours vérifier le code généré

GitHub Copilot génère du code par prédiction statistique. Il peut produire du code :
- **Fonctionnellement incorrect** (logique erronée, cas limites non gérés)
- **Non sécurisé** (vulnérabilités connues, mauvaises pratiques)
- **Obsolète** (utilisation d'API dépréciées)
- **Non conforme** aux conventions de votre projet

### Règle d'or

> **Ne jamais accepter une suggestion sans l'avoir lue et comprise.**

### Checklist de validation

Avant d'accepter une suggestion, vérifiez :

- [ ] La logique est-elle correcte pour tous les cas (y compris les cas limites) ?
- [ ] Les entrées sont-elles validées/sanitisées ?
- [ ] Les erreurs sont-elles gérées correctement ?
- [ ] Le code suit-il les conventions du projet ?
- [ ] Y a-t-il des dépendances inconnues ou suspectes ?
- [ ] Les tests couvrent-ils les cas générés ?

---

## 5.2 Sécurité

### Ne jamais exposer de secrets

Copilot peut proposer d'inclure des clés API ou mots de passe en dur dans le code. **Ne jamais accepter ces suggestions.**

❌ À éviter :
```python
# Connexion à la base de données
conn = psycopg2.connect(
    host="db.monserveur.com",
    ******  # ← DANGER
)
```

✅ À faire :
```python
import os

conn = psycopg2.connect(
    host=os.getenv("DB_HOST"),
    ******"DB_PASSWORD")
)
```

**Bonne pratique :** Désactivez Copilot pour les fichiers `.env` dans les paramètres VS Code.

### Vulnérabilités communes générées par IA

Les LLMs peuvent reproduire des vulnérabilités connues présentes dans leurs données d'entraînement :

| Vulnérabilité | Exemple |
|---------------|---------|
| Injection SQL | Concaténation de chaînes dans une requête SQL |
| XSS | Insertion de données non sanitisées dans le HTML |
| Path traversal | Utilisation non validée de chemins de fichiers |
| Désérialisation non sécurisée | `pickle.loads()` sur des données non fiables |
| Dépendances fantômes | Import d'un package inexistant (*hallucination*) |

### Valider les dépendances

Copilot peut suggérer des packages qui n'existent pas ("hallucinations"). Vérifiez toujours sur [PyPI](https://pypi.org), [npm](https://npmjs.com), etc. avant d'installer.

---

## 5.3 Propriété intellectuelle et licences

### Contexte

Copilot est entraîné sur du code source public de GitHub. Il peut parfois générer des extraits qui ressemblent ou correspondent à du code existant.

### Fonctionnalité "Duplication detection"

GitHub Copilot intègre un filtre de détection de duplication qui peut bloquer les suggestions ressemblant trop à du code public existant. Cette fonctionnalité est activable dans les paramètres.

### Recommandations

- Dans les contextes professionnels, **vérifiez la politique de votre organisation** concernant l'utilisation de code généré par IA
- Pour les projets open source, renseignez-vous sur les implications de licence
- Ne présentez jamais du code généré par Copilot comme entièrement de votre propre création sans l'avoir significativement revu et modifié

---

## 5.4 Quand faire confiance à Copilot ?

### Copilot est très fiable pour…

- ✅ Les patterns très courants (boucles, conditions, CRUD basique)
- ✅ La génération de code boilerplate
- ✅ Les transformations syntaxiques simples (ex : convertir une liste en dict)
- ✅ La génération de tests pour des fonctions simples et pures
- ✅ Les commandes shell courantes

### Copilot nécessite plus de supervision pour…

- ⚠️ La logique métier complexe et spécifique à votre domaine
- ⚠️ Les algorithmes de performance critique
- ⚠️ Le code impliquant la sécurité (authentification, chiffrement)
- ⚠️ Les requêtes de base de données complexes
- ⚠️ Le code concurrent ou asynchrone avancé

### Copilot peut se tromper fréquemment sur…

- ❌ Les APIs récentes (publiées après la date d'entraînement du modèle)
- ❌ Les bibliothèques peu populaires ou très spécialisées
- ❌ Les comportements subtils de votre environnement spécifique
- ❌ Les règles métier non documentées dans le code

---

## 5.5 Utilisation en équipe

### Communiquer les règles d'utilisation

Définissez en équipe une politique d'utilisation de Copilot :
- Revue systématique du code généré avant merge
- Documentation des parties importantes générées par IA (optionnel, selon la politique)
- Validation des dépendances introduites par Copilot

### Copilot et la revue de code

Le code généré par Copilot doit passer **exactement les mêmes critères de revue** que tout autre code :
- Lisibilité et maintenabilité
- Tests adéquats
- Conformité aux conventions du projet
- Absence de vulnérabilités

### Intégration dans le processus CI/CD

Utilisez des outils automatisés en complément :

| Outil | Usage |
|-------|-------|
| [GitHub Advanced Security](https://github.com/features/security) | Détection de vulnérabilités et secrets |
| [Dependabot](https://github.com/dependabot) | Mise à jour des dépendances |
| Linters (flake8, ESLint, etc.) | Style et qualité du code |
| SonarQube / SonarCloud | Analyse statique approfondie |

---

## 5.6 Développer de bonnes habitudes

### La règle du pilote

Pensez à Copilot comme un **co-pilote**, pas un pilote automatique. Vous restez toujours aux commandes.

### L'apprentissage avec Copilot

Copilot peut être un excellent outil d'apprentissage :
- Demandez-lui d'**expliquer** le code qu'il génère
- Utilisez `/explain` pour comprendre un concept
- Ne vous contentez pas d'accepter — **comprenez**

### Éviter la dépendance

- Essayez d'abord d'écrire le code vous-même avant de demander à Copilot
- Utilisez Copilot pour accélérer, pas pour remplacer votre réflexion
- Maintenez vos compétences en code en pratiquant sans IA régulièrement

---

## 5.7 Ressources pour aller plus loin

| Ressource | Lien |
|-----------|------|
| Documentation officielle Copilot | [docs.github.com/copilot](https://docs.github.com/fr/copilot) |
| GitHub Copilot Trust Center | [resources.github.com/copilot-trust-center](https://resources.github.com/copilot-trust-center/) |
| GitHub Skills | [skills.github.com](https://skills.github.com/) |
| OWASP Top 10 (sécurité) | [owasp.org/Top10](https://owasp.org/Top10/) |
| GitHub Blog — Copilot | [github.blog/tag/github-copilot](https://github.blog/tag/github-copilot/) |

---

## 5.8 Points clés à retenir

- Vérifiez **toujours** le code généré avant de l'accepter
- Ne jamais laisser Copilot introduire des secrets dans le code
- Validez les packages suggérés avant de les installer
- Le code généré par IA doit passer les mêmes standards de revue que tout autre code
- Restez le pilote : Copilot accélère, il ne remplace pas votre jugement

---

[← Module 4](module-04-fonctionnalites-avancees.md) | [Retour au plan de cours](../PLAN_DE_COURS.md) | [Exercices →](../exercices/exercices.md)
