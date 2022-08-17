# Twitter Clone

# DEV PROGRESS

...... Set up Firebase project and an app. 

## 1. Install Firebase
```
npm install --save firebase
```

## 2. Copy the config file and paste into my React project.
a. create a file called "firebase.js"
PATH: src/firebase.js
b. import
```js
// Import the functions you need from the SDKs you need
import { initializeApp } from "firebase/app";
// TODO: Add SDKs for Firebase products that you want to use
// https://firebase.google.com/docs/web/setup#available-libraries

// Your web app's Firebase configuration
const firebaseConfig = {
  apiKey: "AIzaSyCMl1xmtrC5gHn5qxAuLZq2ZlURBGYfslo",
  authDomain: "nc-twitter-clone-cec91.firebaseapp.com",
  projectId: "nc-twitter-clone-cec91",
  storageBucket: "nc-twitter-clone-cec91.appspot.com",
  messagingSenderId: "840751435243",
  appId: "1:840751435243:web:21205fab9baa14ec915dae"
};

// Initialize Firebase
const app = initializeApp(firebaseConfig);
```
c. import it into your index.js
```js
import firebaseApp from "./firebase";
console.log(firebase);
// confirm by console logging the Firebase App.
```
d. confirm 


## 3. Create .env to hide keys

.env
```
REACT_APP_API_KEY: <apiKey>,
REACT_APP_AUTH_DOMAIN: <>,
REACT_APP_PROJECT_ID: <>,
REACT_APP_STORAGE_BUCKET: <>,
REACT_APP_MESSAGING_SENDER_ID: <>,
REACT_APP_APP_ID: <>
```

- Put the keys inside the .env folder where there are <>.

*Why do that?*
- It is critical vulnerability to reveal your keys to others in the public. 
- However, when you build an application and you convert into a normal javascript, it will reveal data to the users after importing from .env file. THIS IS NOT A GOOD SECURITY.L

- After you finish creating this .env file, test whether the app gets initialized or not. 

## 4. Router Setup

a. Create new folders called routes and conponents.
b. Create routes in the routes folder. 

Expected Pages:
1. Authentication
2. After logged in > Home
3. Profile
4. Edit Profile. 


c. Install React-Router-Dom
```
npm i react-router-dom
```
d. Create a router.
*Routers are compoennts*

## 5. Use Firebse Auth

- Relative import: ../
- To avoid relative import, you use absolute import. 
*How do you create an absolute import?*
Steps:
1. Create jsconfig.json
2. Add below code in jsconfig.json
```js
{
  "compilerOptions": {
    "baseUrl": "src"
  },
  "include": ["src"]
}
```

- Create AppRouter in Apps.js
Overall Flow: App > AppRouter > Route to diferrent page such as <Home> <Auth /> etc

Steps:
```js
import React, { useState } from "react";
import AppRouter from "components/Router";
import { authService } from "fbase";

function App() {
  const [isLoggedIn, setIsLoggedIn] = useState(authService.currentUser);
  return (
    <>
      <AppRouter isLoggedIn={isLoggedIn} />
      <footer>&copy; {new Date().getFullYear()} Nwitter</footer>
    </>
  );
}

export default App;
```
