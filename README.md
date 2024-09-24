# MongoDb_workshop

Voici un tutoriel pratique sur MongoDB avec des commandes pour créer une base de données et effectuer des opérations CRUD (Create, Read, Update, Delete).

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
