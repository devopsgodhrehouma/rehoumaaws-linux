### Script Bash Interactif : `exercice_linux_choix.sh`

```bash
#!/bin/bash

score=0
total_questions=30

# Fonction pour vérifier la commande
test_command() {
    local correct_cmd="$1"
    local user_cmd=""
    while true; do
        echo "Options: $2"
        read -p "Choisissez une option: " user_cmd
        if [ "$user_cmd" == "$correct_cmd" ]; then
            echo "Correct !"
            score=$((score + 1))
            break
        else
            echo "Oups, ce n'est pas la bonne commande. Essayez encore."
        fi
    done
}

# Création d'un répertoire de travail
mkdir -p /home/$USER/exercice_linux
cd /home/$USER/exercice_linux

# Création de fichiers pour l'exercice
echo "Ceci est un fichier de test pour apprendre les commandes Linux." > fichier1.txt
echo "Une autre ligne de texte pour pratique grep." >> fichier1.txt
echo "Le fichier doit être modifié avec les bonnes permissions." >> fichier1.txt
echo "Apprenez à combiner les options et les arguments dans les commandes Linux." > fichier2.txt

# Création de fichiers supplémentaires avec différentes permissions
touch fichier_a.txt
touch fichier_b.txt
chmod 644 fichier_a.txt
chmod 600 fichier_b.txt

# Création de répertoires et de fichiers pour simuler une structure de fichiers
mkdir -p dossier_test1 dossier_test2
echo "Fichier dans dossier_test1" > dossier_test1/fichier_c.txt
echo "Fichier dans dossier_test2" > dossier_test2/fichier_d.txt

# Copie de fichiers pour des exercices de manipulation
cp fichier1.txt fichier_copie.txt
mv fichier2.txt fichier_renomme.txt

# Création de journaux pour des exercices avec grep
for i in {1..100}; do echo "Ligne $i : Tout fonctionne normalement." >> journal.log; done
echo "Ligne 101 : Erreur critique détectée." >> journal.log
for i in {102..200}; do echo "Ligne $i : Tout fonctionne normalement." >> journal.log; done

# Changement de propriétaire de fichier pour un exercice de chown
sudo chown root:root fichier_b.txt

# Début des questions interactives
echo "L'environnement de test a été préparé dans /home/$USER/exercice_linux."
echo "Vous pouvez maintenant commencer les exercices."
echo ""

# Question 1
echo "Question 1: Les commandes sont sensibles à la casse."
test_command "ls" "ls, LS"

# Question 2
echo ""
echo "Question 2: Lorsque vous tapez une commande, lequel va généralement en premier, les arguments ou les options ?"
test_command "ls -l /home/$USER" "/home/$USER ls -l, ls -l /home/$USER"

# Question 3
echo ""
echo "Question 3: Lequel des suivants n'est pas un moyen correct de combiner des options?"
test_command "ls -r l" "-l -r, -rl, -r l, -lr"

# Question 4
echo ""
echo "Question 4: Quelle commande affichera votre emplacement actuel dans le système de fichiers?"
test_command "pwd" "pcl, pd, pwd, cd"

# Question 5
echo ""
echo "Question 5: Quelle commande vous permettra de changer votre répertoire actuel?"
test_command "cd dossier_test1" "ls dossier_test1, cd dossier_test1, ch dossier_test1, chdir dossier_test1"

# Question 6
echo ""
echo "Question 6: Lequel des suivants n'est pas un exemple de chemin absolu?"
test_command "Documents" "/home/sysadmin, /, Documents"

# Question 7
echo ""
echo "Question 7: Le caractère . (point) est utilisé pour représenter:"
test_command "ls ." "Répertoire de base, Répertoire actuel, Répertoire au-dessus du répertoire actuel, Rien"

# Question 8
echo ""
echo "Question 8: La commande ls utilisée sans options ou arguments..."
test_command "ls" "affiche le contenu du répertoire en cours, demande un répertoire à lister, affiche le contenu du répertoire de base, génère une erreur"

# Question 9
echo ""
echo "Question 9: Le premier caractère de la sortie d'une liste longue ls -l indique:"
test_command "ls -l" "Taille du fichier, Type de fichier, Nombre de liens durs, Permissions"

# Question 10
echo ""
echo "Question 10: Quelle option de la commande ls va trier la sortie par taille de fichier?"
test_command "ls -S" "-S, -r, -s, -z"

# Question 11
echo ""
echo "Question 11: Lequel des ensembles suivants a les permissions de l'utilisateur propriétaire en surbrillance?"
test_command "rw-rw-r--" "rw-rw-r--, rw-rw-r--, rw-rw-r--, rw-rw-r--"

# Question 12
echo ""
echo "Question 12: Lequel des ensembles suivants a les permissions du groupe en surbrillance?"
test_command "rw-rw-r--" "rw-rw-r--, rw-rw-r--, rw-rw-r--, rw-rw-r--"

# Question 13
echo ""
echo "Question 13: Quelle commande permettra à un utilisateur de modifier les permissions d'un fichier?"
test_command "chmod" "perm, chmod, chperm, chown"

# Question 14
echo ""
echo "Question 14: Laquelle des commandes suivantes est utilisée pour changer la propriété d’un fichier?"
test_command "chown" "chmod, chown, chow, chperm"

# Question 15
echo ""
echo "Question 15: Parmi les commandes suivantes, laquelle peut être utilisée pour renommer un fichier?"
test_command "mv" "rn, name, cp, mv"

# Question 16
echo ""
echo "Question 16: La commande mv nécessite au moins deux arguments."
test_command "True" "True, False"

# Question 17
echo ""
echo "Question 17: La commande cp nécessite au moins deux arguments."
test_command "True" "True, False"

# Question 18
echo ""
echo "Question 18: Quelle commande est utilisée pour copier des fichiers au niveau du bit?"
test_command "dd" "dd, cp"

# Question 19
echo ""
echo "Question 19: La commande rm nécessite au moins deux arguments."
test_command "False" "True, False"

# Question 20
echo ""
echo "Question 20: Quelle option de la commande rm permettra à un utilisateur de supprimer des répertoires?"
test_command "rm -r" "-l, -r, -d, -a"

# Question 21
echo ""
echo "Question 21: Laquelle des commandes suivantes est utilisée pour filtrer le texte?"
test_command "grep" "dd, grep, regex, text"

# Question 22
echo ""
echo "Question 22: Laquelle des commandes suivantes correspondra uniquement aux lignes qui se terminent par test?"
test_command "grep 'test$'" "grep 'test$', grep 'test^', grep '$test', grep '^test'"

# Question 23
echo ""
echo "Question 23: Laquelle des lignes suivantes ne correspond pas à la commande grep '[^0-9]' file.txt?"
test_command "3121991" "My favorite food is avocados., 3121991, Hello my name is Joe., I am 37 years old."

# Question 24
echo ""
echo "Question 24: Laquelle des lignes suivantes correspond à la commande grep 'b[oe]t' file.txt?"
test_command "bet" "boet, bet, beet, boot"

# Question 25
echo ""
echo "Question 25: Laquelle des commandes suivantes n’arrête pas le système immédiatement?"
test_command "shutdown +0" "shutdown now 'Goodbye World!', shutdown +0, shutdown now, shutdown"

# Question 26
echo ""
echo "Question 26: Lequel des suivants supprime tous les fichiers d'un paquet?"
test_command "apt-get purge" "apt-get delete, apt-get purge, apt-get remove, apt-get trash"

# Question 27
echo ""
echo "Question 27: Parmi les commandes suivantes, laquelle doit être exécutée avant d'installer un paquet?"
test_command "apt-get update" "apt-get install, apt-get search, apt-get update, apt-get upgrade"

# Question 28
echo ""
echo "Question 28: L’administrateur du système (root) peut changer le mot de passe de n'importe quel utilisateur."
test_command "True" "True, False"

# Question 29
echo ""
echo "Question 29: Quelle option peut être utilisée pour afficher des informations sur le statut du mot de passe de l'utilisateur actuel?"
test_command "-S" "-I, -S, -s, -i"

# Question 30
echo ""
echo "Question 30: La commande ping utilise des adresses IP pour identifier un ordinateur sur un réseau."
test_command "True" "True, False"

# Affichage du score final
echo "Vous avez terminé l'exercice avec un score de $score sur $total_questions."
```


