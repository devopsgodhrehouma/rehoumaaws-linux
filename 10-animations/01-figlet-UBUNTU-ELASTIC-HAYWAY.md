# Installation et Configuration de `figlet` sur Ubuntu 22.04

Ce guide explique comment installer et configurer `figlet` sur Ubuntu 22.04 pour afficher un message d'accueil personnalisé "ELASTIC HAYWAY" dans votre terminal.

## Prérequis

- Une instance Ubuntu 22.04 avec accès à Internet.
- Privilèges sudo.

## Étapes d'Installation

### 1. Installation de `figlet`

Sur Ubuntu 22.04, `figlet` peut être installé directement à partir des dépôts de paquets officiels.

```sh
sudo apt update
sudo apt install figlet
```

### 2. Vérification de l'Installation

Pour vérifier que `figlet` est bien installé, exécutez la commande suivante :

```sh
figlet "ELASTIC HAYWAY"
```

### 3. Ajout du Message d'Accueil Personnalisé

Pour afficher le message "ELASTIC HAYWAY" à chaque ouverture de terminal, ajoutez la commande `figlet` à votre fichier de configuration de shell (`~/.bashrc` ou `~/.bash_profile`).

#### Modification de `~/.bashrc` ou `~/.bash_profile`

Ouvrez le fichier de configuration dans un éditeur de texte :

```sh
nano ~/.bashrc
```

ou

```sh
nano ~/.bash_profile
```

Ajoutez la commande `figlet` à la fin du fichier :

```sh
figlet "ELASTIC HAYWAY"
```

Enregistrez et fermez le fichier.

- Pour `nano`, faites `Ctrl+X`, puis `Y` pour confirmer, et appuyez sur `Entrée` pour enregistrer et quitter.

Rechargez votre fichier de configuration pour appliquer les modifications :

```sh
source ~/.bashrc
```

ou

```sh
source ~/.bash_profile
```

## Résultat Attendu

- Écrire :
  
```sh
bash
```

Chaque fois que vous ouvrez un nouveau terminal, vous devriez voir le message suivant :

```
  ______ _           _     _        _    _                              
 |  ____| |         | |   | |      | |  | |                             
 | |__  | | ___  ___| |__ | |_ __  | |__| | __ _ _ __  _ __   ___ _ __  
 |  __| | |/ _ \/ __| '_ \| | '_ \ |  __  |/ _` | '_ \| '_ \ / _ \ '__| 
 | |____| |  __/ (__| | | | | |_) || |  | | (_| | | | | | | |  __/ |    
 |______|_|\___|\___|_| |_|_| .__(_)_|  |_|\__,_|_| |_|_| |_|\___|_|    
                            | |                                         
                            |_|                                         
```

---

# Exercice : Personnalisation et Suppression du Message d'Accueil avec `figlet` sur Ubuntu 22.04

#### **Objectif :**
Personnaliser le message d'accueil de votre terminal avec votre propre nom, puis supprimer cette personnalisation.

#### **Partie 1 : Personnalisation du Message d'Accueil**

1. **Installation de `figlet` :**
   - Mettez à jour vos paquets et installez `figlet` sur votre instance Ubuntu 22.04 avec les commandes suivantes :

   ```sh
   sudo apt update
   sudo apt install figlet
   ```

2. **Vérification de l'Installation :**
   - Vérifiez que `figlet` est bien installé en affichant votre nom dans le terminal :

   ```sh
   figlet "VOTRE NOM"
   ```
   - Remplacez "VOTRE NOM" par votre nom réel.

3. **Modification du Fichier de Configuration du Shell :**
   - Ouvrez votre fichier de configuration (`~/.bashrc` ou `~/.bash_profile`) pour ajouter la commande `figlet` :

   ```sh
   nano ~/.bashrc
   ```
   - À la fin du fichier, ajoutez la commande suivante pour afficher votre nom :

   ```sh
   figlet "VOTRE NOM"
   ```
   - Sauvegardez les modifications (dans `nano`, faites `Ctrl+X`, puis `Y`, et appuyez sur `Entrée`).

4. **Rechargement du Fichier de Configuration :**
   - Appliquez les modifications en rechargeant votre fichier de configuration :

   ```sh
   source ~/.bashrc
   ```
   - Ou, si vous avez modifié `~/.bash_profile`, utilisez :

   ```sh
   source ~/.bash_profile
   ```

5. **Vérification du Résultat :**
   - Ouvrez un nouveau terminal pour vérifier que votre nom s'affiche correctement à chaque démarrage du terminal.

#### **Partie 2 : Suppression du Message d'Accueil Personnalisé**

1. **Suppression de la Personnalisation :**
   - Ouvrez de nouveau votre fichier de configuration du shell (`~/.bashrc` ou `~/.bash_profile`) :

   ```sh
   nano ~/.bashrc
   ```
   - Recherchez la ligne où vous avez ajouté la commande `figlet "VOTRE NOM"` et supprimez cette ligne.

2. **Rechargement du Fichier de Configuration :**
   - Pour appliquer les modifications et revenir à l'état initial, rechargez votre fichier de configuration :

   ```sh
   source ~/.bashrc
   ```
   - Ou, si vous avez modifié `~/.bash_profile`, utilisez :

   ```sh
   source ~/.bash_profile
   ```

3. **Vérification Finale :**
   - Ouvrez un nouveau terminal pour confirmer que le message d'accueil personnalisé a bien été supprimé.

**Consigne :** Faites une capture d'écran avant et après la suppression du message d'accueil pour prouver que vous avez bien réalisé l'exercice.

**Remarque :** Si vous avez des questions ou rencontrez des difficultés lors de cet exercice, n'hésitez pas à demander de l'aide.
