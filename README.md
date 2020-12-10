# Getting Started with Create React App

This project was bootstrapped with [Create React App](https://github.com/facebook/create-react-app).

# Project goals:

## to check if it is possible to prevent the access to the JWT token if the Front-End is exposed to an XSS attack.

PRE-REQUISITES:
- 1- npm start the project
- 2- lauch the server.js by running #node server.js
- 3- launch the malicious-server.js by running #node malicious-server.js

The app has 3 buttons that performs 3 distinct actions:

### button 1 : Get Token 

This will trigger an http get request to get the token generated by server.js and it will store this token inside localStorage,
sessionStorage and inside a simple cookie. Furthermore It will also generate from the server.js an httpOnly cookie with the JWT token.

### button 2 : Expose Cliente

This will retrieve the information of the localStorage,sessionStorage and cookies available in the Front-End. This action can be performed by an XSS attack.

### button 3 : Send Token

This will retrieve the information of the localStorage,sessionStorage, and cookies available in the Front-End and it will also send this information to a malicious server in order to do whatever we want with it. By sending this information to the malicious server, we are able to retrieve also the cookies which had the flag httpOnly. This action can also be performed by an XSS attack.

**To sum up, this demonstrates that if the Front-End is susceptible to XSS attacks, no matter what you choose (localStorage, sessionStorage, or even Cookies with httpOnly flag) to store the JWT, it can be retrieved by the attacker.
Leaving the only possibility to execute the http requests to our own server.js from the Front-End and making the authorization using JWT only from the Back-End. To do so, we have to mirror the http requests from the Front-End in the Back-End using it just as an interface that can perform requests with JWT tokens without exposing it.**


## Available Scripts

In the project directory, you can run:

### `npm start`

Runs the app in the development mode.\
Open [http://localhost:3001](http://localhost:3001) to view it in the browser.

The page will reload if you make edits.\
You will also see any lint errors in the console.
