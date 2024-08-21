# Lesson 17: Building a Simple Project

In this lesson, we will integrate the concepts we have learned so far to build a small Vue.js project. This project will demonstrate how to implement routing, state management with Vuex, and API calls using Axios. We will create a simple blog application that fetches posts from an API, displays them, and allows users to view details of each post.

## Project Overview

Our simple blog application will have the following features:

1. A homepage that displays a list of blog posts.
2. A detailed view for each post.
3. State management using Vuex to manage the posts.
4. Routing using Vue Router to navigate between the homepage and the post details.
5. Fetching data from the JSONPlaceholder API.

## Step 1: Setting Up the Project

### Step 1.1: Create a New Vue Project

First, create a new Vue project using Vue CLI:

```bash
vue create simple-blog
```

### Step 1.2: Install Dependencies

Navigate to your project directory and install Vue Router and Axios:

```bash
cd simple-blog
npm install vue-router axios
```

### Step 1.3: Set Up Vuex

Create a new file named `store.js` in the `src` directory for Vuex store configuration:

```javascript
import Vue from 'vue';
import Vuex from 'vuex';
import axios from 'axios';

Vue.use(Vuex);

const store = new Vuex.Store({
    state: {
        posts: [],
        loading: false,
        error: null
    },
    mutations: {
        setPosts(state, posts) {
            state.posts = posts;
        },
        setLoading(state, loading) {
            state.loading = loading;
        },
        setError(state, error) {
            state.error = error;
        }
    },
    actions: {
        async fetchPosts({ commit }) {
            commit('setLoading', true);
            try {
                const response = await axios.get('https://jsonplaceholder.typicode.com/posts');
                commit('setPosts', response.data);
            } catch (err) {
                commit('setError', 'Failed to fetch posts: ' + err.message);
            } finally {
                commit('setLoading', false);
            }
        }
    },
    getters: {
        allPosts(state) {
            return state.posts;
        },
        isLoading(state) {
            return state.loading;
        },
        error(state) {
            return state.error;
        }
    }
});

export default store;
```

## Step 2: Setting Up Vue Router

Create a new file named `router.js` in the `src` directory for routing configuration:

```javascript
import Vue from 'vue';
import VueRouter from 'vue-router';
import Home from './components/Home.vue';
import PostDetail from './components/PostDetail.vue';

Vue.use(VueRouter);

const routes = [
    { path: '/', component: Home },
    { path: '/posts/:id', component: PostDetail, props: true }
];

const router = new VueRouter({
    routes
});

export default router;
```

### Step 2.1: Create Components

Create two components: `Home.vue` and `PostDetail.vue` in the `src/components` directory.

**Home.vue**:

```html
<template>
    <div>
        <h1>Blog Posts</h1>
        <ul>
            <li v-for="post in posts" :key="post.id">
                <router-link :to="'/posts/' + post.id">{{ post.title }}</router-link>
            </li>
        </ul>
        <p v-if="loading">Loading posts...</p>
        <p v-if="error">{{ error }}</p>
    </div>
</template>

<script>
import { mapState, mapGetters } from 'vuex';

export default {
    computed: {
        ...mapState(['posts', 'loading', 'error']),
        ...mapGetters(['allPosts', 'isLoading', 'error'])
    },
    created() {
        this.$store.dispatch('fetchPosts');
    }
};
</script>
```

**PostDetail.vue**:

```html
<template>
    <div>
        <h1>{{ post.title }}</h1>
        <p>{{ post.body }}</p>
        <router-link to="/">Back to Posts</router-link>
    </div>
</template>

<script>
export default {
    props: ['id'],
    data() {
        return {
            post: {}
        };
    },
    async created() {
        const response = await fetch(`https://jsonplaceholder.typicode.com/posts/${this.id}`);
        this.post = await response.json();
    }
};
</script>
```

## Step 3: Integrating Everything in `main.js`

Now, integrate Vuex and Vue Router into your main application file, `main.js`:

```javascript
import Vue from 'vue';
import App from './App.vue';
import store from './store';
import router from './router';

new Vue({
    render: h => h(App),
    store,
    router
}).$mount('#app');
```

## Step 4: Update the App Component

Update your `App.vue` file to include the router view:

```html
<template>
    <div id="app">
        <router-view></router-view>
    </div>
</template>

<script>
export default {
    name: 'App'
};
</script>

<style>
/* Add global styles here */
</style>
```

## Step 5: Running the Application

Now that everything is set up, you can run your application:

```bash
npm run serve
```

Open your browser and navigate to `http://localhost:8080`. You should see a list of blog posts. Clicking on a post title will take you to a detailed view of that post.

## Conclusion

In this lesson, you integrated the concepts learned throughout the course to build a simple blog application using Vue.js. You implemented routing with Vue Router, managed state with Vuex, and made API calls using Axios.

This project serves as a foundation for building more complex applications. In the next lesson, we will explore more advanced Vue.js features and best practices.