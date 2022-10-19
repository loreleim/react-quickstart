# Quickstarts for a Vanilla project

## Creating a new react.js project

```
npx/npm create-react-app my-app
cd my-app
```
SCSS Management 2021: 
```
npm install --save-dev sass
```
[Source](https://medium.com/nerd-for-tech/add-sass-to-your-react-app-in-2021-here-is-how-c7260c323a5a)
Page Routing:
```
npm install react-router-dom
```
Firebase Data:
```
npm install --save firebase
```
Reading ENV files:
```
npm install --save-dev dotenv
```
GSAP Animations:
```
npm install gsap
```
SEO Optimization
```
npm i react-helmet
```
Play Sound in Browser
```
npm install --save react-howler
```
To initialize Github Pages:
```
npm install gh-pages --save-dev
```
To initialize Github Pages in package.json: 
```
"homepage": "http://yourname.github.io/my-app"
"scripts": {
//...
"predeploy": "npm run build",
"deploy": "gh-pages -d build"
}
```
Then in terminal run 
```
git init
git remote add origin https://loreleim.github.io/rentalcar/.git
npm run deploy

```
```
git add .
git commit -m “Your commit message”
git push origin master
```
A note on updating Github Pages: When you are ready to merge from your develop branch, do this in develop branch: 
```
npm run deploy
```
Then go to your master branch, and merge the changes from dev into master.
You should see the edits in your github.io

After everything is installed, go ahead and run the project to see live edits! Make sure to do this in a develop branch
```
npm run start
```

## Organization and Structure

Within the src folder please create the following folders:

1. components (place your reusable code here)
2. images (.svg, .jpg, or storage .ai files)
3. pages (index.js shall house your router)
4. style (contains .scss files, index.scss shall be the main stylesheet)
5. database

Remove the following default files:

1. setupTests
2. logo.svg (remove the import on the App.js file, and the html reference in the render <img> tag)
3. App.test.js
4. the .css default files

Edit the public > index.html > <title> and <meta description content="">
  
## Add the Following Files

1. style > index.scss
2. style > variables.scss
3. pages > index.js
4. pages > home directory > index.js & index.module.scss
5. database > index.js

## database > index.js
```
class Database {
  constructor() {
    this.multidimensionalArray = {
      About: [
        {
          name: "CDL Mockups",
        }
      ]
    };

    this.flatArray = {
      title: "about",
      text: "something",
      category: "text",
    }
  }
}

const store = new Database();
export default store;
```

## style > index.scss

```
@import "./variables.scss";
@import url("https://use.typekit.net/mfe7wjt.css"); //the font you want to use
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
```

## style > variables.scss

```
$primary: #00fff5;
$secondary: #ff5de0;
$color: #1e1e1e;
$color: #292929;
```

## home > index.js
```
import React from "react";
import style from "./index.module.scss";

class Home extends React.Component {

  constructor(props) {
    super();
    this.state = {
      string: "",
      int: 0,
      array: [],
      userInput: "",
    };
  }

  handleChange = (e) => {
    this.setState({ searchItem: e.target.value });
    console.log(this.state.searchItem);
  };

  render() {
    return (
      <body className={style.mainContainer}>
        <section>
          <h1>Hello</h1>

          <input
            type="text"
            name={"userInput"}
            onChange={this.handleChange}
          ></input>
          <label>Placeholder</label>
        </section>
      </body>
    );
  }
}

export default Home;
```

## home > index.module.scss
```
@import "../../style/variables.scss";

/*Media Queries*/
/* Larger than tablet (also point when grid becomes active) */
@media (min-width: 550px) {
}

/* Larger than tablet */
@media (min-width: 750px) {
}

/* Larger than desktop */
@media (min-width: 1000px) {
}

/* Larger than Desktop HD */
@media (min-width: 1200px) {
}

/* For TV Screens & Projectors */
@media (min-width: 2000px) {
}
```

## App.js
```
import React, { Component } from "react";
import {
  BrowserRouter as Router,
  Switch,
  Route,
  withRouter,
} from "react-router-dom";
import style from "./style/index.scss";
import Home from "./pages/home";

const App = withRouter(
  class App extends Component {
    constructor(props) {
      super(props);
      this.state = {
      };
    }

    render() {
      return (
        <div className={style.mainContainer}>
            <Switch>
              <Route path="/" exact component={Home}></Route>
            </Switch>
        </div>
      );
    }
  }
);

class RoutedApp extends Component {
  render() {
    return (
      <Router basename="/printerapi">
        <App />
      </Router>
    );
  }
}

export default RoutedApp;
```

## database folder > firebase.js
```
import firebase from "firebase";

const config = {
    apiKey: process.env.REACT_APP_API_KEY,
    authDomain: process.env.REACT_APP_AUTH_DOMAIN,
    databaseURL: process.env.REACT_APP_DATABASE_URL,
    projectId: process.env.REACT_APP_PROJECT_ID,
    storageBucket: process.env.REACT_APP_STORAGE_BUCKET,
    messagingSenderId: process.env.REACT_APP_MESSAGING_SENDER_ID,
    appId: process.env.REACT_APP_APP_ID
};

firebase.initializeApp(config);
export default firebase;
```
## Maps for local arrays 
```
{this.state.todo.map((item) => (<div key={item}>{item}</div>))}
```

## Submitting Forms 
```
  submit = (e) => {
    e.preventDefault();
    document.getElementById("todo").value = "";
    if (!this.state.userInput) {
      this.setState({ showError: true });
    } else {
      this.setState({
        showError: false,
        todo: [...this.state.todo, this.state.userInput],
      });
    }
  };
```

<hr>

## Updating Errors
`npm update react`

`The package-lock.json file was created with an old version of npm`

`Node sass`
Uninstall node-sass: `npm uninstall node-sass` 

Delete package-lock.json, and clean the cache: `npm cache clean --force`

then do `npm update` `npm install` `npm update` 

then again try to install node sass: 
`npm install node-sass`

If this doesn't work, Try to rebuild node-sass:

npm rebuild node-sass

## Errors
A branch named 'gh-pages' already exists
https://stackoverflow.com/questions/63964575/fatal-a-branch-named-gh-pages-already-exists

Public URL Pains
https://stackoverflow.com/questions/27928372/react-router-urls-dont-work-when-refreshing-or-writing-manually

Finding ways to remove the hash
https://stackoverflow.com/questions/56981230/how-to-redirect-old-react-router-hashrouter-with-the-to-browserrouter

```
To be honest, none of these solutions worked for me really, I wanted to perform a redirect from all my previous routes to the new ones without #.

While the accepted answer should be fine for most cases, I'm also handling 404s, which would not really be caught by such redirect.

Ended up adding a guard interacting with React Router history before rendering my switch:

function App() {
  const history = useHistory()

  if (location.hash.startsWith('#/')) {
    history.push(location.hash.replace('#', '')) // or history.replace
  }

  return (
    <Switch>
      <Route path="/" exact component={ Home } />
      ...
      <Route path="*" component={ PageNotFound } />
    </Switch>
  )
}
```

## Debugging
[Node sass issues?](https://stackoverflow.com/questions/46515077/unable-to-install-node-sass-in-my-project)

## Functional Component
```

import React from 'react';
const HelloWorld = () => {
   return (
      <div>
         <p>Hello World!</p>
      </div>
   )
}
export default HelloWorld;
```

## Class Component
```
import React from 'react';
class HelloWorld extends React.Component {
   render() {
      return (
         <div>
            <p>Hello World!</p>
         </div>
      )
   }
}
export default HelloWorld;
```

## High Order Component
```
import React from 'react';
import MyComponent from './components/MyComponent';
class HelloWorld extends React.Component {
   render() {
      return(
         <div>
            {this.props.myArray.map((element) => (
               <MyComponent data={element} key={element.key} />
            ))}
         </div>
      )
   }
}
export default HelloWorld;
```

## Listen for Dark Mode Preference

useEffect(() => {
  // Add listener to update styles
  window.matchMedia('(prefers-color-scheme: dark)').addEventListener('change', e => onSelectMode(e.matches ? 'dark' : 'light'));

  // Setup dark/light mode for the first time
  onSelectMode(window.matchMedia('(prefers-color-scheme: dark)').matches ? 'dark' : 'light')

  // Remove listener
  return () => {
    window.matchMedia('(prefers-color-scheme: dark)').removeEventListener('change', () => {
    });
  }
}, []);


## Best Way to Add Google Fonts
[Use this Google Webfont Helper](https://google-webfonts-helper.herokuapp.com/fonts)

## Config Github Pages
Deploy your app to github pages via a custom Google Domain name.

[Official Github Docs](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site#configuring-a-records-with-your-dns-provider)

[Source](https://dev.to/trentyang/how-to-setup-google-domain-for-github-pages-1p58)
