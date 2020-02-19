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
    
## Programmation Bash
*Vous enregistrerez vos scripts dans un dossier script que vous créerez dans votre répertoire personnel. Tous les scripts sont bien entendu à tester. Ajoutez le chemin vers script à votre PATH de manière permanente.*

    mkdir script
    PATH=$PATH:~/script
    user@ubuntu-serverirc13:~$ cd script/
    user@ubuntu-serverirc13:~/script$


## Exercice 2  Contrôle de mot de passe

*Écrivez un script testpwd.sh qui demande de saisir un mot de passe et vérifie s’il correspond ou non au contenu d’une variable PASSWORD dont le contenu est codé en dur dans le script. Le mot de passe saisi par l’utilisateur ne doit pas s’afficher.*

    
    PASSWORD="Pwd"
    read -s -p "Mot de passe?" saisie

    if [ $saisie = $PASSWORD ] ; then
      echo -e "\nSuper c'est correct !"
    else
      echo -e "\nMauvais mot de passe !"
    fi
    
Il ne faut pas oublier de changer les droits

    user@ubuntu-serverirc13:~/script$ chmod +x testpwd.sh
    user@ubuntu-serverirc13:~/script$ ./testpwd.sh
    Mot de passe?
    Super c'est correct !
    
Note: read -s permet de ne pas afficher le texte saisi par l'utilisateur.

## Exercice 3 

*Ecrivez un script qui prend un paramètre et utilise la fonction suivante pour vérifier que ce paramètre
est un nombre réel :*
    
    #!/bin/bash
    
    function is_number()
    {
            re='^[+-]?[0-9]+([.][0-9]+)?$'
            if ! [[ $1 =~ $re ]] ; then
                    return 1
            else
                    return 0
            fi
    }

    is_number $1
    if [[ $? = 0 ]] ; then
            echo "Nombre rationel"
    else
            echo "Erreur"
    fi

Note : $? permet de recuperer le code d'erreur de la fonction précédente. 

0 -> tout s'est bien passé

1 -> erreur n°1

2 -> erreur n°2

## Exercice 4. Contrôle d’utilisateur
*Écrivez un script qui vérifie l’existence d’un utilisateur dont le nom est donné en paramètre du script. Si le script est appelé sans nom d’utilisateur, il affiche le message : ”Utilisation : nom_du_script nom_utilisateur”, où nom_du_script est le nom de votre script récupéré automatiquement (si vous changez le nom de votre script, le message doit changer automatiquement)*



    




