# Tutorial 01 - Getting Started

Welcome to the first exercise in the **Vue Track** of this Apollo Client Tutorial! If you prefer React, React Native or  Angular 2 over Vue.js, head over to the respective tutorial track.

<iframe width="560" height="315" src="https://www.youtube.com/embed/TiqPHEzSOg0?list=PLn2e1F9Rfr6neWxkWtlTAwshh07-m1p5I" frameborder="0" allowfullscreen></iframe>

## Goal

The **goal** of this first exercise is to install a Vue.js App and run it afterwards. You will get familiar with the infrastructure surrounding Apollo Client for Vue.js and with the app structure of the Pokedex.

We will see a generic greeting in our pokedex at the end of this exercise:

![](../images/react-exercise-01-pokedex.png)

## Introduction

Sign up with GitHub to receive your own `pokedex-vue` here:

<!-- __DOWNLOAD_VUE__ -->

Now change to the first exercise, install the dependencies and start the app from your console

```sh
cd pokedex-vue/exercise-01
yarn install # or npm install
yarn dev # or npm dev
```

## Getting Familiar with the app

Let's take a moment to get more familiar with the structure of the app.

The starting point for our app is `src/index.js`. At the moment, all that happens here is setting up the  Vue.js application with the router to render the `PokemonList` component for the `/` route path.

## Adding Apollo Client to the app

Let's first open `src/package.json` to have a look what packages we are using.

* `apollo-client` - the core package exposes the vanilla JS Apollo Client which provides the core functionality
* `vue-apollo` - the Vue.js integration which integrates Apollo in your Vue components with declarative queries.

Go ahead and create a new file `./src/apollo/index.js` then configure these packages as shown below:

```js
import Vue from 'vue';
import ApolloClient, { createNetworkInterface } from 'apollo-client';
import VueApollo from 'vue-apollo';

const apolloClient = new ApolloClient({
  networkInterface: createNetworkInterface({
    uri: 'https://api.graph.cool/simple/v1/__PROJECT_ID__'
  }),
  dataIdFromObject: r => r.id
});

Vue.use(VueApollo, {
  apolloClient
});

export default apolloClient;
```

Open the `./src/index.js` and import this new file:

```js
import './apollo';
```

If you signed up with GitHub and downloaded the example, we already took care of this step for the following exercises.

## Starting the app

To confirm your environment is all correctly setup, open [http://localhost:3000](http://localhost:3000) in your browser and you should see the greeting from the Pokedex component.

## Recap

Great, you did it! You successfully ran the Vue.js app and got familiar with its general structure. Let's quickly summarize what we've learned so far:

* To use **Apollo Client**, we need the `apollo-client` and need to setup its **networkInterface**.
* We can **issue queries and mutations** in our Vue.js components by using the **vue-apollo** plugin.
* We will use the **PokemonList component** to list our pokemons and to offer other features.
