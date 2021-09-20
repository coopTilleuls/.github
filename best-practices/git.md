# Bonnes pratiques Git

Utiliser les fichiers `.gitconfig` et `.gitignore_global` définis ici

## Conventions de commits

Commit: https://www.conventionalcommits.org/en/v1.0.0/
Branch: feature/issue-#34

## Workflow de base

https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow

## Quelques règles pour le travail en équipe :

Une pull request doit avoir un maximum de 700 modifications, moins c’est mieux

Car il faut au moins 15 à 20 min pour relire / tester une pull request de 700 modifications

Quand on propose une relecture de sa Pull Request, il faut la relire soit même avant. Ça évite de laisser des erreurs bêtes (console.log, des commentaires, du code mort...), de les corriger au plus vite et les relecteurs seront plus concentré sur votre code.

Lors de la relecture des Pull Request il faut être bienveillant dans l’ajout de commentaire. Il vaut mieux donner la réponse et en parler par la suite avec la personne, au lieu de dire “c’est de la merde” ou “tu n’es pas loin, cherche encore”. Il ne faut pas oublier que cette étape prend du temps (donc de l’argent pour le client) et que nous sommes là pour apprendre et améliorer le code pour que le projet soit pérenne. Donc soyez efficace et bienveillant !

Quand vous validez une Pull Request, vous êtes autant responsable de la qualité ou des bugs laissés que la personne qui a fait la tâche. Le développement est un travail d’équipe. Vous ne pouvez pas mettre la faute sur le développeur si vous l’avez aussi validé.

Lors de la relecture on fait :

- on relit le code (au moins la syntaxe et les bonne pratique si vous n’êtes pas familiarisé avec la technologie utilisé)

* on relit les tests (si pas de test on les demande en commentaire)
* on relit la documentation (si pas de documentation et que ça vous semble nécessaire il faut la demander en commentaire et dire ce que vous souhaitez voir dessus)
* on test la feature en local (surtout quand c’est du front)
* si les tests ne sont pas lancé dans la CI, il faut les lancer en local pour être sur du bon fonctionnement
* il ne faut pas faire confiance aveuglément au développeur de la PR même si c’est Kévin Dunglas :D
* VOUS ÊTES GARANT DE LA QUALITÉ ET DU BON FONCTIONNEMENT DU CODE
* 1 feature == 1 branche de travail (qui sera supprimé après le merge de la branche) == 1 commit à la fin (on squash & merge sur Github, ça nous permet de réécrire notre commit correctement et github ajoute automatiquement l’ID de la PR à la fin du titre du commit)
* ON NE TOUCHE PAS AU DÉVELOPPEMENT DES AUTRES SANS LEUR DEMANDER, CHACUN SON PÉRIMÈTRE

## Tutorial pour apprendre git

https://learngitbranching.js.org/
