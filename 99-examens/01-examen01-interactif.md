### Script Bash Interactif : `exercice_linux_interactif_v2.sh`

```bash
#!/bin/bash

# Fonction pour vérifier la commande et permettre à l'étudiant de réessayer
test_command() {
    local correct_cmd="$1"
    while true; do
        read -p "Tapez une commande pour tester: " user_cmd
        if [ "$user_cmd" == "$correct_cmd" ]; then
            $user_cmd
            echo "Correct ! Maintenant, tapez la même commande pour valider."
            read -p "Tapez la commande: " validate_cmd
            if [ "$validate_cmd" == "$correct_cmd" ]; then
                echo "Validé !"
                break
            else
                echo "Vous n'avez pas tapé la commande correcte. Essayez à nouveau."
            fi
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
echo "Essayez de tester la commande correcte."
test_command "pwd"

# Question 2
echo ""
echo "Question 2: Lorsque vous tapez une commande, lequel va généralement en premier, les arguments ou les options ?"
echo "Testez la bonne commande pour lister les fichiers du répertoire personnel."
test_command "ls -l /home/$USER"

# Question 3
echo ""
echo "Question 3: Lequel des suivants n'est pas un moyen correct de combiner des options?"
echo "Testez différentes combinaisons pour trouver la bonne façon de combiner les options."
test_command "ls -l -r"

# Question 4
echo ""
echo "Question 4: Quelle commande affichera votre emplacement actuel dans le système de fichiers?"
echo "Testez jusqu'à ce que vous trouviez la commande qui affiche votre répertoire actuel."
test_command "pwd"

# Question 5
echo ""
echo "Question 5: Quelle commande vous permettra de changer votre répertoire actuel?"
echo "Testez la commande correcte pour naviguer vers un autre répertoire."
test_command "cd dossier_test1"

# Question 6
echo ""
echo "Question 6: Lequel des suivants n'est pas un exemple de chemin absolu?"
echo "Testez la commande correcte pour naviguer vers un chemin absolu."
test_command "cd /home/$USER"

# Question 7
echo ""
echo "Question 7: Le caractère . (point) est utilisé pour représenter:"
echo "Testez la commande correcte pour lister les fichiers dans le répertoire actuel."
test_command "ls ."

# Question 8
echo ""
echo "Question 8: La commande ls utilisée sans options ou arguments..."
echo "Testez la commande correcte pour voir ce que fait ls sans options."
test_command "ls"

# Question 9
echo ""
echo "Question 9: Le premier caractère de la sortie d'une liste longue ls -l indique:"
echo "Testez la commande correcte pour voir la liste longue des fichiers."
test_command "ls -l"

# Question 10
echo ""
echo "Question 10: Quelle option de la commande ls va trier la sortie par taille de fichier?"
echo "Testez la commande correcte pour trier les fichiers par taille."
test_command "ls -S"

# Question 11
echo ""
echo "Question 11: Lequel des ensembles suivants a les permissions de l'utilisateur propriétaire en surbrillance?"
echo "Testez la commande correcte pour vérifier les permissions d'un fichier."
test_command "ls -l fichier_a.txt"

# Question 12
echo ""
echo "Question 12: Lequel des ensembles suivants a les permissions du groupe en surbrillance?"
echo "Testez la commande correcte pour vérifier les permissions du groupe."
test_command "ls -l fichier_b.txt"

# Question 13
echo ""
echo "Question 13: Quelle commande permettra à un utilisateur de modifier les permissions d'un fichier?"
echo "Testez la commande correcte pour changer les permissions d'un fichier."
test_command "chmod 755 fichier1.txt"

# Question 14
echo ""
echo "Question 14: Laquelle des commandes suivantes est utilisée pour changer la propriété d’un fichier?"
echo "Testez la commande correcte pour changer la propriété d'un fichier."
test_command "sudo chown $USER fichier1.txt"

# Question 15
echo ""
echo "Question 15: Parmi les commandes suivantes, laquelle peut être utilisée pour renommer un fichier?"
echo "Testez la commande correcte pour renommer un fichier."
test_command "mv fichier_copie.txt fichier_renomme.txt"

# Question 16
echo ""
echo "Question 16: La commande mv nécessite au moins deux arguments."
echo "Testez la commande correcte avec mv."
test_command "mv fichier_renomme.txt fichier_final.txt"

# Question 17
echo ""
echo "Question 17: La commande cp nécessite au moins deux arguments."
echo "Testez la commande correcte avec cp."
test_command "cp fichier1.txt fichier_copie.txt"

# Question 18
echo ""
echo "Question 18: Quelle commande est utilisée pour copier des fichiers au niveau du bit?"
echo "Testez la commande correcte pour une copie au niveau du bit."
test_command "sudo dd if=fichier1.txt of=fichier_bit_copie.txt"

# Question 19
echo ""
echo "Question 19: La commande rm nécessite au moins deux arguments."
echo "Testez la commande correcte avec rm."
test_command "rm fichier_final.txt"

# Question 20
echo ""
echo "Question 20: Quelle option de la commande rm permettra à un utilisateur de supprimer des répertoires?"
echo "Testez la commande correcte pour supprimer un répertoire."
test_command "rm -r dossier_test1"

# Question 21
echo ""
echo "Question 21: Laquelle des commandes suivantes est utilisée pour filtrer le texte?"
echo "Testez la commande correcte pour filtrer le contenu d'un fichier texte."
test_command "grep 'Erreur' journal.log"

# Question 22
echo ""
echo "Question 22: Laquelle des commandes suivantes correspondra uniquement aux lignes qui se terminent par test?"
echo "Testez la commande correcte pour trouver les lignes se terminant par 'test'."
test_command "grep 'test$' journal.log"

# Question 23
echo ""
echo "Question 23: Laquelle des lignes suivantes ne correspond pas à la commande grep '[^0-9]' file.txt?"
echo "Testez la commande correcte pour exclure les lignes numériques."
echo -e "My favorite food is avocados.\n3121991\nHello my name is Joe.\nI am 37 years old." > testfile.txt
test_command "grep '[^0-9]' testfile.txt"

# Question 24
echo ""
echo "Question 24: Laquelle des lignes suivantes correspond à la commande grep 'b[oe]t' file.txt?"
echo "Testez la commande correcte pour trouver les mots correspondants."
echo -e "boet\nbet\nbeet\nboot" > testfile2.txt
test_command "grep 'b[oe]t' testfile2.txt"

# Question 25
echo ""
echo "Question 25: Laquelle des commandes suivantes n’arrête pas le système immédiatement?"
echo "Testez la commande correcte pour planifier un arrêt du système."
test_command "shutdown +0"

# Question 26
echo ""
echo "Question 26: Lequel des suivants supprime tous les fichiers d'un paquet?"
echo "Testez la commande correcte pour supprimer un paquet complètement."
test_command "sudo apt-get purge nom_paquet"

# Question 27
echo ""


echo "Question 27: Parmi les commandes suivantes, laquelle doit être exécutée avant d'installer un paquet?"
echo "Testez la commande correcte pour mettre à jour la liste des paquets."
test_command "sudo apt-get update"

# Question 28
echo ""
echo "Question 28: L’administrateur du système (root) peut changer le mot de passe de n'importe quel utilisateur."
echo "Testez la commande correcte pour changer le mot de passe d'un utilisateur."
test_command "sudo passwd utilisateur"

# Question 29
echo ""
echo "Question 29: Quelle option peut être utilisée pour afficher des informations sur le statut du mot de passe de l'utilisateur actuel?"
echo "Testez la commande correcte pour afficher le statut du mot de passe."
test_command "passwd -S $USER"

# Question 30
echo ""
echo "Question 30: La commande ping utilise des adresses IP pour identifier un ordinateur sur un réseau."
echo "Testez la commande correcte pour vérifier la connectivité réseau."
test_command "ping 8.8.8.8"

echo "Exercice terminé !"
```

