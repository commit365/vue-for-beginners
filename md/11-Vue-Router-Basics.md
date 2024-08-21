# Lesson 11: Vue Router Basics

In this lesson, we will explore Vue Router, a powerful library for managing navigation in Vue.js applications. We will learn how to set up Vue Router, create routes, and link components to enable navigation between different views.

## Setting Up Vue Router for Navigation

### Step 1: Install Vue Router

If you are using Vue CLI to create your project, you can add Vue Router during the project setup. If you already have a Vue project, you can install Vue Router using npm. Open your terminal and run the following command:

```bash
npm install vue-router
```

### Step 2: Create a Router File

Create a new file named `router.js` in the `src` directory of your Vue project. This file will contain the configuration for your routes.

### Step 3: Import Vue and Vue Router

In your `router.js` file, import Vue and Vue Router, and then use Vue Router as a plugin:

```javascript
import Vue from 'vue';
import VueRouter from 'vue-router';

Vue.use(VueRouter);
```

### Step 4: Define Your Routes

Next, define your routes by creating an array of route objects. Each route object should specify the path and the component to render. Here’s an example:

```javascript
import Home from './components/Home.vue';
import About from './components/About.vue';

const routes = [
    { path: '/', component: Home },
    { path: '/about', component: About }
];
```

### Step 5: Create the Router Instance

Create a new instance of `VueRouter` and pass the routes array to it:

```javascript
const router = new VueRouter({
    routes // short for `routes: routes`
});
```

### Step 6: Export the Router

Finally, export the router instance so you can use it in your main Vue instance:

```javascript
export default router;
```

### Complete `router.js` Example

Here’s how your complete `router.js` file should look:

```javascript
import Vue from 'vue';
import VueRouter from 'vue-router';
import Home from './components/Home.vue';
import About from './components/About.vue';

Vue.use(VueRouter);

const routes = [
    { path: '/', component: Home },
    { path: '/about', component: About }
];

const router = new VueRouter({
    routes
});

export default router;
```

### Step 7: Integrate Router into Your Main Vue Instance

In your `main.js` file, import the router and add it to your Vue instance:

```javascript
import Vue from 'vue';
import App from './App.vue';
import router from './router';

new Vue({
    render: h => h(App),
    router // Add the router here
}).$mount('#app');
```

## Creating Routes and Linking Components

### Step 1: Create Components for Your Routes

Create two simple components, `Home.vue` and `About.vue`, in the `src/components` directory.

**Home.vue**:

```html
<template>
    <div>
        <h1>Home Page</h1>
        <p>Welcome to the Home Page!</p>
    </div>
</template>

<script>
export default {
    name: 'Home'
};
</script>

<style>
/* Add styles here */
</style>
```

**About.vue**:

```html
<template>
    <div>
        <h1>About Page</h1>
        <p>This is the About Page!</p>
    </div>
</template>

<script>
export default {
    name: 'About'
};
</script>

<style>
/* Add styles here */
</style>
```

### Step 2: Add Navigation Links

To navigate between the routes, you can use the `<router-link>` component. Update your `App.vue` file to include navigation links:

```html
<template>
    <div id="app">
        <nav>
            <router-link to="/">Home</router-link>
            <router-link to="/about">About</router-link>
        </nav>
        <router-view></router-view>
    </div>
</template>

<script>
export default {
    name: 'App'
};
</script>

<style>
nav {
    margin-bottom: 20px;
}
nav a {
    margin-right: 15px;
}
</style>
```

### Explanation of the Code

- **`<router-link>`**: This component is used to create navigation links. The `to` attribute specifies the path to navigate to.
- **`<router-view>`**: This component acts as a placeholder for the matched component based on the current route. When you navigate to a different route, the corresponding component will be rendered here.

## Conclusion

In this lesson, you learned how to set up Vue Router for navigation in your Vue.js application. You created routes, linked components, and enabled navigation between different views. Vue Router is a powerful tool that enhances the user experience by providing a seamless way to navigate through your application.

In the next lesson, we will explore state management in Vue.js using Vuex.