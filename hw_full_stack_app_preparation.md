# Homework: Full Stack Games Hub App

### Learning Objectives

- Understand the relationship between client, server and database
- Be able to navigate a codebase that you haven't written

## Brief

Your boss has asked to you look over the codebase of a full-stack JavaScript application. The front-end is written in JavaScript using React, the back-end uses an Express server and a MongoDB database. Your task is to make yourself familiar with the codebase.

The application includes a README.md with instructions on running the application.

![Overview of the tech stack and tooling with commands](images/tech_stack_with_commands.png)

*Overview of the tech stack and tooling with commands*

*EDIT: Frontend is now written in React with the command to run `npm start`*

## MVP

### Task

Draw a diagram showing the dataflow through the application starting with a form submission, ending with the re-rendering of the page. This will involve a multi-direction data-flow with the client posting data to the server and the server sending data back to the client with the response. Detail the client, server and database in the diagram and include the names of the files involved in the process.

### Questions

1. What is responsible for defining the routes of the `games` resource?
A: The routes are defined on the client side where they are then mapped to the controller (server) CRUD actions. 

2. What do you notice about the folder structure?  Whats the client responsible for? Whats the server responsible for?
A: There is a services folder within the client which contains the code needed to speak with the server. The client is displaying the information while the server handles the speaking to the database and passing this information between the two, the Controller in MVC.

3. What are the the responsibilities of server.js?
A: Server js takes the data from the front end and routes it to the database with the help of create_router.js

4. What are the responsibilities of the `gamesRouter`?
A: gamesRouter is a method which takes in the database (gamesCollection) and the RESTful routes (createRouter) from create_router and passes the data to and from the db. 

5. What process does the the client (front-end) use to communicate with the server?
A: The GamesService.js file which fetches the data from the URL and posts updates the to db through the server. 

6. What optional second argument does the `fetch` method take? And what is it used for in this application? Hint: See [Using Fetch](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch) on the MDN docs
A: init, this allows modification of a bunch of different settings through the fetch request. E.g. changing from default GET method to a POST method.

7. Which of the games API routes does the front-end application consume (i.e. make requests to)?
A: /api/games

8. What are we using the [MongoDB Driver](http://mongodb.github.io/node-mongodb-native/) for?
A: The driver enables us to talk to the Mongo database and create/modify and delete entries in the database from the front end using the RESTful routes. 


## Extension

Why do we need to use [`ObjectId`](https://mongodb.github.io/node-mongodb-native/api-bson-generated/objectid.html) from the MongoDB driver?
A: As it is non relational, there needs to be a way to determine different documents in the database from each other. The 24 character ObjectId provides this functionality. A simple counter like in SQL would not make sense as documents can be entirely different so would not match the table-like format of an SQL DB. 


Add to your diagram the dataflow for removing a game.
