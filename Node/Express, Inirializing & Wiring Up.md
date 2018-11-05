# Node.js

Node.js is JavaScript run-time enviroment that executes javaScript code outside browser. Check node version using `node -v`. if absent instal node.js.

# Express.js

An unopinionated framework for node.js that helps us build APIs. Express middleware/framework also helps create an object that of the server that will be used for the CRUD operation of the endpoints. 

# Middlewares

Express also comes with  middlewares - functions that have access to the request object. A web server is a function that takes a request and outputs a response. Middlewares are executed in the middle sequentially, based on the sequence of declaration,  and help produce the final output response. Types of middlewares:

- Application-level middleware.
- Router-level middleware.
- Error-handling middleware.
- Built-in middleware.
- Third-party middleware.


```
<!-- //Server Instantiation -->
const appServ = express();

//Import(require) knexfile & Instantiate a database object using knex

const knexConfig = require('./knexfile.js');
const db = knex(knexConfig.development);

//Third party middleware
//express.json returns json objects of the response
//All global middlewares that will be used across enpoints must also be plugged into the app
//cors and helmet middlewares are not used
appServ.use(express.json(), logger('combined'), cors(), helmet());
```

# Initializing Backend Project

Add Package.json that houses general information along with dev dependencies as well as production dependencies

`yarn init`

### Add Middlewares

`yarn add express cors helmet knex logger morgan sqlite3`

### Add Nodemon to Restart(watch) the Server

`yarn add nodemom -D`

### Add Scripts Property

The below property upon adding into package.json must also be configured.

`"scripts": {
    "server": "nodemon server.js"
  }`


  # Knex

  A SQL query builder for NOde.js & browser. It connects the web application to the database.

  `yarn add knex` to install

  `knex init` to add the knexfile with below configuration:

  ```
  module.exports = {

  development: {
    client: 'sqlite3',
    connection: {
      filename: './data/lambda.sqlite3'
    },
    useNullAsDefault: true,
    migrations: {
      directory: './data/migrations'
    },
    seeds: {
      directory: './data/seeds'
  }

  
}

};
```

### Instantiating Database Object

An object of the created knexfile is used to create/instantiate an object of the database

```
const knexConfig = require('./knexfile.js');
const db = knex(knexConfig.development);
```

### Migrations 

Database migrations keep track of all the structural changes made to a database. Below CLI commands are used:

```
Knex migrate:make tableName_table
Knee migrate:latest
knex migrate:make add_finished_column
Knex migrate:rollback
```



### Seeding

Seed files are insertions of data into the table in the right order to set precedent for the sahpe of the data to be posted

```
Knex seed:make 01-cohorts
knex seed:run
```

