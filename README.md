# creating-database-using-nodejs

1. Install Dependencies
You need to install mysql or pg (for PostgreSQL) depending on the database you're using.

For MySQL:
npm install mysql2

For PostgreSQL:
npm install pg

2. Create a Database Using Node.js
   For MySQL
const mysql = require('mysql2');

const connection = mysql.createConnection({
    host: 'localhost',
    user: 'root',
    password: 'your_password'
});

connection.connect((err) => {
    if (err) throw err;
    console.log("Connected to MySQL");

    connection.query("CREATE DATABASE myDatabase", (err, result) => {
        if (err) throw err;
        console.log("Database created");
        connection.end();
    });
});


For PostgreSQL :
const { Client } = require('pg');

const client = new Client({
    user: 'your_username',
    host: 'localhost',
    password: 'your_password',
    port: 5432
});

client.connect()
    .then(() => console.log("Connected to PostgreSQL"))
    .then(() => client.query("CREATE DATABASE myDatabase"))
    .then(() => console.log("Database created"))
    .catch(err => console.error(err))
    .finally(() => client.end());


To create a database using Node.js, follow these steps:

1. Install Dependencies
You need to install mysql or pg (for PostgreSQL) depending on the database you're using.

For MySQL:

sh
Copy
Edit
npm install mysql2
For PostgreSQL:

sh
Copy
Edit
npm install pg
2. Create a Database Using Node.js
For MySQL
javascript
Copy
Edit
const mysql = require('mysql2');

const connection = mysql.createConnection({
    host: 'localhost',
    user: 'root',
    password: 'your_password'
});

connection.connect((err) => {
    if (err) throw err;
    console.log("Connected to MySQL");

    connection.query("CREATE DATABASE myDatabase", (err, result) => {
        if (err) throw err;
        console.log("Database created");
        connection.end();
    });
});
For PostgreSQL
javascript
Copy
Edit
const { Client } = require('pg');

const client = new Client({
    user: 'your_username',
    host: 'localhost',
    password: 'your_password',
    port: 5432
});

client.connect()
    .then(() => console.log("Connected to PostgreSQL"))
    .then(() => client.query("CREATE DATABASE myDatabase"))
    .then(() => console.log("Database created"))
    .catch(err => console.error(err))
    .finally(() => client.end());

    
3. Run the Script
Save the file as createDatabase.js and run:
node createDatabase.js

1. Install Dependencies
Install the MongoDB driver for Node.js:
npm install mongodb


2. Create a MongoDB Database Using Node.js
Create a file createDatabase.js and add the following code:

const { MongoClient } = require("mongodb");

// Connection URL
const url = "mongodb://localhost:27017"; // Replace with your MongoDB URL
const client = new MongoClient(url);

async function createDatabase() {
    try {
        await client.connect();
        console.log("Connected to MongoDB");

        const db = client.db("myDatabase"); // This creates the database if it doesn't exist
        console.log(`Database "${db.databaseName}" created`);

    } catch (err) {
        console.error("Error:", err);
    } finally {
        await client.close();
    }
}

createDatabase();

3. Run the Script :

  node createDatabase.js
