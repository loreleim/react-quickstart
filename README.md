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

1. serviceWorker (remove line 5 on the index.js file aka the service worker import, and line 12's service worker .register())
2. setupTests
3. logo.svg (remove the import on the App.js file, and the html reference in the render <img> tag)
4. App.test.js

## Router Setup
```
const App = withRouter(
  class App extends Component {
    constructor(props) {
      super(props);
    }

    render() {
      return (
        <div className={style.MainContainer}>
          <AuthProvider>
            <Switch>
              <Route path="/" exact component={Home}></Route>
              <Route path="/fares" component={Fares}></Route>
              <Route path="/tripplanner" component={TripPlanner}></Route>
              <Route path="/about" component={About}></Route>
              <Route path="/login" component={Login}></Route>
            </Switch>
          </AuthProvider>
        </div>
      );
    }
  }
);

class RoutedApp extends Component {
  render() {
    return (
      <Router basename={process.env.PUBLIC_URL}>
        <App />
      </Router>
    );
  }
}

export default RoutedApp;
```

## License

[MIT](https://choosealicense.com/licenses/mit/)
