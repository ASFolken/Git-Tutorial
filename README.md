# Git-Tutorial

### Les personnalisations à la première installation

    git config --global core.editor "editeur"
    git config --global user.name "asfolken"
    git config --global user.email "email"

### Les logicieles interessant, SmartGit

    sudo add-apt-repository ppa:eugenesan/ppa
    sudo apt-get update
    sudo apt-get install smartgit

### Utiliser les Alias dans GIT créer ses propres raccourcis
`git config --global alias.<name> '<command>'`      
`git log --oneline --graph --decorate --all` commande utile à créer en Alias par exemple     
        

![File Statut](https://i.stack.imgur.com/ppgRW.png)
   

## Les 3 piliers de GIT
    
  1. Gérer le projet et l'historique      
  
    git init                    # créer un dossier géré par git
    git add <fichier>           # ajouter un ou plusieurs fichier dans le comit
    git reset HEAD~1            # enlever un ou plusieurs fichier dans le comit ou revenir en arriere en local
    git rm                      # supprimer les fichiers et enlevé du staged 
    git mv <from> <to>          # deplacer les fichiers
    git status                  # etat du commit et file status lifecycle
    git commit -a -m "message"  # comité avec un message (-a ajoute tous les fichiers modifiés)
    git commit --amend          # modifier le dernier comit,
    git log                     # afficher les logs des différents commits
    
  2.  Gérer les système envoi/reception de fichiers      
     
    git remote                          # Liste les dépôts distants
    git remote -v                       # Liste les dépôts distants et les chemins associés
    git remote add <alias> <chemin/url> # Ajoute un nouveau dépôt distant
    git remote rm <alias>               # Supprimé un dépôt distant
    git remote rename <old> <new>       # renomer le remote
    git fetch <remote>                  # telecharger le remote
    git push -u <remote> <branche>      # uploader les fichiers dans le repository dans la branche master
    git pull <remote> branche           # télécharger les fichiers depuis le repository dans la branche master
    git diff HEAD                       # voir la différences des header entre ma version et le repo
    git diff --staged                   # voir la différences au niveau des fichiers entre ma version et le repo
    git config --global branch.autosetuprebase always # pull avec rebase automatique
     
  3. Gérer le système de branche     
  
    git branch                  # Permet de lister les branches
    git branch <branche>        # Permet de créer une nouvelle branche <branche>
    git branch -m <branche>     # Renomme la branche courante en <branche>
    git branch -d <branche>     # Permet de supprimer une branche
    git branch -D <branche>     # Supprime la branche même si elle n'a pas été fusionnée
    git checkout <branche>         # switcher d'une branche a une autre  (avec -b créer la branche et met le head dessus)
    git checkout -b <branche>      # switcher sur une branche et la créer si existe pas
    git merge <branche>            # Merge permet de ramener une branche sur une autre et ainsi de la fusionner, se fait à partir de la branche principale.
    git rebase <branche>           # mélanger la branche avec le principal et retourne sur avancement linéaire, se fait à partir de la branche fille
    git branch -d <branche>        # suprimer une branche
    git revert HEAD^               # revenir en arrière sur le remote
    git cherry-pick HEAD HEAD2     # copier le commit dans la branche actuelle
    git rebase -i HEAD             # rebase interactif


## Le Workflow dans un projet

1. __Créer le projet__         
`git clone <url> <path>` depuis un repot      
`git init` Créer directement le projet en local  puis le connecter au remote        
`git remote add <remote> <url>` puis ajouter le remote après coup      
Créer une clef ssh `ssh-keygen` et l'ajouter sur github
       

2. __Télécharger sur un remote__ 
`git fetch <remote>`     
`git pull <remote> <branch>`        
     __Fetch__ : télécharge les nouveaux fichiers d'un remote mais ne met pas à jour les fichiers actuels        
     __Pull__ : télécharge les nouveaux fichiers et tente de merger avec vos fichiers actuels       
`git pull --rebase <remote>` simplifier l'historique en faisant un rebase      
`git config --global branch.autosetuprebase always`  automatiser le rebase dans la config      
      
          
3. __Utiliser une branche et modifier l'historique__        
`git checkout -b <branche>` créer une branche et switcher dessus     
__Passer sur une branche modifie les fichiers dans le workingDirectory__
`git rebase -i` permet de modifier ou jouer avec l'historique en local avant de commit pour arranger la structure    
    __pick__, permet de d'inclure le commit. On peut en profiter pour changer l'ordre des différents commit      
    __reword__, permet d'inclure le commit tout en ayant la possibiliter de changer le message     
    __edit__, permet d'éditer le commit. En séparant en plusieurs commits par exemple      
    __squash__, combine le commit avec le commit du dessus et permet de changer le message du commit      
    __fixup__, comme squash mais utilisera le message du commit situé au dessus     
    __exec__, permet de lancer des commandes shell sur le commit      
   

4. __Revenir en arrière ou corriger__        
`git checkout -- <file>` revenir en arriere sur un file modifié    
`git checkout <idCommit>` Juste pour voir mais pas de modificaiton           
`git checkout <idCommit> <fichier>` Pour voir un fichier dans sont ancien état        
`git revert <idCommit>` Cette commande va défaire ce qui avait été fait au moment du <commit> en créant un nouveau commit. Cela n'altère pas l'historique mais va ajouter un nouveau commit d'inversion       
`git reset <fichier>` Supprime un fichier de la zone de staging, mais ne supprime pas les modifications qui sont faites       
`git reset` Supprime tous les fichiers de la zone de staging, sans supprimer les modifications.       
`git reset --hard` Cette commande est à utiliser avec extrème précaution, elle renvoit le dossier de travail au niveau du dernier commit. Toutes les modifications non commit seront perdues.       
`git reset <commit>`  Permet de revenir en arrière jusqu'au <commit>, réinitialise la zone de staging tout en laissant votre dossier de travail en l'état. L'historique sera perdu (les commits suivant <commit> seront perdus, mais pas vos modifications). Cette commande vous permet surtout de nettoyer l'historique en resoumettant un commit unique à la place de commit trop éparses.       
`git reset <commit> --hard` Permet de revenir au <commit> et réinitialise la zone de staging et le dossier de travail.     
`git commit --amend` L'argument --amend permet de rajouter les fichier en staging dans le commit précédent. Ceci permet de corriger un oubli et d'éviter de faire 10 commits pour la même chose.     
     

5. __Sauvegarder et Ignorer__ facilement en local pour changer de branche ou répondre a un autre comit rapidement      
`git stash` Cette commande va mettre de côté toutes les modifications qui ont été apportées au projet depuis le dernier commit     
`git stash apply` coller les différentes différences dans le stash     
`git stash pop` colle le premier stash et le supprimer de la pille     
`git stash list` voir l'ensemble des stash sauvegardés avec     
`git stash drop` vider les différentes stash en mémoire     
`git add .` ajouter les fichiers au futur commit       
`git commit -a -m "<message>"` commiter les changement sur la branch      
`echo \*.tmp > .gitignore` les fichiers ajoutés dans .gitignore à la racine sont ignoré par le staging     
        
   
6. __Uploader vos modification__ sur le remote avec `git push <remote> <branche>`     
`git push <remote>`     # pousse tout le remote avec toutes les branches


7. __Appliquer les changements d'une branche a une autre__ avec Merge    
`git merge <branche>` le merge ce fait toujours à partir de la branche principale contrairement au rebase         
      

8. __Vérifier__ ce qui c'est passé sur un fichier `git log -n 2 --oneline -p nomFichier`     
`git status`              # donne l'état des différents fichiers depuis le dernier commit      
`git remote -v`           # permet d'avoir les informations sur les remotes     
`git branch`              # permet de voir les différentes branches et celle active      
`git log --oneline`       # avoir une seule ligne pour les logs pratique pour l'arbo     
`git log -n <X>`          # remonter les log avec une profondeur de X     
`git log -p <fichier>`    # avoir les logs des comits concernant un fichier en particulier     

