# Read Me File

# noSQL vs SQL

## Data Modeling – Table Relationships

![Data Modeling – Table Relationships](https://www.essentialsql.com/wp-content/uploads/2014/06/DataModel-Relations1.png)

## The differences between noSQL and SQL databases

    noSQL :
    - non-relational
    - have dynamic schemas for unstructured data
    - horizontally scalable
    - document, key-value, graph or wide-column stores
    - better for unstructured data like documents or JSON
    - databases are document based
    - databases are horizontally scalable
    - NoSQL databases are not good fit for complex queries

##

    SQL :
    - relational 
    - structured query language and have a predefined schema
    - vertically scalable 
    - table based 
    - better for multi-row transactions 
    - databases are table based databases
    - databases are vertically scalable 
    - For complex queries: SQL databases are good fit for the complex query intensive environment

## What kind of data is a good fit for an SQL database?

     if your data is highly structured and associations among the program entities are clearly defined (for instance, if you are developing a point of sale system where you need to store customer orders and product records), conventional SQL based databases are the best fit

## Give a real world example

    MySQL Community Edition

    MySQL database is very popular open-source database. It is generally been stacked with apache and PHP, although it can be also stacked with nginx and server side JavaScripting using Node js

## What kind of data is a good fit a NoSQL database?

    to work better on both unstructured and unrelated data. The better solutions are the crossover databases that have elements of both NoSQL and SQL. RDBMS that use SQL are schema–oriented which means the structure of the data should be known in advance to ensure that the data adheres to the schema

## Database Examples

### SQL Database Examples

    - MySQL Community Edition
    - MS-SQL Server Express Edition
    - Oracle Express Edition

### NoSQL Database Examples

    - MongoDB
    - CouchDB
    - Redis

### MongoDB

    Mongodb is one of the most popular document based NoSQL database as it stores data in JSON like documents. It is non-relational database with dynamic schema. It has been developed by the founders of DoubleClick, written in C++ and is currently being used by some big companies like The New York Times, Craigslist, MTV Networks

## Best database for hierarchical data storage?

    Document based database like MongoDB, and Redis are great for small scale, hierarchical data with a relatively small amount of children for each entry

## Which type of database is best for scalability?

    in general, NoSQL/DDBMS will scale easier than RDBMS. In particular,DB is the most scalable and one of the most performant NoSQL database that I currently know of, especially with respect to active/active regional DC replication

##

    First of all, MySQL, MSSQL, Oracle, PostgreSQL, all are highly scalable, it's just that they require little maintenance for it. All SQL based databases are very stable, and are in production since years

## What is a schema?

    The term “schema” refers to the organization of data as a blueprint of how the database is constructed (divided into database tables in the case of relational databases). The formal definition of a database schema is a set of formulas (sentences) called integrity constraints imposed on a database

## Sequelize

    Sequelize is a promise-based Node.js ORM tool for Postgres, MySQL, MariaDB, SQLite, Microsoft SQL Server, Amazon Redshift and Snowflake’s Data Cloud. It features solid transaction support, relations, eager and lazy loading, read replication and more.

    Sequelize follows Semantic Versioning and supports Node v10 and above.

## Sequelize example

    const { Sequelize, Model, DataTypes } = require('sequelize');
    const sequelize = new Sequelize('sqlite::memory:');

    class User extends Model {}
    User.init({
    username: DataTypes.STRING,
    birthday: DataTypes.DATE
    }, { sequelize, modelName: 'user' });

    (async () => {
    await sequelize.sync();
    const jane = await User.create({
        username: 'janedoe',
        birthday: new Date(1980, 6, 20)
    });
    console.log(jane.toJSON());
    })();

## Things I want to know more about

    Learn more about MongoDB.

    Learn more about nosql vs sql.