### Instructions pour les étudiants

1. **Téléchargez le script** : Téléchargez le script `exercice_linux_interactif_v2.sh` sur votre système Ubuntu 22.04.

2. **Rendez le script exécutable** : Pour exécuter le script, il faut d'abord le rendre exécutable :
   ```bash
   chmod +x exercice_linux_interactif_v2.sh
   ```

3. **Exécutez le script** : Lancez le script pour commencer les exercices interactifs :
   ```bash
   ./exercice_linux_interactif_v2.sh
   ```

4. **Interagissez avec le script** : À chaque question, le script vous demandera de tester différentes commandes jusqu'à ce que vous trouviez la bonne. Une fois que vous avez trouvé la commande correcte, vous devrez la retaper pour valider votre réponse.

5. **Recevez un feedback immédiat** : Le script vous donnera un retour immédiat, vous indiquant si votre commande est correcte ou si vous devez essayer à nouveau.

6. **Continuez avec les autres questions** : Le script continuera à poser les questions suivantes, vous permettant de tester et d'apprendre les commandes Linux tout en renforçant vos connaissances.

Ce script interactif est conçu pour guider les étudiants pas à pas, leur permettant de tester et de valider chaque commande, ce qui renforce leur compréhension et leur maîtrise des commandes Linux de base.
