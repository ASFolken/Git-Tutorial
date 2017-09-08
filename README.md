# Git-Tutorial

## Créer un projet avec GIT

  1. Créer un projet, faire un commit, ajouter des fichiers dans le commit, voir les logs et les status
  
__git init__ -> créer un dossier géré par git     
__git add__ -> ajouter un ou plusieurs fichier dans le comit   
__git reset HEAD~1__ -> enlever un ou plusieurs fichier dans le comit ou revenir en arriere en local   
__git rm__ -> supprimer les fichiers et enlevé du staged 
__git status__ -> etat du commit       
__git commit -m "message"__ -> comité avec un message       
__git log__ -> afficher les logs des différents commits     

    git init
    git add README.md
    git commit -m "first commit"
    git status
    git log
    
  2.  Envoyer, Télécharger les fichiers et vérifier les différences avec le repo   
        
__git remote add origin__ -> lier notre projet git a un repository        
__git push -u origin master__ -> uploader les fichiers dans le repository dans la branche master         
__git pull origin master__ -> télécharger les fichiers depuis le repository dans la branche master         
__git diff HEAD__ -> voir la différences des header entre ma version et le repo      
__git diff --staged__ ->  voir la différences au niveau des fichiers entre ma version et le repo       
    
    git remote add origin https://github.com/ASFolken/Git-Tutorial.git
    git push -u origin master
    git diff HEAD
    
  3. Gérer le système de branche  
  
__git branch branche_name__ -> créer une branche       
__git checkout branche_name__ ->  switcher d'une branche a une autre  
__git merge branche_name__ -> mélanger la branche avec le principal                      
__git rebase branche_name__ -> mélanger la branche avec le principal et retourne sur avancement linéaire    
__git branch -d branch name__ -> suprimer une branche
__git revert HEAD^__ -> revenir en arrière sur le remote
__git cherry-pick HEAD HEAD2__ -> copier le commit dans la branche actuelle
__git rebase -i HEAD__ -> rebase interactif
