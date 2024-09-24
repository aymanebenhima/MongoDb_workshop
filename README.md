# MongoDb_workshop

Atelier pratique sur MongoDB avec des commandes pour créer une base de données et effectuer des opérations CRUD (Create, Read, Update, Delete).

### 1. **Installation de MongoDB** (si ce n’est pas déjà fait)
- Sur Windows, utilisez l'[installateur MongoDB](https://www.mongodb.com/try/download/community) pour installer MongoDB.
- Sur macOS, utilisez Homebrew:
  ```bash
  brew tap mongodb/brew
  brew install mongodb-community@6.0
  ```
- Sur Ubuntu/Debian, utilisez:
  ```bash
  sudo apt-get install -y mongodb
  ```

### 2. **Lancer MongoDB**
Après l’installation, démarrez le service MongoDB:
- Sur macOS/Linux :
  ```bash
  sudo systemctl start mongod
  ```
- Sur Windows, MongoDB démarre généralement automatiquement, sinon lancez le "MongoDB Server" depuis les services.

### 3. **Accéder à MongoDB Shell**
Accédez à l'interface en ligne de commande de MongoDB (`mongosh`):
```bash
mongosh
```

### 4. **Créer une base de données**
Dans MongoDB, les bases de données sont créées automatiquement dès que des données y sont insérées. Vous pouvez cependant en "créer" en vous connectant à une base spécifique:
```bash
use maBaseDeDonnees
```
Cela change le contexte vers la base de données appelée `maBaseDeDonnees`. Si elle n’existe pas, elle sera créée dès que vous y insérerez des documents.

### 5. **Opérations CRUD en MongoDB**

#### **a. CREATE** (Insérer des documents)
MongoDB stocke les données sous forme de documents JSON. Pour insérer un document dans une collection:
```bash
db.maCollection.insertOne({
  nom: "Aymane",
  age: 30,
  role: "Développeur"
})
```
Ou plusieurs documents à la fois:
```bash
db.maCollection.insertMany([
  { nom: "Kalil", age: 30, role: "Manager" },
  { nom: "Mahdi", age: 22, role: "Designer" }
])
```

#### **b. READ** (Lire les documents)
Pour lire tous les documents d'une collection:
```bash
db.maCollection.find()
```
Lire un document spécifique en fonction d'une condition:
```bash
db.maCollection.find({ nom: "Aymane" })
```

#### **c. UPDATE** (Mettre à jour des documents)
Pour mettre à jour un document spécifique:
```bash
db.maCollection.updateOne(
  { nom: "Aymane" },  // Critère de sélection
  { $set: { age: 26 } }  // Nouvelle valeur
)
```
Pour mettre à jour plusieurs documents:
```bash
db.maCollection.updateMany(
  { age: { $gt: 25 } },  // Critère : âge supérieur à 25
  { $set: { role: "Senior Développeur" } }
)
```

#### **d. DELETE** (Supprimer des documents)
Pour supprimer un document:
```bash
db.maCollection.deleteOne({ nom: "Aymane" })
```
Pour supprimer plusieurs documents:
```bash
db.maCollection.deleteMany({ age: { $lt: 30 } })  // Supprimer ceux ayant moins de 30 ans
```

### 6. **Vérification des bases de données et collections**
- Liste des bases de données:
  ```bash
  show dbs
  ```
- Liste des collections dans la base de données actuelle:
  ```bash
  show collections
  ```

### 7. **Supprimer une base de données ou une collection**
- Pour supprimer une collection:
  ```bash
  db.maCollection.drop()
  ```
- Pour supprimer une base de données entière:
  ```bash
  db.dropDatabase()
  ```

## Des tâches supplémentaires pour MongoDB avec des exemples concrets.

### Tâches supplémentaires

#### 1. **Ajouter un index sur une collection**
Un index peut accélérer les recherches dans une collection. Demandez aux participants de créer un index sur un champ pour optimiser les requêtes.

**Tâche :** Créer un index sur le champ `nom` de la collection.
```bash
db.maCollection.createIndex({ nom: 1 })
```
Ensuite, faites une recherche pour observer l'amélioration des performances:
```bash
db.maCollection.find({ nom: "Aymane" }).explain("executionStats")
```

#### 2. **Utiliser des filtres complexes avec des opérateurs**
MongoDB supporte une large variété d'opérateurs de comparaison (`$gt`, `$lt`, `$in`, etc.) pour filtrer les résultats.

