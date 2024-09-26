### Atelier MongoDB : Manipulation des opérations CRUD

L'objectif de cet atelier est de manipuler les opérations CRUD (Create, Read, Update, Delete) avec MongoDB en utilisant des indices sans fournir directement les solutions. Les participants devront suivre les étapes données et réaliser les tâches en s'aidant des pistes fournies.

---

#### 1. **Créer une base de données appelée "contact"**
   - **Indice** : Pensez à utiliser une commande MongoDB pour sélectionner ou créer une base de données. Il s’agit de la même commande pour choisir une base existante ou en créer une nouvelle.

#### 2. **Créer une collection appelée "contactlist"**
   - **Indice** : Recherchez la commande qui permet de créer une collection dans MongoDB. Elle se fait automatiquement lorsque vous insérez un premier document si elle n’existe pas encore.

#### 3. **Insérer des documents dans "contactlist"**
   - **Indice** : Utilisez l'opération d'insertion pour ajouter des documents. Pensez à insérer plusieurs contacts à la fois à l'aide d'une commande qui permet d'ajouter plusieurs documents d’un coup.

   **Contacts à insérer** :
   - Nom : Ben, Prénom : Moris, Email : ben@gmail.com, âge : 26
   - Nom : Kefi, Prénom : Seif, Email : kefi@gmail.com, âge : 15
   - Nom : Emilie, Prénom : Brouge, Email : emilie.b@gmail.com, âge : 40
   - Nom : Alex, Prénom : Brown, âge : 4
   - Nom : Denzel, Prénom : Washington, âge : 3

---

### Opérations CRUD

#### 4. **Afficher toute la liste des contacts**
   - **Indice** : Il existe une commande pour afficher tous les documents d'une collection. Cherchez une commande MongoDB qui renvoie tous les enregistrements d'une collection.

#### 5. **Afficher toutes les informations d'une personne en utilisant son ID**
   - **Indice** : Vous devez utiliser une commande de recherche. Pour cibler une personne par son ID, MongoDB utilise un identifiant unique (_id). Utilisez cet identifiant pour rechercher un document spécifique.

#### 6. **Afficher tous les contacts dont l’âge est supérieur à 18 ans**
   - **Indice** : Utilisez un opérateur de comparaison pour filtrer les résultats en fonction de l'âge. MongoDB dispose d'opérateurs pour ce type de recherche.

#### 7. **Afficher tous les contacts avec un âge supérieur à 18 ans et un nom contenant "ah"**
   - **Indice** : Combinez un filtre basé sur l’âge avec une recherche par motif (regex) pour trouver les noms contenant un certain ensemble de lettres.

#### 8. **Modifier le prénom du contact "Kefi Seif" en "Kefi Anis"**
   - **Indice** : Cherchez une commande MongoDB qui permet de mettre à jour un document. Assurez-vous d’utiliser la condition correcte pour identifier le bon document et changer uniquement le champ souhaité.

#### 9. **Supprimer les contacts âgés de moins de 5 ans**
   - **Indice** : Utilisez une commande de suppression. Pensez à combiner cette commande avec une condition basée sur l’âge pour supprimer uniquement les contacts répondant au critère d'âge donné.

#### 10. **Afficher à nouveau toute la liste des contacts**
   - **Indice** : Réutilisez la commande déjà utilisée pour afficher tous les contacts. Cette étape permet de vérifier que la suppression et les modifications ont été appliquées correctement.

---

### **Conseils finaux :**
- N’oubliez pas de **documenter vos résultats** à l’aide de **captures d’écran** à chaque étape, surtout après les opérations importantes (affichage, modification, suppression).
