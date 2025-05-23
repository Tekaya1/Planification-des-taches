# Planification des Tâches

## I) CRON

### 1) Commandes Utiles
- 📂 **Lister les fichiers cron**  
    ```bash
    ls -l /cron
    ```
    (Appuyez sur la touche `Tab` pour compléter)

- 📄 **Afficher le contenu de crontab**  
    ```bash
    cat /etc/crontab
    ```

### 2) Créer une Tâche Planifiée
- ✏️ **Modifier crontab**  
    ```bash
    crontab -e
    ```

#### Exemples :
- 🗓️ **Planifier une tâche qui affiche la date dans un fichier nommé `fich` chaque 5 mars à 8h30**  
    ```bash
    30 08 05 03 * date >> fich
    ```
    - `30` : minute  
    - `08` : heure  
    - `05` : jour  
    - `03` : mois  
    - `*`  : jour de la semaine  

- 🗓️ **Chaque 5, 6, et 7 mars à 7h30 et 8h30**  
    ```bash
    30 7,8 5-7 03 * date >> fich
    ```

- 🕒 **Chaque 5 minutes à 9h (9h00, 9h05, ..., 9h55)**  
    ```bash
    */5 9 * * * date >> fich
    ```

- 🕒 **Chaque 5 minutes à 9h et 10h**  
    ```bash
    */5 9,10 * * * date >> fich
    ```
    - Test : 9h00 → 9h55 et 10h00 → 10h55

### 3) Édition des Tâches
- 📋 **Lister les tâches planifiées**  
    ```bash
    crontab -l
    ```

- ✏️ **Éditer la table cron**  
    ```bash
    crontab -e
    ```

- 🗑️ **Vider la table cron**  
    ```bash
    crontab -r
    ```

- 👤 **Éditer la table d'un utilisateur (en tant que root)**  
    ```bash
    crontab -e -u <user>
    ```

- 📋 **Lister la table d'un utilisateur**  
    ```bash
    crontab -l -u <user>
    ```

- 🗑️ **Supprimer la table d'un utilisateur**  
    ```bash
    crontab -r -u <user>
    ```

---

## II) AT

### 1) Bloquer un Utilisateur pour Planifier des Tâches
- 🚫 **Ajouter un utilisateur dans `/cron.deny`**  
    ```bash
    vim /cron.deny
    ```
    (Ajoutez le nom de l'utilisateur)

- ✅ **Ajouter un utilisateur dans `/cron.allow`**  
    ```bash
    vim /cron.allow
    ```
    (Ajoutez le nom de l'utilisateur)

### 2) Vérifier le Statut du Service `atd`
- 🔍 **Vérifier le statut**  
    ```bash
    systemctl status atd
    ```

### 3) Créer une Tâche avec la Commande `at`
- 🕒 **Planifier une tâche à 21h**  
    ```bash
    at 21:00
    ```
    (Dans l'invite `at>`, entrez : `date > fich`)

### 4) Gestion des Tâches
- 📋 **Lister les tâches**  
    ```bash
    at -l
    ```
    ou  
    ```bash
    atq
    ```

- 🗑️ **Supprimer une tâche**  
    ```bash
    atrm <id_tache>
    ```

### 5) Planifier une Tâche avec une Date
- 📅 **Exemple : 21h le 10 mai 2025**  
    ```bash
    at 21:00 2025-05-10
    ```

### 6) Planifier une Tâche avec des Mots-Clés
- ⏳ **Exemple : dans 2 minutes, 2 semaines, 2 jours, ou 2 mois**  
    ```bash
    at now + 2 min
    ```
    ou  
    ```bash
    at now + 2 weeks
    ```
