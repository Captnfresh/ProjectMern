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
