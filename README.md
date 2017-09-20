# Git-Tutorial

## Créer un projet avec GIT

Les personnalisations à la première installation

    git config --global core.editor "editeur"
    git config --global user.name "asfolken"
    git config --global user.email "email"
    
![File Statut](https://i.stack.imgur.com/ppgRW.png)

  1. Créer un projet, faire un commit, ajouter des fichiers dans le commit, voir les logs et les status
  
    git init            // créer un dossier géré par git     
    git add README.md   // ajouter un ou plusieurs fichier dans le comit   
    git reset HEAD~1    // enlever un ou plusieurs fichier dans le comit ou revenir en arriere en local   
    git rm              // supprimer les fichiers et enlevé du staged 
    git mv from to      // deplacer les fichiers
    git status          // etat du commit et file status lifecycle
    git commit -a -m "message" // comité avec un message (-a ajoute tous les fichiers modifiés)
    git commit --amend  // modifier le dernier comi
    git log_            // afficher les logs des différents commits     
    
  2.  Envoyer, Télécharger les fichiers et vérifier les différences avec le repo   
  
 
    
    git remote add origin https://github.com/ASFolken/Git-Tutorial.git
    git remote -v               // voir les différents remotes du projet    
    git remote add origin       // lier notre projet git a un repository  
    git fetch origin            // telecharger le remote
    git push -u remote branch   // uploader les fichiers dans le repository dans la branche master        
    git pull remote branch      // télécharger les fichiers depuis le repository dans la branche master        
    git diff HEAD               // voir la différences des header entre ma version et le repo      
    git diff --staged           // voir la différences au niveau des fichiers entre ma version et le repo      
    
  3. Gérer le système de branche  
  
    git branch branch           // créer une branche       
    git checkout branch         // switcher d'une branche a une autre  (avec -b créer la branche et met le head dessus)
    git merge branch            // mélanger la branche avec le principal                      
    git rebase branch           // mélanger la branche avec le principal et retourne sur avancement linéaire    
    git branch -d branch        // suprimer une branche
    git revert HEAD^            // revenir en arrière sur le remote
    git cherry-pick HEAD HEAD2  // copier le commit dans la branche actuelle
    git rebase -i HEAD          // rebase interactif
