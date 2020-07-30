# Quickstarts for a Vanilla project

## Creating a new react.js project

```
npx/npm create-react-app my-app
cd my-app
```
SCSS Management:

```
npm install node-sass
```
Page Routing:
```
npm install react-router-dom
```
Firebase Data:
```
npm install --save firebase
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
And then open & start the project
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
    this.workData = {
      SketchArray: [
        {
          name: "CDL Mockups",
          medium: "Adobe XD",
          image: require("../images/cdlmockup-thumb.jpg"),
          link: "page",
          description: "this is a mockup for blank",
        },
        {
          name: "Envisioning Justice",
          medium: "Adobe XD",
          image: require("../images/cdlmockup-thumb.jpg"),
          link: "page",
          description: "this is a mockup for blank",
        },
        {
          name: "Print Dashboard",
          medium: "Post Its",
          image: require("../images/cdlmockup-thumb.jpg"),
          link: "page",
          description: "this is a mockup for blank",
        },
      ],
      UXArray: [
        {
          name: "The Bus Hawai'i",
          medium: "Case Study",
          image: require("../images/cdlmockup-thumb.jpg"),
          link: "page",
          description: "this is a mockup for blank",
        },
        {
          name: "Transit Data",
          medium: "Research",
          image: require("../images/cdlmockup-thumb.jpg"),
          link: "page",
          description: "this is a mockup for blank",
        },
      ],
      ProgArray: [
        {
          name: "Print Dashboard",
          medium: "React & Firebase",
          image: require("../images/cdlmockup-thumb.jpg"),
          link: "page",
          description: "this is a mockup for blank",
        },
        {
          name: "DaBus Hawai'i",
          medium: "React, Firebase & TheBus API",
          image: require("../images/cdlmockup-thumb.jpg"),
          link: "page",
          description: "this is a mockup for blank",
        },
        {
          name: "Passion to Purpose",
          medium: "React.js",
          image: require("../images/cdlmockup-thumb.jpg"),
          link: "page",
          description: "this is a mockup for blank",
        },
      ],
    };
    this.projects = {
      Featured: [
        {
          name: "Rebrand",
          collab: "Convergence Design Lab",
          image: require("../images/cdlmockup-thumb.jpg"),
          link: "page",
        },
        {
          name: "Passion to Purpose",
          collab: "Convergence Design Lab",
          image: require("../images/cdlmockup-thumb.jpg"),
          link: "page",
        },
        {
          name: "Equity Framework",
          collab: "Chicago Public Schools",
          image: require("../images/cdlmockup-thumb.jpg"),
          link: "page",
        },
        {
          name: "Da Bus",
          collab: "The Bus Hawai'i",
          image: require("../images/cdlmockup-thumb.jpg"),
          link: "page",
        },
        {
          name: "Nettiquette Game",
          collab: "Augmented Reality",
          image: require("../images/cdlmockup-thumb.jpg"),
          link: "page",
        },
      ],
    };
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

