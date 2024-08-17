### Script Bash Interactif : `exercice_linux_interactif.sh`

```bash
#!/bin/bash

# Fonction pour vérifier les réponses des étudiants
check_answer() {
    if [ "$1" == "$2" ]; then
        echo "Correct !"
    else
        echo "Oups, essaye encore."
    fi
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
echo "1. Voulez-vous tester la commande avec 'PWD' ou 'pwd' ?"
read -p "Tapez 'PWD' ou 'pwd' pour tester: " cmd
$cmd
echo "La commande était-elle correcte ?"
read -p "Répondez 'True' ou 'False': " answer1
check_answer "$answer1" "False"

# Question 2
echo ""
echo "Question 2: Lorsque vous tapez une commande, lequel va généralement en premier, les arguments ou les options ?"
echo "2. Voulez-vous tester avec 'ls -l /home/$USER' ou '/home/$USER ls -l' ?"
read -p "Tapez 'ls -l /home/$USER' ou '/home/$USER ls -l': " cmd2
$cmd2
echo "La commande était-elle correcte ?"
read -p "Répondez 'Options' ou 'Arguments': " answer2
check_answer "$answer2" "Options"

# Question 3
echo ""
echo "Question 3: Lequel des suivants n'est pas un moyen correct de combiner des options?"
echo "3. Voulez-vous tester avec '-l -r', '-rl', '-r l', ou '-lr' ?"
read -p "Tapez une combinaison pour tester: " cmd3
ls $cmd3
echo "La commande était-elle correcte ?"
read -p "Répondez '-l -r', '-rl', '-r l', ou '-lr': " answer3
check_answer "$answer3" "-r l"

# Question 4
echo ""
echo "Question 4: Quelle commande affichera votre emplacement actuel dans le système de fichiers?"
echo "4. Voulez-vous tester avec 'pcl', 'pd', 'pwd', ou 'cd' ?"
read -p "Tapez une commande pour tester: " cmd4
$cmd4
echo "La commande était-elle correcte ?"
read -p "Répondez 'pcl', 'pd', 'pwd', ou 'cd': " answer4
check_answer "$answer4" "pwd"

# Question 5
echo ""
echo "Question 5: Quelle commande vous permettra de changer votre répertoire actuel?"
echo "5. Voulez-vous tester avec 'ls', 'cd', 'ch', ou 'chdir' ?"
read -p "Tapez une commande pour tester: " cmd5
$cmd5 dossier_test1
echo "La commande était-elle correcte ?"
read -p "Répondez 'ls', 'cd', 'ch', ou 'chdir': " answer5
check_answer "$answer5" "cd"

# Question 6
echo ""
echo "Question 6: Lequel des suivants n'est pas un exemple de chemin absolu?"
echo "6. Voulez-vous tester en naviguant vers '/home/$USER', '/', ou 'Documents' ?"
read -p "Tapez un chemin pour tester: " cmd6
cd $cmd6
echo "Le chemin était-il un chemin absolu ?"
read -p "Répondez '/home/sysadmin', '/', ou 'Documents': " answer6
check_answer "$answer6" "Documents"

# Question 7
echo ""
echo "Question 7: Le caractère . (point) est utilisé pour représenter:"
echo "7. Voulez-vous tester avec 'ls .' ou un autre répertoire?"
read -p "Tapez une commande pour tester: " cmd7
$cmd7
echo "Le point représente-t-il : Rien, Répertoire de base, Répertoire actuel, ou Répertoire au-dessus?"
read -p "Répondez: " answer7
check_answer "$answer7" "Répertoire actuel"

# Question 8
echo ""
echo "Question 8: La commande ls utilisée sans options ou arguments..."
echo "8. Voulez-vous tester 'ls' ou une autre option?"
read -p "Tapez une commande pour tester: " cmd8
$cmd8
echo "La commande 'ls' affiche-t-elle : un répertoire à lister, le contenu du répertoire en cours, le contenu du répertoire de base, ou génère une erreur?"
read -p "Répondez: " answer8
check_answer "$answer8" "le contenu du répertoire en cours"

# Question 9
echo ""
echo "Question 9: Le premier caractère de la sortie d'une liste longue ls -l indique:"
echo "9. Voulez-vous tester avec 'ls -l'?"
read -p "Tapez une commande pour tester: " cmd9
$cmd9
echo "Le premier caractère indique-t-il : Taille du fichier, Type de fichier, Nombre de liens durs, ou Permissions?"
read -p "Répondez: " answer9
check_answer "$answer9" "Type de fichier"

# Question 10
echo ""
echo "Question 10: Quelle option de la commande ls va trier la sortie par taille de fichier?"
echo "10. Voulez-vous tester avec 'ls -S'?"
read -p "Tapez une commande pour tester: " cmd10
$cmd10
echo "L'option correcte pour trier par taille est-elle : -S, -r, -s, ou -z?"
read -p "Répondez: " answer10
check_answer "$answer10" "-S"

# Question 11
echo ""
echo "Question 11: Lequel des ensembles suivants a les permissions de l'utilisateur propriétaire en surbrillance?"
echo "11. Voulez-vous tester avec 'ls -l' sur un fichier?"
read -p "Tapez une commande pour tester: " cmd11
$cmd11 fichier_a.txt
echo "L'utilisateur propriétaire a-t-il les permissions : rw-rw-r--?"
read -p "Répondez: " answer11
check_answer "$answer11" "rw-rw-r--"

# Question 12
echo ""
echo "Question 12: Lequel des ensembles suivants a les permissions du groupe en surbrillance?"
echo "12. Voulez-vous tester avec 'ls -l' sur un fichier?"
read -p "Tapez une commande pour tester: " cmd12
$cmd12 fichier_b.txt
echo "Le groupe a-t-il les permissions : rw-rw-r--?"
read -p "Répondez: " answer12
check_answer "$answer12" "rw-rw-r--"

# Question 13
echo ""
echo "Question 13: Quelle commande permettra à un utilisateur de modifier les permissions d'un fichier?"
echo "13. Voulez-vous tester avec 'chmod'?"
read -p "Tapez une commande pour tester: " cmd13
$cmd13 755 fichier1.txt
echo "La commande pour modifier les permissions est-elle : perm, chmod, chperm, ou chown?"
read -p "Répondez: " answer13
check_answer "$answer13" "chmod"

# Question 14
echo ""
echo "Question 14: Laquelle des commandes suivantes est utilisée pour changer la propriété d’un fichier?"
echo "14. Voulez-vous tester avec 'chown'?"
read -p "Tapez une commande pour tester: " cmd14
sudo $cmd14 root fichier1.txt
echo "La commande correcte est-elle : chmod, chown, chow, ou ch

perm?"
read -p "Répondez: " answer14
check_answer "$answer14" "chown"

# Question 15
echo ""
echo "Question 15: Parmi les commandes suivantes, laquelle peut être utilisée pour renommer un fichier?"
echo "15. Voulez-vous tester avec 'mv'?"
read -p "Tapez une commande pour tester: " cmd15
$cmd15 fichier_copie.txt fichier_renomme.txt
echo "La commande correcte pour renommer est-elle : rn, name, cp, ou mv?"
read -p "Répondez: " answer15
check_answer "$answer15" "mv"

# Question 16
echo ""
echo "Question 16: La commande mv nécessite au moins deux arguments."
echo "16. Voulez-vous tester avec 'mv'?"
read -p "Tapez une commande pour tester: " cmd16
$cmd16 fichier_renomme.txt fichier_final.txt
echo "La commande mv nécessite-t-elle au moins deux arguments ? True ou False?"
read -p "Répondez: " answer16
check_answer "$answer16" "True"

# Question 17
echo ""
echo "Question 17: La commande cp nécessite au moins deux arguments."
echo "17. Voulez-vous tester avec 'cp'?"
read -p "Tapez une commande pour tester: " cmd17
$cmd17 fichier1.txt fichier_copie.txt
echo "La commande cp nécessite-t-elle au moins deux arguments ? True ou False?"
read -p "Répondez: " answer17
check_answer "$answer17" "True"

# Question 18
echo ""
echo "Question 18: Quelle commande est utilisée pour copier des fichiers au niveau du bit?"
echo "18. Voulez-vous tester avec 'dd'?"
read -p "Tapez une commande pour tester: " cmd18
sudo $cmd18 if=fichier1.txt of=fichier_bit_copie.txt
echo "La commande correcte pour copier au niveau du bit est-elle : dd ou cp?"
read -p "Répondez: " answer18
check_answer "$answer18" "dd"

# Question 19
echo ""
echo "Question 19: La commande rm nécessite au moins deux arguments."
echo "19. Voulez-vous tester avec 'rm'?"
read -p "Tapez une commande pour tester: " cmd19
$cmd19 fichier_final.txt
echo "La commande rm nécessite-t-elle au moins deux arguments ? True ou False?"
read -p "Répondez: " answer19
check_answer "$answer19" "False"

# Question 20
echo ""
echo "Question 20: Quelle option de la commande rm permettra à un utilisateur de supprimer des répertoires?"
echo "20. Voulez-vous tester avec 'rm -r'?"
read -p "Tapez une commande pour tester: " cmd20
$cmd20 dossier_test1
echo "L'option correcte pour supprimer des répertoires est-elle : -l, -r, -d, ou -a?"
read -p "Répondez: " answer20
check_answer "$answer20" "-r"

# Question 21
echo ""
echo "Question 21: Laquelle des commandes suivantes est utilisée pour filtrer le texte?"
echo "21. Voulez-vous tester avec 'grep'?"
read -p "Tapez une commande pour tester: " cmd21
$cmd21 "Erreur" journal.log
echo "La commande correcte pour filtrer le texte est-elle : dd, grep, regex, ou text?"
read -p "Répondez: " answer21
check_answer "$answer21" "grep"

# Question 22
echo ""
echo "Question 22: Laquelle des commandes suivantes correspondra uniquement aux lignes qui se terminent par test?"
echo "22. Voulez-vous tester avec 'grep'?"
read -p "Tapez une commande pour tester: " cmd22
$cmd22 'test$' journal.log
echo "La commande correcte est-elle : grep 'test$', grep 'test^', grep '$test', ou grep '^test'?"
read -p "Répondez: " answer22
check_answer "$answer22" "grep 'test$'"

# Question 23
echo ""
echo "Question 23: Laquelle des lignes suivantes ne correspond pas à la commande grep '[^0-9]' file.txt?"
echo "23. Voulez-vous tester avec 'grep'?"
read -p "Tapez une commande pour tester: " cmd23
echo -e "My favorite food is avocados.\n3121991\nHello my name is Joe.\nI am 37 years old." > testfile.txt
$cmd23 '[^0-9]' testfile.txt
echo "La ligne correcte est-elle : My favorite food is avocados., 3121991, Hello my name is Joe., ou I am 37 years old.?"
read -p "Répondez: " answer23
check_answer "$answer23" "3121991"

# Question 24
echo ""
echo "Question 24: Laquelle des lignes suivantes correspond à la commande grep 'b[oe]t' file.txt?"
echo "24. Voulez-vous tester avec 'grep'?"
read -p "Tapez une commande pour tester: " cmd24
echo -e "boet\nbet\nbeet\nboot" > testfile2.txt
$cmd24 'b[oe]t' testfile2.txt
echo "La ligne correcte est-elle : boet, bet, beet, ou boot?"
read -p "Répondez: " answer24
check_answer "$answer24" "bet"

# Question 25
echo ""
echo "Question 25: Laquelle des commandes suivantes n’arrête pas le système immédiatement?"
echo "25. Voulez-vous tester avec 'shutdown'?"
read -p "Tapez une commande pour tester: " cmd25
echo "La commande correcte est-elle : shutdown now 'Goodbye World!', shutdown +0, shutdown now, ou shutdown?"
read -p "Répondez: " answer25
check_answer "$answer25" "shutdown"

# Question 26
echo ""
echo "Question 26: Lequel des suivants supprime tous les fichiers d'un paquet?"
echo "26. Voulez-vous tester avec 'apt-get purge'?"
read -p "Tapez une commande pour tester: " cmd26
echo "La commande correcte est-elle : apt-get delete, apt-get purge, apt-get remove, ou apt-get trash?"
read -p "Répondez: " answer26
check_answer "$answer26" "apt-get purge"

# Question 27
echo ""
echo "Question 27: Parmi les commandes suivantes, laquelle doit être exécutée avant d'installer un paquet?"
echo "27. Voulez-vous tester avec 'apt-get update'?"
read -p "Tapez une commande pour tester: " cmd27
echo "La commande correcte est-elle : apt-get install, apt-get search, apt-get update, ou apt-get upgrade?"
read -p "Répondez: " answer27
check_answer "$answer27" "apt-get update"

# Question 28
echo ""
echo "Question 28: L’administrateur du système (root) peut changer le mot de passe de n'importe quel utilisateur."
echo "28. Voulez-vous tester avec 'passwd'?"
read -p "Tapez une commande pour tester: " cmd28
sudo $cmd28
echo "Le root peut-il changer n'importe quel mot de passe ? True ou False?"
read -p "Répondez: " answer28
check_answer "$answer28" "True"

# Question 29
echo ""
echo "Question 29: Quelle option peut être utilisée pour afficher des informations sur le statut du mot de passe de l'utilisateur actuel?"
echo "29. Voulez-vous tester avec 'passwd -S'?"
read -p "Tapez une commande pour tester: " cmd29
$cmd29
echo "L'option correcte est-elle : -I, -S, -s, ou -i?"
read -p "Répondez: " answer29
check_answer "$answer29" "-S"

# Question 30
echo ""
echo "Question 30: La commande ping utilise des adresses IP pour identifier un ordinateur sur un réseau."
echo "30. Voulez-vous tester avec 'ping'?"
read -p "Tapez une commande pour tester: " cmd30
$cmd30 8.8.8.8
echo "La commande ping utilise-t-elle des adresses IP ? True ou False?"
read -p "Répondez: " answer30
check_answer "$answer30" "True"

echo "Exercice terminé !"
```

### Instructions pour les étudiants

1. **Téléchargez le script** : Téléchargez le script `exercice_linux_interactif.sh` sur votre système Ubuntu 22.04.

2. **Rendez le script exécutable** : Pour exécuter le script, il faut d'abord le rendre exécutable :
   ```bash
   chmod +x exercice_linux_interactif.sh
   ```

3. **Exécutez le script** : Lancez le script pour commencer les exercices interactifs :
   ```bash
   ./exercice_linux_interactif.sh
   ```

4. **Interagissez avec le script** : À chaque question, le script vous demandera si vous souhaitez tester une commande. Vous pouvez alors entrer la commande suggérée pour voir ce qui se passe avant de répondre à la question.

5. **Recevez un feedback immédiat** : Après avoir testé et répondu, le script vous dira si votre réponse est correcte ou non et vous encouragera à essayer à nouveau si nécessaire.

6. **Continuez avec

 les autres questions** : Le script continuera à poser les questions suivantes, vous permettant de tester les commandes avant de répondre. 

Ce script interactif vous permet de non seulement répondre aux questions mais aussi d'explorer et de tester les commandes dans un environnement pratique avant de donner votre réponse, renforçant ainsi l'apprentissage.
