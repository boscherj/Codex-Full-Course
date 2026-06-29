# Plan de cours — GitHub Copilot Codex

## Informations générales

| | |
|---|---|
| **Titre** | Cours complet sur GitHub Copilot Codex |
| **Durée totale** | 7 heures (format journée complète ou 2 demi-journées) |
| **Niveau** | Débutant à intermédiaire |
| **Prérequis** | Notions de base en programmation |

---

## Objectifs globaux

À l'issue de ce cours, les participants seront capables de :

- Comprendre ce qu'est GitHub Copilot Codex et comment il fonctionne
- Installer, configurer et activer Copilot dans Visual Studio Code
- Utiliser les suggestions de code, le chat et l'agent de codage
- Adopter de bonnes pratiques pour maximiser la productivité tout en restant responsable

---

## Déroulé du cours

### Module 1 — Introduction à Codex *(1 heure)*

**Objectifs :**
- Situer Codex dans l'écosystème GitHub / OpenAI
- Comprendre les grands principes de l'IA générative pour le code
- Identifier les cas d'usage principaux

**Contenu :**
1. Historique : d'OpenAI Codex à GitHub Copilot
2. Fonctionnement d'un LLM orienté code
3. Panorama des outils IA pour développeurs (Copilot, ChatGPT, etc.)
4. Démonstration : première génération de code

**Activité :** Discussion sur les attentes et les craintes vis-à-vis de l'IA dans le développement

---

### Module 2 — Installation et configuration *(1 heure)*

**Objectifs :**
- Activer GitHub Copilot sur un compte GitHub
- Installer l'extension dans VS Code
- Personnaliser les paramètres de base

**Contenu :**
1. Création / activation d'un abonnement Copilot
2. Installation de l'extension VS Code
3. Authentification GitHub dans VS Code
4. Tour d'horizon de l'interface et des raccourcis
5. Paramètres recommandés

**Activité :** Chaque participant installe et configure Copilot sur sa machine

---

### Module 3 — Utilisation de base *(2 heures)*

**Objectifs :**
- Exploiter les suggestions automatiques en ligne
- Utiliser Copilot Chat pour poser des questions et générer du code
- Générer des tests unitaires et de la documentation

**Contenu :**
1. Complétion de code en ligne (*inline suggestions*)
2. Accepter, refuser et naviguer dans les suggestions
3. Rédiger des commentaires pour guider les suggestions
4. Copilot Chat : questions, explications, refactorisation
5. Génération de tests unitaires
6. Génération de documentation (docstrings, JSDoc…)

**Activités pratiques :**
- Écrire une fonction en Python/JavaScript guidée uniquement par des commentaires
- Demander à Copilot Chat d'expliquer un extrait de code complexe
- Générer des tests pour une fonction existante

---

### Module 4 — Fonctionnalités avancées *(2 heures)*

**Objectifs :**
- Utiliser l'agent de codage (Copilot Coding Agent) pour des tâches autonomes
- Exploiter Copilot dans le terminal et l'éditeur de code
- Intégrer Copilot dans un flux CI/CD

**Contenu :**
1. Introduction à l'agent de codage Copilot
2. Créer et suivre des issues confiées à Copilot
3. Copilot dans le terminal (`gh copilot suggest`, `gh copilot explain`)
4. Copilot pour la revue de code (pull request summaries)
5. Copilot et les pipelines GitHub Actions
6. Personnalisation avec les instructions personnalisées (`.github/copilot-instructions.md`)

**Activités pratiques :**
- Confier une issue simple à l'agent de codage et examiner la PR générée
- Utiliser `gh copilot suggest` dans le terminal
- Créer un fichier d'instructions personnalisées

---

### Module 5 — Bonnes pratiques et éthique *(1 heure)*

**Objectifs :**
- Appliquer les bonnes pratiques pour une utilisation efficace
- Comprendre les enjeux de propriété intellectuelle et de sécurité
- Savoir quand faire confiance à Copilot (et quand ne pas le faire)

**Contenu :**
1. Vérification et validation systématiques du code généré
2. Sécurité : ne jamais partager de secrets, valider les dépendances
3. Propriété intellectuelle et licences
4. Quand Copilot peut se tromper : hallucinations et dépendances fantômes
5. Intégration dans une équipe et dans un processus de revue de code
6. Ressources pour continuer à apprendre

**Activité :** Atelier d'audit : détecter les problèmes dans un code généré par IA

---

## Évaluation

| Critère | Pondération |
|---------|-------------|
| Participation aux activités pratiques | 40 % |
| Exercice final (voir `exercices/exercices.md`) | 60 % |

---

## Ressources complémentaires

- [Documentation GitHub Copilot](https://docs.github.com/fr/copilot)
- [GitHub Copilot Trust Center](https://resources.github.com/copilot-trust-center/)
- [GitHub Skills — Copilot](https://skills.github.com/)
- [OpenAI Codex (modèle de base)](https://openai.com/blog/openai-codex)