**Tâche :** Récupérer tous les utilisateurs dont l'âge est compris entre 20 et 30 ans.
```bash
db.maCollection.find({ age: { $gte: 20, $lte: 30 } })
```
**Tâche Bonus :** Récupérer tous les utilisateurs qui ont un rôle de "Développeur" ou de "Designer".
```bash
db.maCollection.find({ role: { $in: ["Développeur", "Designer"] } })
```

#### 3. **Mettre à jour des documents avec des opérateurs d’incrément**
L'opérateur `$inc` permet d'incrémenter une valeur numérique d'un champ.

**Tâche :** Augmenter l'âge de tous les développeurs de 1 an.
```bash
db.maCollection.updateMany({ role: "Développeur" }, { $inc: { age: 1 } })
```

#### 4. **Ajouter des sous-documents dans MongoDB**
MongoDB permet de stocker des documents imbriqués.

**Tâche :** Ajouter un champ `adresse` comme sous-document pour un utilisateur.
```bash
db.maCollection.updateOne(
  { nom: "Aymane" },
  { $set: { adresse: { ville: "Oujda", codePostal: "60000" } } }
)
```

**Tâche Bonus :** Récupérer tous les utilisateurs qui vivent dans une ville donnée.
```bash
db.maCollection.find({ "adresse.ville": "Oujda" })
```

#### 5. **Utiliser l’opérateur `$push` pour ajouter des éléments à un tableau**
MongoDB supporte les tableaux, et l’opérateur `$push` permet d’ajouter des éléments dans un champ de type tableau.

**Tâche :** Ajouter une liste de projets à un utilisateur.
```bash
db.maCollection.updateOne(
  { nom: "Aymane" },
  { $push: { projets: { nom: "Projet MongoDB", status: "En cours" } } }
)
```

#### 6. **Effectuer des recherches partielles avec des expressions régulières (regex)**
Les regex sont utiles pour effectuer des recherches textuelles plus complexes.

**Tâche :** Trouver tous les utilisateurs dont le nom commence par un "A".
```bash
db.maCollection.find({ nom: { $regex: "^A" } })
```

#### 7. **Utiliser l’agrégation pour analyser les données**
L’agrégation permet de réaliser des traitements avancés sur les données (similaire aux GROUP BY en SQL).

**Tâche :** Compter le nombre d’utilisateurs pour chaque rôle dans la collection.
```bash
db.maCollection.aggregate([
  { $group: { _id: "$role", total: { $sum: 1 } } }
])
```

#### 8. **Exporter et importer des données**
MongoDB permet d’exporter et d’importer des collections dans un fichier.

**Tâche :** Exporter une collection dans un fichier JSON.
```bash
mongoexport --db maBaseDeDonnees --collection maCollection --out collection_export.json
```

**Tâche Bonus :** Importer une collection à partir d'un fichier JSON.
```bash
mongoimport --db maBaseDeDonnees --collection nouvelleCollection --file collection_export.json
```

#### 9. **Créer une base de données avec des rôles utilisateurs et des permissions**
MongoDB permet de créer des utilisateurs avec des permissions spécifiques (lecture seule, lecture/écriture).

**Tâche :** Créer un utilisateur avec des droits limités à la lecture de la base de données.
```bash
db.createUser({
  user: "lecteur",
  pwd: "motdepasse",
  roles: [{ role: "read", db: "maBaseDeDonnees" }]
})
```

#### 10. **Backup et restauration d’une base de données**
MongoDB permet de créer des sauvegardes.

**Tâche :** Créer un backup de la base de données.
```bash
mongodump --db maBaseDeDonnees --out /path/to/backup
```

**Tâche Bonus :** Restaurer une base de données depuis un backup.
```bash
mongorestore /path/to/backup
```

### Résumé des tâches supplémentaires

1. Créer des index pour optimiser les recherches.
2. Utiliser des filtres complexes avec des opérateurs.
3. Mettre à jour des documents avec des opérateurs d'incrément.
4. Ajouter des sous-documents dans MongoDB.
5. Utiliser l’opérateur `$push` pour ajouter des éléments à un tableau.
6. Faire des recherches avec des expressions régulières.
7. Utiliser des pipelines d'agrégation pour des analyses avancées.
8. Exporter et importer des collections.
9. Gérer des utilisateurs avec des rôles et des permissions.
10. Faire un backup et restaurer une base de données.


