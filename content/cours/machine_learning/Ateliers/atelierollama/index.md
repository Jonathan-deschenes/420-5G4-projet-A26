---
title: 3 - Llm agentique
weight: 30
---


## TP / Atelier Pratique : Développement d'une Interface GUI Python et Coding Assisté par IA

**Environnement :** VS Codium + Extension Continue + Ollama (Gemma 4)

**Langages :** C++, Python (Tkinter)


## Évaluation

> [!warning] **Remise**
> Le dernier commit pour la remise doit être fais avant :
> - **Groupe 1** : Remise le 30/11 23h59
> - **Groupe 2** : Remise le ~~17/11 23h59~~ 30/11 23h59
> - **Groupe 3** : Remise le 19/11 23h59
>
> message de commit :  `[REMISE] Partie 3`
> Faites la Pull Request une fois que vous avez terminer cette partie

### Encadrement de l'IA générative

## Contexte & Objectif

Dans cet atelier, vous allez concevoir une **interface graphique (GUI) en Python avec customTkinter** permettant de remplacer l'interface en ligne de commande du programme du TP **C++**.

L'objectif second de cet atelier est d'apprendre à **collaborer efficacement avec un assistant de code IA** (LLM local/cloud via opencode) tout en conservant la maîtrise de votre projet, en gérant le contexte/tokens de manière responsable, et en appliquant de rigoureuses méthodologies de planification.


## Environnement de Travail & Configuration

### Outils requis

* **Éditeur :** VScode, avec un devcontainer exécutant opencode. La configuration du devcontainer vous sera fourni.
* **Moteur LLM (Ollama) :**
    * Modèle recommandé : **`deepseek v4.1-flash`** (très performant et équilibré, disponible sur le cloud seulement).
    * *Alternatives :* `gemma4 36B` (puissant, plus gourmand) ou `gemma4 26B` (rapide et léger).


## Travail à Réaliser

### Phase 1 : Planification et Conception

Avant de générer la moindre ligne de code, il faut planifier le travail (mode `plan` de opencode). Commencez par faire `/init` dans opencode pour créer un fichier agents.md qui résume l'état du projet. Ajoutez ce fichier à git, et n'oubliez pas de le mettre à chaque commit, il peut évoluer.



### Phase 2 : Développement de l'Interface GUI

* Interface python avec le code C++ avec `pybind11`
* Coder l'interface customTkinter en Python en vous appuyant sur vos maquettes.
* Avancer par **petites étapes testables** (découper le problème en sous-composants).
* Valider le fonctionnement de l'interfaçage entre Python et la logique C++.


## Consignes & Bonnes Pratiques d'Utilisation de l'IA

> **Règle d'or :** L'IA est votre assitant, pas le developpeur principal. Ne déléguez pas 100 % du travail au LLM. Vous devez comprendre et être capable d'expliquer chaque ligne de code produite.

* **Traçabilité des échanges :**
* Exportez régulièrement vos sessions de chat au format Markdown (`/export`) et **commitez-les dans Git**.

* **Gestion optimale des tokens & du contexte :** Pensez à utiliser la commande **/compact** ou à ouvrir une **nouvelle session** dès que vous changez de sujet ou de composant pour éviter de saturer la mémoire contextuelle, le fichiers agents.md vous permet de garder une trace de vos avancements.

* **Maintenir une continuité entre les session :**
* Utiliser des fichiers `.md` pour suivre vos avancements, vous pouvez les faires générez et les réutiliser pour ne pas perdre de vue les taches les plus complexes. Ca aide aussi à réduire la taille du contexte.

* **Stratégie multi-modèles :** N'hésitez pas à alterner entre différents niveaux de LLM (SOTA, Open Weight, modèles plus légers) selon la complexité de la tâche (refactoring, génération de fonctions simple, documentation).

* **Versioning Git :** Effectuez des commits réguliers avec des messages clairs retraçant l'évolution du projet.


## Livrables Attendus

Un dépôt Git contenant :

* [ ] Le code source C++ original et le nouveau code Python (customtkinter), et fichier d'interface C++.
* [ ] Le fichier agents.md versionné dans git.
* [ ] L'historique des échanges avec opencode (fichiers `.md` des chats). Dans un répertoire `chatsLogs`.
* [ ] Un historique de commits Git propre et régulier. 
