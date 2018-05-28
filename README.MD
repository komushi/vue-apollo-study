# vue-apollo-study

**Tutorial/Example of a Vue.js app using Apollo GraphQL**

## 1. How was this study project created.
### 1-1. Create this project with Vue CLI v3+
```
$ vue create vue-apollo-study
```

### 1-2. Add vue-cli-plugin-apollo
```
$ cd vue-apollo-study
$ vue add apollo

? Add example code Yes
? Add a GraphQL API Server? Yes
? Enable automatic mocking? No
? Add Apollo Engine? No

```

### 1-3. Edit App.vue to inclued the ApolloExample.vue
```
<template>
  <div id="app">
    <img src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
    <apollo-example></apollo-example>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import ApolloExample from './components/ApolloExample.vue'

export default {
  name: 'app',
  components: {
    HelloWorld,
    ApolloExample
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
```

### 1-4. Edit main.js to include vue-apollo provider
```
import Vue from 'vue'
import App from './App.vue'
import { createProvider } from './vue-apollo'

Vue.config.productionTip = false

new Vue({
  provide: createProvider().provide(),
  render: h => h(App)
}).$mount('#app')

```

## 2. Quick Start to run the ApolloExample
### 2-1. Start the GraphQL API Server
```
$ npm run graphql-api
```

### 2-2. Access http://localhost:4000/ and test the following queries
![GraphQL API Server](https://raw.githubusercontent.com/komushi/vue-apollo-study/master/image/image1.png)
```
query hello {
  hello(name: "xu1")
}
```

```
query messages {
  messages {
    text
    id
  }
}
```

### 2-3. Start the client application on another terminal
```
$ npm run serve
```

### 2-4. Access http://localhost:8080/ and play with ApolloExample
![GraphQL Client App](https://raw.githubusercontent.com/komushi/vue-apollo-study/master/image/image2.png)

--------
## References
* https://github.com/Akryum/vue-apollo
* https://github.com/Akryum/vue-cli-plugin-apollo
* https://github.com/vuejs/vue-cli