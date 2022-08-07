# Express REST API

1. Review: ES6 Classes
2. Using Express Routing
3. Express Routing

## Review: ES6 Classes

Classes are a template for creating objects. They encapsulate data with code to work on that data. Classes in JS are built on prototypes but also have some syntax and semantics that are not shared with ES5 class-like semantics.

### To declare a class

    class newClass {
    constructor(height, width) {
        this.height = height;
        this.width = width;
    }
    }

### Hoisting

    class newClass {}
    
    const p = new newClass();

    const p = new newClass(); 

    class newClass {}

#### Class expressions

    It is another way to define a class.

    let newClass = class {
    constructor(height, width) {
        this.height = height;
        this.width = width;
    }
    };
    console.log(newClass.name);
    // output: "newClass"

    // named
    let newClass = class newClass2 {
    constructor(height, width) {
        this.height = height;
        this.width = width;
    }
    };
    console.log(newClass.name);
    // output: "newClass2"

### Class body and method definitions

The body of a class is the part that is in curly brackets {}. This is where you define class members, such as methods or constructor.

### Constructor

The constructor method is a special method for creating and initializing an object created with a class. There can only be one special method with the name "constructor" in a class. A SyntaxError will be thrown if the class contains more than one occurrence of a constructor method.

## Using Express Routing

Routing refers to how an application’s endpoints (URIs) respond to client requests.

## Route methods

GET, POST(add), PUT(update), DELETE, ALL(for all HTTP request methods on the same path).
We can use them like: `app.get('path',handlePathFun);`.

        // GET method route
        app.get('/', (req, res) => {
        res.send('GET request homepage');
        });

        // POST method route
        app.post('/', (req, res) => {
        res.send('POST request homepage');
        });

        app.all('/secret', (req, res, next) => {
        console.log('Accessing the secret section ');
        next(); 
        });

## Express Routing

Router is like a mini-Express application.
Router doesn’t bring in views or settings but provides us with the routing APIs like:

- `.use`
- `.get`
- `.params`
- `.route`

Create a router file :

    onst express = require('express');
    const router = express.Router();

    router.use((req, res, next) => {
    console.log('Time: ', Date.now());
    next();
    });

    router.get('/', (req, res) => {
    res.send('Home Page');
    });

    router.get('/about', (req, res) => {
    res.send('About Page');
    });

    module.exports = router;

### With Express Router we can

- Use `express.Router()` multiple times to define groups of routes.
- Apply the `express.Router()` to a section of our site using `app.use()`.
- Use route middleware to process requests.
- Use route middleware to validate parameters using `.param()`.
- Use `app.route()` as a shortcut to the Router to define multiple requests on a route.

## Route parameters

Route parameters are named URL segments that are used to capture the values specified at their position in the URL.

The captured values are populated in the req.params object, with the name of the route parameter specified in the path as their respective keys.

    Route path: /users/:userId
    Request URL: <http://localhost:3000/users/90>
    req.params: { "userId": "90"}

### Route handlers

    app.get('/example/a', (req, res) => {
    res.send('Hello , User');
    });
