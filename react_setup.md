# vs code settings for prettier format on save
> this goes in the workspace settings
```json
{
  "editor.formatOnSave": true,
  "javascript.format.enable": false,
  "prettier.eslintIntegration": true
}
```
> this goes in `.eslintrc` file found in root of project
```json
{
  "extends": "fbjs"
}
```
#packages I normally install

> axios, redux, styled components, react router, redux thunk,

yarn add axios redux react-redux redux-devtools styled-components react-router-dom redux-thunk

>sometimes use redux-form

#prettier/eslint dev packages

> found [here](https://www.npmjs.com/package/eslint-config-fbjs)

yarn add --dev \
  eslint-config-fbjs \
  eslint-plugin-babel \
  eslint-plugin-flowtype \
  eslint-plugin-jsx-a11y \
  eslint-plugin-react \
  eslint-plugin-relay \
  eslint \
  babel-eslint

----------

# HMR

```javascript
if (module.hot) {
  module.hot.accept('./App', () => {
    const NextApp = require('./App').default;
    ReactDOM.render(<NextApp />, document.getElementById('root'));
  });
}
```

# set up redux store

1. create `configureStore.js`
2. import redux vars
  `{ createStore, combineReducers, applyMiddleware, compose } from 'redux'`
3. import thunk
  `import thunk from 'redux-thunk`
4. set up variable for redux devtools
  `const composeEnhancers = window.__REDUX_DEVTOOLS_EXTENSION_COMPOSE__ || compose`
5. create store and apply combineReducers and middleware
```javascript
export default () => {
  const store = createStore(
    combineReducers({
	...reducers go here
    }),
    composeEnhancers(applyMiddleware(thunk))
  );
  return store;
};
```

# set up reducers

# set up App.js to connect to redux store
1. import Provider from 'react-redux'
2. import store we created and make a store var
3. wrap contents of App.js with:
```javascript
<Provider store = {store}>
	...contents of App.js
</Provider>
```
# set up React-Router // AppRouter.js into App.js
inside AppRouter.js
```javascript
export default () => {
  return (
    <BrowserRouter>
      <div>
        <Header />
        <Switch>
          <Route exact path="/" component={Welcome} />
        </Switch>
      </div>
    </BrowserRouter>
  );
};
```
Inside App.js
1. import AppRouter.js
2. place inside Provider


# final notes
I have alread installed `styled-components` which is what I use for css styling. I can either keep the styles on each component, have a directory with styles to import like components or a combination of both

#extra

## tests
1. create `tests` folder inside `src` folder
2. add testing packages to project
`$ yarn add enzyme enzyme-adapter-react-16 react-test-renderer jest-enzyme`

3. create `setupTests.js` in `src`
```javascript
import 'jest-enzyme';
import { configure } from 'enzyme';
import Adapter from 'enzyme-adapter-react-16';

configure({ adapter: new Adapter() });
```

### example shallow render test for App.js
inside `App.test.js` from `/tests` in `src`
```javascript
import React from 'react';
import { shallow } from 'enzyme';
import App from '../App';

it('renders without crashing', () => {
  shallow(<App />);
});
```



















