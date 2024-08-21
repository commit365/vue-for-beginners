# Lesson 16: Handling API Requests

In this lesson, we will learn how to handle API requests in Vue.js using Axios, a popular library for making HTTP requests. We will cover how to fetch data from an API and display it in your Vue application.

## Making HTTP Requests Using Axios

### What is Axios?

Axios is a promise-based HTTP client for JavaScript that can be used in both the browser and Node.js. It simplifies the process of making HTTP requests and handling responses. Axios supports features such as request and response interceptors, automatic JSON data transformation, and cancellation of requests.

### Step 1: Installing Axios

To use Axios in your Vue project, you need to install it via npm. Open your terminal and run the following command:

```bash
npm install axios
```

### Step 2: Importing Axios

Once Axios is installed, you can import it into your Vue component or your main entry file. Here’s how to import Axios in a Vue component:

```javascript
import axios from 'axios';
```

## Fetching Data from an API and Displaying It in Your App

### Step 1: Creating a Component to Fetch Data

Let’s create a simple Vue component that fetches data from a public API and displays it. We will use the JSONPlaceholder API, which provides fake data for testing and prototyping.

Here’s an example of a component that fetches a list of posts:

```html
<template>
    <div>
        <h1>Posts</h1>
        <ul>
            <li v-for="post in posts" :key="post.id">
                <h2>{{ post.title }}</h2>
                <p>{{ post.body }}</p>
            </li>
        </ul>
        <p v-if="loading">Loading...</p>
        <p v-if="error">{{ error }}</p>
    </div>
</template>

<script>
import axios from 'axios';

export default {
    data() {
        return {
            posts: [],
            loading: true,
            error: null
        };
    },
    created() {
        this.fetchPosts();
    },
    methods: {
        async fetchPosts() {
            try {
                const response = await axios.get('https://jsonplaceholder.typicode.com/posts');
                this.posts = response.data;
            } catch (err) {
                this.error = 'Failed to fetch posts: ' + err.message;
            } finally {
                this.loading = false;
            }
        }
    }
};
</script>

<style scoped>
/* Add any component-specific styles here */
h1 {
    color: #333;
}
</style>
```

### Explanation of the Code

- **Data Properties**: 
  - `posts`: An array to hold the fetched posts.
  - `loading`: A boolean to indicate whether data is being loaded.
  - `error`: A string to hold any error messages that occur during the fetch.

- **Lifecycle Hook**: The `created` lifecycle hook is used to call the `fetchPosts` method when the component is created. This ensures that the data is fetched as soon as the component is initialized.

- **Fetching Data**: The `fetchPosts` method uses Axios to make a GET request to the JSONPlaceholder API. If the request is successful, the data is assigned to the `posts` array. If there is an error, the error message is stored in the `error` property.

- **Displaying Data**: The template uses a `v-for` directive to iterate over the `posts` array and display each post's title and body. It also shows a loading message while the data is being fetched and displays an error message if the fetch fails.

### Step 2: Using the Component

To use this component, simply include it in your main application file or another component:

```html
<template>
    <div id="app">
        <post-list></post-list>
    </div>
</template>

<script>
import PostList from './components/PostList.vue';

export default {
    components: {
        PostList
    }
};
</script>
```

### Explanation of the Usage

- **Component Registration**: The `PostList` component is imported and registered in the parent component, allowing it to be used in the template.

## Conclusion

In this lesson, you learned how to handle API requests in Vue.js using Axios. You created a component that fetches data from an API and displays it in your application, handling loading states and errors effectively.

Handling API requests is a crucial part of building dynamic applications that interact with external data sources. In the next lesson, we will explore computed properties and watchers in Vue.js.