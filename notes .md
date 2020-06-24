 # Git Workflow
    - master/develop main branches
    - master branch always represents production ready code base
    - create new feature/update branches off develop branch
    - merge develop branch into master 
    - pull origin branch before you push


# Databases

Types of Database
1. Relational Databases
 - links data in table and rows (e.g. SQL)
2. Non Relational Database
 - represents data as collection of ddocuments wwithout any table or rows (e.g. MongoDB)

Interacting with a Database
1. Database Query Langugage(e.g SQL)
2. Object Data Model
    - represents website's data as a javascript object (JSON)

## MongoDB

- Non relational database system
- has database as service called Atlas and a GUI called Compass
- Object Data Model

## Mongoose

- JS module that lets us interact with MongoDB database and construct document objects
- defines schema, the blueprint for the model constructor. A schema defines the possible fields, types and references in a model. 
```
        //Requires Mongoose
        const mongoose = require("mongoose");

        //Creates variables to store Schema
        const Schema = mongoose.Schema;

        //Creates comment schema
        const commentSchema = Schema({
            userID: { type: Schema.Types.ObjectId, ref: "User" },
            username: { type: Schema.Types.ObjectId, ref: "User" },
            text: {type: String, required: true},
            date: { type: Date, default: Date.now(), required: true},
            channel: {type: String, required: true}
        });
```
- defines and exports model, which is a constructor for the document object
```
        //Creates comment model to construct documents for our database
        const Comment = mongoose.model("Comment", commentSchema);

        //Exports model
        module.exports = Comment;
```
- Documents are instances of a model, these are stored in DB collection
- Documents are in JSON format

# Web Framework
- handles the server side logic of an application

## Express
- JS web framework to handle http requests and responses
- Express routes determine how the application (backend) will respond to client (browser) requests to particular endpoint
 - define routes using express app `Object` methods that correspond to http requests (e.g, GET, POST)
 - Route paths, in combination with a request method, define the endpoints at which requests can be made.  
```
        // respond with "hello world" when a GET request is made to the homepage
        app.get('/', function (req, res) {
            res.send('hello world')
        }) 
```         
```
        //This route path will match requests to /about and respond with "about".
        app.get('/about', function (req, res) {
            res.send('about')
        })
```
- Express is a series of routes and middleware
    - middleware are functions called within a route that have access to request and response objects
    - in the above examples `res.send()` is the middleware

# Socket.io

- utilizes web sockets to create a live/persistent connections between client/server
- allows for real time communication between client/server

```
<!--insert socket.io script client side through the browser (index.html)-->       
<script src="http://localhost:8000/socket.io/socket.io.js"></script>
<script>
  var socket = io('http://localhost:8000');

  socket.on('connect', () => {
  socket.emit('message', ' hello world');
  return;
});

socket.on('disconnect', () => {
  socket.emit('bye', ' goodbye, world');
  return
});
</script>
```

# Traditional Web Apps

- client (browser) requests html/css/js from server
- Server responds to client with the files, either as:
    - static files sitting on the server
    - or dynamically built in the server application  (the server logic would create the html)
- client renders the html/css and immediately runs any js
- if new data is requested, entire page would be re-sent or the server would redirect to a new page

# Single Page Apps

- these modern web applications don't fetch pages separately from the server
- instead they are comprised of a single html page from the server
- the SPA uses js to modify the DOM when new data is received
    - the entire page does not reload, the DOM tree is simply updated on the browser

# LAMP Stack

# MERN Stack

# JAM Stack

# React

# Testing

# TypeScript

