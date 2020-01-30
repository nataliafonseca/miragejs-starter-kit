# Mirage JS Starter Kit

[From Mirage website](https://miragejs.com/):

> Mirage JS is an API mocking library that lets you build, test and share a complete working JavaScript application without having to rely on any backend services.

Their documentation is straight to the point but it only helps you setting up a simple server without any suggestion of folder organization. This starter kit keeps things separate into their own folders, introducing separation of concerns and making it easier to reason about all the parts.

---

## How to use it

### 1. Having started a React or Vue.js project, copy all the files to the src folder:

```
cd src && npx degit vedovelli/miragejs-starter-kit miragejs
```

[What is **degit**?](https://github.com/Rich-Harris/degit#readme)

This will create the `miragejs` folder inside `src`. You can use any folder name you find best.

**IMPORTANT**: do NOT omit the folder name in the degit command otherwise all starter kit's folders will be created inside your src folder, messing up your project organization.

### 2. Make sure all dependencies are installed:

```
npm install --save-dev miragejs faker
```

### 3. Make your project aware of Mirage JS:

**React**

```
import React from "react";
import ReactDOM from "react-dom";
import App from "./App";
import { makeServer } from "./miragejs/server";

if (process.env.NODE_ENV === "development") {
  makeServer();
}

ReactDOM.render(<App />, document.getElementById("root"));
```

**Vue.js**

```
import Vue from "vue";
import App from "./App.vue";
import router from "./router";
import store from "./store";
import { makeServer } from "./server";

if (process.env.NODE_ENV === "development") {
  makeServer();
}

Vue.config.productionTip = false;

new Vue({
  router,
  store,
  render: h => h(App)
}).$mount("#app");
```

### 4. Calling the API

Inside any component of your application and using your favorite HTTP request's library make a call to `api/users`. You will receive back a list of 10 objects with the following shape:

```
{id: "1", name: "Some name", mobile: "+1 555 525636"}
```

Additionally if you call `api/products` you'll receive back a list of 3 objects with the following shape:

```
{
  id: "1",
  name: "Javascript coffee mug",
  description: "We are nothing without coffee",
  price: 3.5
},
```

Those routes operate with a `resource` meaning they accept all HTTP verbs involved in a CRUD operation.

### 5. Adding your own content

Lastly tweak `factories`, `fixtures` and `seeds` to accommodate your own needs.

---

## Folder structure
