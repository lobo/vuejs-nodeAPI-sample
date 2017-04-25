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

### To run the Node API

The following will run in `localhost:3333`
```
cd ./server
node server.js
```

### Authentication explained

The logic is saved in the `utils/auth.js` file.

1. A hosted version of Auth0 Lock is used in the `login` method.
Credentials are passed onto that method.

2. The auth0 package calls the Auth0's `authorize` endpoint. With all the details we passed
 to the method, our client app will be validated and authorized to perform authentication. 
 You can learn more about the specific values that can be passed to the authorize method
  [here](https://auth0.com/docs/libraries/auth0js/v8#login).

3. The token expiration is checked in the `getTokenExpirationDate` and `isTokenExpired` methods. 
The `isLoggedIn` method returns true or false based on the presence and validity of a user `id_token`. 
For more information on `id_token`, [please check here](https://auth0.com/docs/tokens/id-token).

4. The component `callback.vue` will be activated when the `localhost:8080/callback` route is called and it
 will process the redirect from Auth0 and ensure that the right data back after a successful authentication 
 was received. The component will store the `access_token` and `id_token`.

5. Once a user is authenticated, Auth0 will redirect back to the application and call the `/callback` route. 
Auth0 will also append the `id_token` as well as the `access_token` to this request, and the `callback.vue` 
component will make sure to properly process and store those tokens in localStorage. 
If all is well, meaning the `id_token` and `access_token` are received, and verified the nonce, 
the user will be redirected back to the `/` page and will be in a logged in state.
