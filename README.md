# Quickstarts for a Vanilla project

## Creating a new react.js project

```
npx/npm create-react-app my-app
cd my-app
npm start
```

And then for scss management:

```
npm install node-sass
```
For page routing
```
npm install react-router-dom
```
For Firebase Data Management
```
npm install --save firebase
```

## Organization and Structure

Within the src folder please create the following folders:

1. components (place your reusable code here)
2. images (.svg, .jpg, or storage .ai files)
3. pages (index.js shall house your router)
4. style (contains .scss files, index.scss shall be the main stylesheet)

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

## index.scss

```
@import "./variables.scss";
@import url("https://use.typekit.net/mfe7wjt.css"); //the font you want to use
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
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

## License

[MIT](https://choosealicense.com/licenses/mit/)
