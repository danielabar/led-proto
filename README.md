led-proto
=========

The purpose of this project is to investigate how to implement Authentication and Authorization in a SPA using Angular js.
This solution is based on [angular-client-side-auth](https://github.com/fnakstad/angular-client-side-auth), 
with the big difference that jade templating is not used here. Instead, the views are just regular html with Angular directives.
The steps below explained what was changed to make this work.

* Added to [package.json](package.json)

    ```
    "dependencies": {
        ...
        "ejs": "*",
        ...
    }
    ```

* Added to [server.js](server.js)

    ```
    app.engine('html', require('jade').renderFile);
    app.engine('html', require('ejs').renderFile);
    app.set("view options", {layout: false});
    ```

* Modified [routes.js](server/routes.js) path matching

    ```
    path: '/partials/*',
    httpMethod: 'GET',    
    ...
        var requestedView = req.url.slice(1, req.url.length) + '.html';
        res.render(requestedView);
    ```

    ```
    path: '/*',
    httpMethod: 'GET',    
    ...
        res.render('index.html');
    ```

### Setup Instructions

* If you don't already have it, install [Node.js](http://nodejs.org/)
* Clone this repo and cd to project directory, then run

    ```
    npm install
    ```
* From project root directory, run

    ```
    node server.js
    ```

* Browse to [http://localhost:8000](http://localhost:8000)

* Login using one of the predefined users

    ```
    user@test.com/123
    admin@test.com/456
    ```

* Logout from dropdown menu under avatar image    

* Register a new user

    * Name can be anything (not used yet)
    * Surname can be anything (not used yet)
    * Email is used as the username, enter a valid format (eg: user1@test.com)
    * Password must be at least 5 characters
    * Retype password can be anything (not used yet)
    * Check or uncheck terms & conditions (not used yet)

* Register with server side validation error

    * Follow instructions as for registering a new user, but enter a password with less than 5 characters    

### IMPORTANT

This is a mock solution with no datastore backing it. The predefined users are hard-coded in [Users.js](models/User.js).
When new users are added via registration, they are 'persisted' in server memory by adding to the list of predefined users.
The passwords are stored in plain text. When the server is restarted, all the registered users are gone. 
A real solution would require a datastore to persist user information and a mechanism to hash the passwords.