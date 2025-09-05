# Patron state

Ce dépôt met en pratique le patron state dans le cadre du cours 420-930-MA au
Collège de Maisonneuve (Hiver 2025).


**Modalité :** Individuel

**Durée :** 2 heures

## Consignes

Le code actuel implémente un système de feu de circulation avec plusieurs états
: Rouge, Jaune, Vert, et Maintenance. Cependant, il utilise de nombreuses
instructions conditionnelles (if-elif-else) pour gérer les transitions et le
comportement des états. Cela rend le code difficile à maintenir et à étendre et engendre
des problèmes tels que :

1. Beaucoup d'instructions if-elif-else répétitives
2. L'ajout de nouveaux états nécessite de modifier plusieurs méthodes
3. Le comportement spécifique aux états est dispersé dans la classe
4. Difficile de tester les comportements individuels des états
5. Viole le principe Ouvert/Fermé - pas ouvert pour l'extension

Les étudiants devraient refactoriser ceci pour utiliser le patron State où:

- Chaque état est sa propre classe
- Le comportement spécifique aux états est encapsulé dans les classes d'état
- Facile d'ajouter de nouveaux états sans modifier le code existant
- Meilleure séparation des responsabilités

Votre tâche consiste donc à :

1. Faire une duplication (Fork) du dépôt dans votre compte GitHub.
2. Corriger le code pour qu'il respecte le patron state. Vous pouvez
   ajouter des classes ou modifier les classes existantes.
3. À la fin des deux heures, faire une pull request vers le dépôt original. Ce
   code ne sera pas évalué, mais il permettra au professeur de fournir une
   rétroaction.

## Comment exécuter le code fourni

Vous pouvez exécuter le code fourni en utilisant uv avec la commande suivante :

```bash
uv run main
```