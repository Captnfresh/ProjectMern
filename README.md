# ProjectMern
Web Stack using MERN (MongoDB, ExpressJS, ReactJS, NodeJS)


## In this project, I will be implementing a web deployment model based on MERN stack in AWS Cloud.

MERN Web stack consists of following components:

1. Mongodb: A document-based, No-SQL database used to store application data in a form of documents.
2. Expressjs: A server side Web Application framework for Node.js.
3. Reactjs: A frontend framework developed by Facebook. It is based on JavaScript, used to build User Interface (UI) components.
4. Node.js: A JavaScript runtime environment. It is used to run JavaScript on a machine rather than in a browser.

## What types of Database Management Systems (DBMS) exist and what each type is more suitable for.

1. Relational DBMS (RDBMS): Data is stored in structured tables (rows and columns) with defined relationships between tables. It uses SQL for querying and manipulating data.
Examples: MySQL, PostgreSQL, Microsoft SQL Server, Oracle.

2. NoSQL DBMS: Non-relational databases that store unstructured or semi-structured data. They are designed to handle large-scale data and distributed systems.
Examples: Document-based: MongoDB, Couchbase.
Key-value: Redis, DynamoDB.
Column-family: Cassandra, HBase.
Graph: Neo4j, ArangoDB.

3. Graph DBMS: Specifically designed to represent and store data in graphs
Examples: Neo4j, Amazon Neptune, OrientDB.

4. Time-series DBMS: Specializes in storing and managing time-series data.
Examples: InfluxDB, TimescaleDB, Prometheus.

5. Distributed DBMS: A database system spread across multiple locations, with data distributed across different nodes in a network. It allows for high availability, fault tolerance, and scalability.
Examples: Google Spanner, Apache Cassandra, CockroachDB.

## Concept of Web Application Frameworks. Get to know what server-side (backend) and client-side (forntend) frameworks exist and what they are used for:

Web Application Frameworks are tools or software libraries that provide a structured way to develop web applications. They streamline the development process by offering pre-built modules and components for common tasks such as routing, database access, authentication, and more. Web application frameworks can be classified into two major categories:

1. Server-Side (Backend) Frameworks:-
Server-side frameworks are responsible for handling the business logic, database interactions, server communication, and routing requests from the client to the server. They generate HTML dynamically and respond to requests from client-side applications.

