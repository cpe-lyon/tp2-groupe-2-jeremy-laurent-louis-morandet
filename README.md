# TP 2 : (LAURENT - MORANDET)
## Exercice 1 Variables d’environnement
*1. Dans quels dossiers bash trouve-t-il les commandes tapées par l’utilisateur ?*

En tapant la commande:

    printenv PATH

On trouve les dossiers suivants:

    /usr/local/sbin    
    /usr/local/bin  
    /usr/sbin  
    /usr/bin  
    /sbin  
    /bin  
    /usr/games  
    /usr/local/games  
    /snap/bin

*2. Quelle variable d’environnement permet à la commande cd tapée sans argument de vous ramener dans votre répertoire personnel ?*

la variable HOME

    cd $HOME


*3. Explicitez le rôle des variables LANG, PWD, OLDPWD, SHELL et _.*

En utilisant la commande: "man", on obtient les définitions suivantes:
    
    LANG : : la variable d’environnement LANG détermine la langue que les logiciels utilisent pour communiquer avec l’utilisateur
    PWD : Le répertoire de travail courant de l'interpréteur de commande
    OLDPWD : Le répertoire de travail courant avant la dernière commande CD
    SHELL : Donne le chemin vers l'interpréteur

*4. Créez une variable locale MY_VAR (le contenu n’a pas d’importance). Vérifiez que la variable existe.*

    MY_VAR="hello world"
    echo $VAR
    
La variable est local car en tapant:

    printenv MY_VAR

Rien ne s'affiche.

*5. Tapez ensuite la commande bash. Que fait-elle ? La variable MY_VAR existe-t-elle ? Expliquez. A la fin de cette question, tapez la commande exit pour revenir dans votre session initiale.*

La commande bash ouvre un nouveau process BASH.
Non elle n'existe pas, car ce n'est pas une variable d'environnement.


*6. Transformez MY_VAR en une variable d’environnement et recommencez la question précédente. Expliquez.*

Pour transformer MY_VAR en une variable d'environement:

    export MY_VAR
    printenv MY_VAR

*7. Créer la variable d’environnement NOMS ayant pour contenu vos noms de binômes séparés par un espace. Afficher la valeur de NOMS pour vérifier que l’affectation est correcte.*

    user@ubuntu-serverirc13:~$ export NOMS="JEREMY LOUIS"
    user@ubuntu-serverirc13:~$ printenv NOMS

*8. Ecrivez une commande qui affiche ”Bonjour à vous deux, binôme1 binôme2 !” (où binôme1 et binôme2 sont vos deux noms) en utilisant la variable NOMS.*

    user@ubuntu-serverirc13:~$ vim progm.sh
    
    --> vim progm.sh
        echo 'Bonjour à vous deux, $NOMS"
        :w
        :q 
        
    user@ubuntu-serverirc13:~$ . progm.sh
    Bonjour à vous deux, JEREMY LOUIS
    user@ubuntu-serverirc13:~$

*9. Quelle différence y a-t-il entre donner une valeur vide à une variable et l’utilisation de la commande unset ?*

unset permet de supprimer la variable d'environnement, donc elle n'existera plus. Alors que donner une valeur vide à une variable ne la supprime pas. 


*10. Utilisez la commande echo pour écrire exactement la phrase : $HOME = chemin (où chemin est votre dossier personnel d’après bash)*

    user@ubuntu-serverirc13:~$ vim progm.sh
    --> vim progm.sh
        echo '$HOME =' $HOME
        :w
        :q 

    user@ubuntu-serverirc13:~$ . progm.sh
    $HOME = /home/user
    user@ubuntu-serverirc13:~$