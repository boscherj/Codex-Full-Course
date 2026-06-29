# Module 1 — Introduction à GitHub Copilot Codex

## Objectifs du module

- Comprendre l'origine et l'évolution de GitHub Copilot / Codex
- Saisir les principes fondamentaux des modèles de langage appliqués au code
- Identifier les principaux cas d'usage de Copilot

---

## 1.1 Qu'est-ce que Codex ?

**OpenAI Codex** est un modèle de langage (LLM – *Large Language Model*) entraîné sur des milliards de lignes de code source public et de texte en langage naturel. Il est capable de :

- Comprendre des descriptions en langage naturel
- Générer du code dans plus de 20 langages de programmation (Python, JavaScript, TypeScript, Go, Ruby, Java, C#, etc.)
- Expliquer, déboguer et refactoriser du code existant

**GitHub Copilot** est le produit commercial développé par GitHub (une filiale de Microsoft) en partenariat avec OpenAI. Il exploite Codex et des modèles successeurs pour proposer une assistance IA directement dans l'éditeur de code.

---

## 1.2 Historique

| Année | Événement |
|-------|-----------|
| 2020 | OpenAI lance GPT-3, modèle de langage généraliste |
| 2021 | OpenAI publie Codex, spécialisé dans le code |
| 2021 | GitHub lance GitHub Copilot en version bêta technique |
| 2022 | Disponibilité générale de GitHub Copilot |
| 2023 | Lancement de Copilot X : Copilot Chat, Copilot for CLI, Copilot for Docs |
| 2024 | Intégration de modèles GPT-4o et Claude dans Copilot |
| 2025 | Lancement de l'agent de codage Copilot (*Copilot Coding Agent*) |

---

## 1.3 Comment fonctionne un LLM orienté code ?

Un LLM (comme Codex) est un réseau de neurones de type *transformer* entraîné sur d'immenses corpus de textes et de code. En résumé :

1. **Entraînement** : le modèle apprend des patterns statistiques à partir de milliards de tokens (morceaux de texte/code)
2. **Inférence** : à partir d'un *contexte* (le code déjà écrit, un commentaire, une question), le modèle prédit les tokens suivants les plus probables
3. **Prompt = contexte** : Copilot utilise le fichier ouvert, les fichiers voisins, et éventuellement une instruction utilisateur comme prompt

> **Important :** Copilot ne "comprend" pas le code au sens humain — il reconnaît des patterns. Il peut donc se tromper. La vérification humaine reste indispensable.

---

## 1.4 Panorama des outils IA pour développeurs

| Outil | Éditeur | Particularité |
|-------|---------|---------------|
| GitHub Copilot | GitHub / Microsoft | Intégration native VS Code, JetBrains, etc. |
| ChatGPT / GPT-4o | OpenAI | Interface chat généraliste |
| Cursor | Cursor AI | Éditeur IA-first basé sur VS Code |
| Tabnine | Tabnine | Focus confidentialité, modèle local possible |
| Amazon CodeWhisperer | AWS | Intégré AWS, gratuit pour usage individuel |
| Codeium | Exafunction | Gratuit, multiéditeur |
| Gemini Code Assist | Google | Intégré Google Cloud |

---

## 1.5 Cas d'usage principaux

### Accélération de l'écriture de code
- Complétion automatique de fonctions
- Génération de boilerplate (CRUD, handlers HTTP, etc.)
- Conversion de pseudocode en code réel

### Apprentissage et exploration
- Comprendre une API inconnue
- Traduire du code d'un langage à un autre
- Obtenir des exemples d'utilisation

### Qualité et maintenance
- Génération de tests unitaires
- Rédaction de documentation et commentaires
- Détection et correction de bugs
- Refactorisation de code legacy

### Automatisation via l'agent
- Résolution autonome d'issues GitHub
- Mise en place de pipelines CI/CD
- Corrections de bugs simples en mode non supervisé

---

## 1.6 Points clés à retenir

- Codex est le moteur IA derrière GitHub Copilot
- Un LLM génère du code par prédiction statistique, pas par compréhension
- Copilot accélère le développement mais **ne remplace pas le jugement du développeur**
- Toujours relire, tester et valider le code généré

---

## 🔗 Ressources

- [GitHub Copilot — Documentation officielle](https://docs.github.com/fr/copilot)
- [OpenAI Codex — Article de blog](https://openai.com/blog/openai-codex)
- [Comprendre les Transformers (vidéo 3Blue1Brown)](https://www.youtube.com/watch?v=wjZofJX0v4M)

---

[← Retour au plan de cours](../PLAN_DE_COURS.md) | [Module 2 →](module-02-configuration.md)
