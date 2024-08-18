# Examen Linux Ubuntu 22.04 : Gestion des Permissions - Partie 01
## 1. Connexion en tant que Superutilisateur

```bash
su
# Entrez le mot de passe du superutilisateur
```

## 2. Création des Utilisateurs

```bash
# Assurez-vous que les utilisateurs existent ou créez-les
useradd -m jean
useradd -m paul
useradd -m marie
useradd -m sophie
```

## 3. Création du Dossier et des Fichiers

```bash
# Créer le dossier shared_data et les sous-dossiers/fichiers nécessaires
mkdir -p /home/shared_data/dossier1

touch /home/shared_data/file1.txt
touch /home/shared_data/file2.txt
touch /home/shared_data/dossier1/script1.sh
touch /home/shared_data/dossier1/script2.sh
```

## 4. Attribution des Propriétaires et des Permissions (Configurées Incorrectement)

```bash
# Configuration des permissions et propriétaires (avec erreurs intentionnelles)
chown jean:paul /home/shared_data/file1.txt
chmod 400 /home/shared_data/file1.txt

chown paul:jean /home/shared_data/file2.txt
chmod 600 /home/shared_data/file2.txt

chown -R marie:marie /home/shared_data/dossier1
chmod 777 /home/shared_data/dossier1
chmod 644 /home/shared_data/dossier1/script1.sh
chmod 000 /home/shared_data/dossier1/script2.sh

chown -R sophie:jean /home/shared_data
chmod -R 444 /home/shared_data
```

## 5. Scénarios de Tests de Permission et Identification des Problèmes

**Scénario 1** : Jean doit lire `file1.txt`.

- **Commande** : `su jean -c 'cat /home/shared_data/file1.txt'`
- **Résultat Attendu** : Échec (Permission refusée)
- **Question** : Pourquoi Jean ne peut-il pas lire ce fichier, et quelle commande résoudrait ce problème ?

**Scénario 2** : Paul doit modifier `file2.txt`.

- **Commande** : `su paul -c 'echo "Modification" >> /home/shared_data/file2.txt'`
- **Résultat Attendu** : Échec (Permission refusée)
- **Question** : Pourquoi Paul ne peut-il pas écrire dans ce fichier, et comment résoudre ce problème ?

**Scénario 3** : Marie doit exécuter `script1.sh` dans `dossier1`.

- **Commande** : `su marie -c 'bash /home/shared_data/dossier1/script1.sh'`
- **Résultat Attendu** : Échec (Permission refusée)
- **Question** : Quelle est la cause de l'erreur, et comment Marie peut-elle exécuter le script ?

**Scénario 4** : Sophie doit créer un nouveau fichier dans `shared_data`.

- **Commande** : `su sophie -c 'touch /home/shared_data/newfile.txt'`
- **Résultat Attendu** : Échec (Permission refusée)
- **Question** : Pourquoi Sophie ne peut-elle pas créer de fichier, et comment corriger cette situation ?

**Scénario 5** : Paul doit accéder en écriture à `script2.sh`.

- **Commande** : `su paul -c 'nano /home/shared_data/dossier1/script2.sh'`
- **Résultat Attendu** : Échec (Permission refusée)
- **Question** : Pourquoi l'accès est refusé, et quelle commande permettrait à Paul d'éditer ce script ?

## 6. Résolution des Problèmes

Vous devez identifier et corriger les problèmes de permission identifiés dans chaque scénario. Pour chaque scénario :

1. **Explication** : Expliquez pourquoi l'utilisateur n'a pas pu réaliser l'action demandée.
2. **Commande Corrective** : Fournissez la ou les commandes nécessaires pour corriger les permissions et permettre à l'utilisateur de réaliser l'action.

---

### Questions de Réflexion

1. **Pourquoi est-il important de tester les permissions après les avoir configurées ?**
2. **Quels risques pourraient découler d'une mauvaise configuration des permissions sur un serveur Linux ?**
3. **Quelles pratiques recommanderiez-vous pour éviter les erreurs de configuration des permissions ?**