Common Server-Side Frameworks:
Node.js with Express.js (JavaScript)
Django (Python)
Flask (Python)
Ruby on Rails (Ruby)
Laravel (PHP)
ASP.NET Core (C#)
Spring Boot (Java)

2. Client-Side (Frontend) Frameworks:-
Client-side frameworks (also called frontend frameworks) manage the part of the application that the user interacts with directly. These frameworks primarily handle the layout, UI/UX, and interactivity of the application.

Common Client-Side Frameworks:
React.js (JavaScript)
Vue.js (JavaScript)
Angular (TypeScript/JavaScript)
Svelte (JavaScript)
Ember.js (JavaScript)

## What RESTful API is and what it is used for in Web development:-
RESTful APIs are widely used in web development to allow communication between clients (such as web or mobile applications) and servers. They are popular due to their simplicity, flexibility, and ability to handle a wide range of use cases—from fetching data to handling complex interactions in modern web applications.

Key Concepts of RESTful API:

Client-Server Architecture: A RESTful API is based on a client-server architecture, where the client (usually a browser or mobile app) sends requests to the server, which processes the request and returns the response.
Stateless: REST APIs are stateless, meaning each request from the client to the server must contain all the information the server needs to understand and process the request.
Resources: In REST, everything is considered a resource, such as a user, product, blog post, or any other object in a system. Each resource is identified by a URI.
HTTP Methods: RESTful APIs use standard HTTP methods to perform actions on resouces like GET, PUT, POST, DELETE.
Caching: RESTful APIs can be designed to allow caching of responses, which helps reduce server load and improve performance by storing copies of responses on the client.
Stateless Communication: The communication between the client and the server in a RESTful API is stateless, meaning each request is independent.



Here’s a step-by-step guide on how to set up a LAMP stack (Linux, Apache, MySQL, PHP) on an AWS EC2 t2.micro instance with Ubuntu 24.04 LTS for a DevOps project.


## Prerequisites

1. Install Windows Terminal
2. Open an AWS account and provision an Ubuntu server
3. SSH key pair for EC2 instance

   
## Step 1 - Get your instance up and running

1. Sign up to AWS console following this [instruction](https://console.aws.amazon.com/).
2. After successfully signing up, launch a new instance.
3. Select a region close to you and launch an instance of t2.micro family with Linux ubuntu server.
4. Create a new .pem priavte key(If you don't have one already) and save it securely.

  image 1
   
5. Configure your security groups by ensuring that the following ports are allowed:

   SSH (port 22) – for remote access
   
   HTTP (port 80) – for web traffic

   image 2


## Step 2 - Connect to the ec2 instance via ssh
      
1. Open your Windows terminal tool and navigate to your downloads directory

   `cd downloads`

2. Connect to the instance by running
   
   `ssh -i your-key.pem ubuntu@(your-ec2-public-ip)`

 
Now, you're connected to your ec2 instance via ssh    

   image 3


## Step 3 - Backend Configuration

1. Update Ubuntu

   `sudo apt update`

2. Upgrade ubuntu

   `sudo apt upgrade`

3. Get the location of NodeJS software from Ubuntu repositories.

   `curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -`

4. Install NodeJS on the server

   `sudo apt-get install -y nodejs`

5. Verify the node version

   `node -v`


   `npm -v`

   image 4

6. Setup Application code by creating a new directory for your new project. In this case, we will be using "Todo" as  the name of the directory

   `mkdir Todo`

    `cd Todo`

   
7. Initialize the project so that a new file *package.json* will be created. This file will normally contain information about application and the dependencies that it needs to run:

   `npm init`

   image 5


## Step 4 - Install ExpressJS

1. To use express, install using npm

   `npm install express`

2. Create a new file *index.js*

   `touch index.js`

3. Install dotenv module:

   `npm install dotenv`

 4. Open the index.js and copy the following in the file

    `nano index.js`



    ```
        const express = require('express');
        require('dotenv').config();
        const app = express();
        const port = process.env.PORT || 5000;
        
        app.use((req, res, next) => {
            res.header("Access-Control-Allow-Origin", "*");
            res.header("Access-Control-Allow-Headers", "Origin, X-Requested-With, Content-Type, Accept");
            next();
        });
        
        app.use((req, res, next) => {
            res.send('Welcome to Express');
        });
        
        app.listen(port, () => {
            console.log(`Server running on port ${port}`);
        });
    ```

    Use Ctrl + X, Y, Enter to exit nano editor

5. Start the server to see if it works

   `node index.js`

   image 6

6. Navigate to your ec2 security group and edit inbound security group access. Allow TCP Custom network on Port 5000 from anywhere

   image 7



   You can view the latest web page from your local browser using http://(your public ip address):5000


   image 8

7. Creating Route: There are three actions that our To-Do application needs to be able to do:

   Create a new task
   Display list of all tasks
   Delete a completed task
   Each task will be associated with some particular endpoint and will use different standard HTTP request methods: POST, GET, DELETE.
  
   For each task, we need to create routes

   `mkdir routes`

   `cd routes`

8. Create an *api.js* file while still in the same directory and copy the following code in it.

   `touch api.js`   

   ```
      const express = require('express');
      const router = express.Router();
      
      router.get('/todos', (req, res, next) => {});
      
      router.post('/todos', (req, res, next) => {});
      
      router.delete('/todos/:id', (req, res, next) => {});
      
      module.exports = router;
   ```

   
## Step 5 - Creating the models

1. Navigate to the Todo directory and install mongoose:


   `cd ..`


   `npm install mongoose`

   
3. Create a new folder "models" and inside it, create a todo.js folder and copy the following code into the nano editor

   `mkdir models && cd models && touch todo.js && nano todo.js`


   ```
      const mongoose = require('mongoose');
      const Schema = mongoose.Schema;
      
      // create schema for todo
      const TodoSchema = new Schema({
          action: {
              type: String,
              required: [true, 'The todo text field is required']
          }
      });
      
      // create model for todo
      const Todo = mongoose.model('todo', TodoSchema);
      
      module.exports = Todo;

   ```


4. Navigate back to routes directory and update the api.js file to make use of the new models

   `cd ..`

   `cd routes`

   ```
      const express = require('express');
      const router = express.Router();
      const Todo = require('../models/todo');
      
      router.get('/todos', (req, res, next) => {
          //this will return all the data, exposing only the id and action field to the client
          Todo.find({}, 'action').then(data => res.json(data)).catch(next);
      });
      
      router.post('/todos', (req, res, next) => {
          if (req.body.action) {
              Todo.create(req.body).then(data => res.json(data)).catch(next);
          } else {
              res.json({ error: "The input field is empty" });
          }
      });
      
      router.delete('/todos/:id', (req, res, next) => {
          Todo.findOneAndDelete({ "_id": req.params.id }).then(data => res.json(data)).catch(next);
      });
      
      module.exports = router;

   ```

   image 9


## Step 6 - Configure MongoDB database

1. Navigate to mlabs to create a MongoDB database and collection there.

   image 10

   image 11

   image 12


2. Navigate to your Todo directory and create a .env file

   `cd ..`

   `touch .env && nano .env`

3. Now paste your connection string and paste it in your .env file in this format:

   `DB = 'mongodb+srv://<db_username>:<db_password>@cluster0.hxbqi.mongodb.net/?retryWrites=true&w=majority&appName=Cluster0'`

   Where db_username and db_password is your username and password.

4. Update index.js with the following code

   ```
      const express = require('express');
      const bodyParser = require('body-parser');
      const mongoose = require('mongoose');
      const routes = require('./routes/api');
      const path = require('path');
      require('dotenv').config();
      
      const app = express();
      const port = process.env.PORT || 5000;
      
      // connect to the database
      mongoose.connect(process.env.DB, { useNewUrlParser: true, useUnifiedTopology: true })
          .then(() => console.log(`Database connected successfully`))
          .catch(err => console.log(err));
      
      // since mongoose promise is deprecated, we override it with node's promise
      mongoose.Promise = global.Promise;
      
      app.use((req, res, next) => {
          res.header("Access-Control-Allow-Origin", "*");
          res.header("Access-Control-Allow-Headers", "Origin, X-Requested-With, Content-Type, Accept");
          next();
      });
      
      app.use(bodyParser.json());
      app.use('/api', routes);
      app.use((err, req, res, next) => {
          console.log(err);
          next();
      });
      
      app.listen(port, () => {
          console.log(`Server running on port ${port}`);
      });

   ```


5. Start your server:

   `node index.js`


   image 13



## Step 7 - Frontend creation

Since we are done with the functionality we want from our backend and API, it is time to create a user interface for a Web client (browser) to interact with the application via API. To start out with the frontend of the To-do app, we will use the create-react-app command to scaffold our app.

1. In the same root directory as your backend code, which is the Todo directory, run:

   `npx create-react app client`

2. Before testing the react app, there are some dependencies that needs to be installed:

   `npm install concurrently --save-dev`

   It is used to run more than one command simultaneously from the same terminal window

   `npm install nodemon --save-dev`

   It is used to run and monitor the server

3. In Todo folder open the package.json file. Change the part replace with the code below.

   ```   
      "scripts": {
        "start": "node index.js",
        "start-watch": "nodemon index.js",
        "dev": "concurrently \"npm run start-watch\" \"cd client && npm start\""
      }
    ```     

4. 















































