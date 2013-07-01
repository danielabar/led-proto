led-proto
=========

The purpose of this project is to investigate how to implement Authentication and Authorization in a SPA using Angular js.
This solution is based on [angular-client-side-auth](https://github.com/fnakstad/angular-client-side-auth), 
with the big difference that jade templating is not used here. Instead, the views are just regular html with Angular directives.

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

* Login using top nav form (registration form not working yet)

    ```
    user@test.com/123
    admin@test.com/456
    ```

* Logout from dropdown menu under avatar image    