# vuejs-nodeapi-sample

> A modern weapon for a more civilised age

## Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build

# build for production and view the bundle analyzer report
npm run build --report
```

For detailed explanation on how things work, checkout the [guide](http://vuejs-templates.github.io/webpack/) and [docs for vue-loader](http://vuejs.github.io/vue-loader).

[vue-cli](https://github.com/vuejs/vue-cli) scaffolded the app and I'm using the webpack template chosen from [this available list of templates](https://github.com/vuejs-templates/).

### Project structure explained

```
 build/ - All build files are here
 config/ - All environment config files are here
 node_modules/ - All the packages required for the vuejs app resides here
 src/
   - assets - All assets reside here
   - components - All our Vue components resides here
   - router - Our router is defined here
   - App.vue - The Parent component
   - main.js - Starting point for our app where the router, template and App component are bound to the root app div
 static/ - contains static files
 index.html - Index file that declares the root div where the App component is been bound to
 package.json - File that contains the names of all the packages residing in node_modules folder
 README.md
 node_modules/ - All the packages required for the react app resides here
```

### Fetching API data

Inside the `utils` directory, there's a `battles-api.js` which fetches the data from the node 
backend and displays it in the frontend.

### Testing

No testing for the time being.
