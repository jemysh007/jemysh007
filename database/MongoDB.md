# MongoDB Cheatsheet

This cheatsheet is a comprehensive guide to the most important MongoDB commands and operations. It covers basic queries, CRUD operations, indexing, aggregation, and more advanced concepts.

## Table of Contents

1. [MongoDB Basics](#mongodb-basics)
2. [CRUD Operations](#crud-operations)
3. [Querying Documents](#querying-documents)
4. [Updating Documents](#updating-documents)
5. [Deleting Documents](#deleting-documents)
6. [Indexes](#indexes)
7. [Aggregation](#aggregation)
8. [Data Modeling](#data-modeling)
9. [Replication](#replication)
10. [Sharding](#sharding)
11. [Transactions](#transactions)
12. [Security](#security)
13. [Best Practices](#best-practices)

---

## 1. **MongoDB Basics**

### Connecting to MongoDB

```shell
mongo --host <hostname> --port <port> -u <username> -p <password> --authenticationDatabase <authDB>
```

### Show Databases

```javascript
show dbs;
```

### Use a Database

```javascript
use myDatabase;
```

### Show Collections

```javascript
show collections;
```

---

## 2. **CRUD Operations**

### Create a Collection

```javascript
db.createCollection("myCollection");
```

### Insert Documents

```javascript
db.myCollection.insertOne({ name: "John", age: 30 });
db.myCollection.insertMany([{ name: "Jane", age: 25 }, { name: "Doe", age: 22 }]);
```

### Read Documents

```javascript
db.myCollection.find();
db.myCollection.find({ name: "John" });
```

### Update Documents

```javascript
db.myCollection.updateOne({ name: "John" }, { $set: { age: 31 } });
db.myCollection.updateMany({ age: { $lt: 30 } }, { $set: { status: "young" } });
```

### Delete Documents

```javascript
db.myCollection.deleteOne({ name: "John" });
db.myCollection.deleteMany({ age: { $lt: 25 } });
```

---

## 3. **Querying Documents**

### Basic Queries

```javascript
db.myCollection.find({ name: "John" });
db.myCollection.find({ age: { $gt: 25 } });
```

### Projection

```javascript
db.myCollection.find({}, { name: 1, age: 1 });
```

### Sorting

```javascript
db.myCollection.find().sort({ age: -1 });
```

### Limiting and Skipping

```javascript
db.myCollection.find().limit(5);
db.myCollection.find().skip(5).limit(5);
```

---

## 4. **Updating Documents**

### Update Operators

- **$set**: Sets the value of a field

```javascript
db.myCollection.updateOne({ name: "John" }, { $set: { age: 31 } });
```

- **$unset**: Removes a field

```javascript
db.myCollection.updateOne({ name: "John" }, { $unset: { age: "" } });
```

- **$inc**: Increments the value of a field

```javascript
db.myCollection.updateOne({ name: "John" }, { $inc: { age: 1 } });
```

- **$push**: Adds an item to an array

```javascript
db.myCollection.updateOne({ name: "John" }, { $push: { hobbies: "reading" } });
```

---

## 5. **Deleting Documents**

### Delete Operators

- **deleteOne**: Deletes a single document

```javascript
db.myCollection.deleteOne({ name: "John" });
```

- **deleteMany**: Deletes multiple documents

```javascript
db.myCollection.deleteMany({ age: { $lt: 25 } });
```

---

## 6. **Indexes**

### Creating Indexes

```javascript
db.myCollection.createIndex({ name: 1 });
```

### Viewing Indexes

```javascript
db.myCollection.getIndexes();
```

### Dropping Indexes

```javascript
db.myCollection.dropIndex("name_1");
```

---

## 7. **Aggregation**

### Basic Aggregation

```javascript
db.myCollection.aggregate([
    { $match: { status: "active" } },
    { $group: { _id: "$age", total: { $sum: 1 } } }
]);
```

### Common Aggregation Stages

- **$match**: Filters documents

```javascript
{ $match: { status: "active" } }
```

- **$group**: Groups documents by a specified field

```javascript
{ $group: { _id: "$age", total: { $sum: 1 } } }
```

- **$sort**: Sorts documents

```javascript
{ $sort: { total: -1 } }
```

- **$project**: Reshapes documents

```javascript
{ $project: { name: 1, age: 1 } }
```

---

## 8. **Data Modeling**

### Embedding Documents

```javascript
let post = {
    title: "Post Title",
    content: "Post Content",
    comments: [
        { user: "John", comment: "Great post!" },
        { user: "Jane", comment: "Thanks for sharing!" }
    ]
};
```

### Referencing Documents

```javascript
let user = { name: "John" };
let post = { title: "Post Title", content: "Post Content", userId: user._id };
```

---

## 9. **Replication**

### Setting Up a Replica Set

```javascript
rs.initiate();
rs.add("mongodb1.example.net:27017");
rs.add("mongodb2.example.net:27017");
rs.add("mongodb3.example.net:27017");
```

### Checking Replica Set Status

```javascript
rs.status();
```

---

## 10. **Sharding**

### Enabling Sharding

```javascript
sh.enableSharding("myDatabase");
```

### Sharding a Collection

```javascript
sh.shardCollection("myDatabase.myCollection", { shardKey: 1 });
```

---

## 11. **Transactions**

### Starting a Transaction

```javascript
const session = db.getMongo().startSession();
session.startTransaction();
```

### Committing a Transaction

```javascript
session.commitTransaction();
session.endSession();
```

### Aborting a Transaction

```javascript
session.abortTransaction();
session.endSession();
```

---

## 12. **Security**

### Creating a User

```javascript
db.createUser({
    user: "myUser",
    pwd: "myPassword",
    roles: [{ role: "readWrite", db: "myDatabase" }]
});
```

### Authenticating a User

```javascript
db.auth("myUser", "myPassword");
```

---

## 13. **Best Practices**

- **Use Indexes**: Ensure that your queries are efficient by using indexes.
- **Data Modeling**: Choose the right data model (embedding vs. referencing) based on your use case.
- **Backup Regularly**: Regularly backup your data to prevent data loss.
- **Monitor Performance**: Use monitoring tools to keep an eye on the performance of your MongoDB instance.
- **Secure Your Database**: Implement proper authentication and authorization mechanisms.

---

## Conclusion

This MongoDB cheatsheet summarizes key concepts, commands, and operations for working with MongoDB. Keep this as a quick reference while you're working with MongoDB!