### Instructions pour les étudiants 

1. **Téléchargez le script** : Téléchargez le script `exercice_linux_choix.sh` sur votre système Ubuntu 22.04.

2. **Rendez le script exécutable** : Pour exécuter le script, il faut d'abord le rendre exécutable :
   ```bash
   chmod +x exercice_linux_choix.sh
   ```

3. **Exécutez le script** : Lancez le script pour commencer les exercices interactifs :
   ```bash
   ./exercice_linux_choix.sh
   ```

4. **Répondez aux questions** : À chaque question, le script vous proposera plusieurs options. Vous devrez choisir la bonne commande parmi les options données. Si votre choix est incorrect, vous aurez la possibilité de réessayer jusqu'à ce que vous sélectionniez la bonne réponse.

5. **Validez vos réponses** : Une fois que vous avez trouvé la bonne commande, le script vous demandera de la retaper pour confirmer votre réponse.

6. **Recevez un feedback immédiat** : Le script vous indiquera si votre commande est correcte ou non et vous permettra de réessayer si nécessaire. À la fin de l'exercice, votre score total sera affiché.

7. **Apprenez en pratiquant** : Ce script est conçu pour renforcer vos compétences en ligne de commande Linux en vous permettant de pratiquer et de tester différentes commandes dans un environnement interactif.


