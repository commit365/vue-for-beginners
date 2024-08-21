# Lesson 24: Server-Side Rendering (SSR) with Nuxt.js

In this lesson, we will explore Nuxt.js, a powerful framework built on top of Vue.js that enables server-side rendering (SSR) and simplifies the development of Vue applications. We will cover the basics of Nuxt.js and guide you through setting up a basic Nuxt.js application.

## Introduction to Nuxt.js for Server-Side Rendering

### What is Nuxt.js?

Nuxt.js is a framework for building Vue.js applications that provides powerful features such as:

- **Server-Side Rendering (SSR)**: Improves performance and SEO by rendering pages on the server before sending them to the client.
- **Static Site Generation (SSG)**: Allows you to generate static HTML files for your application, which can be served quickly.
- **Routing**: Automatically generates routes based on the file structure, simplifying the process of setting up navigation.
- **Modules**: Offers a rich ecosystem of modules to extend functionality, such as authentication, analytics, and more.

### Benefits of Server-Side Rendering

- **Improved SEO**: Search engines can crawl your site more effectively since the content is rendered on the server.
- **Faster Initial Load**: Users receive a fully rendered page, leading to a better user experience, especially on slower connections.
- **Enhanced Performance**: SSR can reduce the time to first paint (TTFP) and time to interactive (TTI).

## Setting Up a Basic Nuxt.js Application

### Step 1: Installing Nuxt.js

To create a new Nuxt.js application, you can use the create-nuxt-app command-line tool. Open your terminal and run the following command:

```bash
npx create-nuxt-app my-nuxt-app
```

Replace `my-nuxt-app` with your desired project name. This command will prompt you to select various options for your project, including:

- **Package Manager**: Choose between npm or Yarn.
- **UI Framework**: Select a UI framework (e.g., Bootstrap, Vuetify).
- **Server Framework**: Choose a server framework (e.g., Express).
- **Linting Tools**: Select linting tools to maintain code quality.
- **Testing Framework**: Choose a testing framework if needed.
- **Rendering Mode**: Select between Universal (SSR) or Single Page App (SPA).

### Step 2: Navigate to Your Project Directory

Once the setup is complete, navigate to your project directory:

```bash
cd my-nuxt-app
```

### Step 3: Running the Development Server

To start the development server, run the following command:

```bash
npm run dev
```

This command will start the Nuxt.js development server, and you can access your application at `http://localhost:3000`.

### Step 4: Understanding the Project Structure

After creating your Nuxt.js application, you will notice a specific folder structure:

```
my-nuxt-app/
├── assets/
├── components/
├── layouts/
├── pages/
├── plugins/
├── static/
├── store/
├── nuxt.config.js
└── package.json
```

- **assets/**: Contains uncompiled assets such as LESS, SASS, or JavaScript files.
- **components/**: Holds Vue components that can be reused throughout your application.
- **layouts/**: Contains layout components that can be used to wrap pages.
- **pages/**: This is where you define your application’s routes. Each `.vue` file in this directory corresponds to a route.
- **plugins/**: Contains JavaScript plugins that can be run before instantiating the root Vue.js application.
- **static/**: Holds static files that can be served directly (e.g., images).
- **store/**: Contains Vuex store files for state management.
- **nuxt.config.js**: The main configuration file for your Nuxt.js application.

### Step 5: Creating Your First Page

To create your first page, add a new file named `index.vue` in the `pages` directory:

```html
<!-- pages/index.vue -->
<template>
    <div>
        <h1>Welcome to My Nuxt.js App!</h1>
        <p>This is a simple Nuxt.js application with server-side rendering.</p>
    </div>
</template>

<script>
export default {
    // Any component-specific logic can go here
};
</script>

<style>
/* Add styles specific to this page */
h1 {
    color: #42b983;
}
</style>
```

### Step 6: Accessing Your Page

After creating the `index.vue` file, navigate to `http://localhost:3000` in your browser. You should see your welcome message displayed on the page.

## Conclusion

In this lesson, you learned about Nuxt.js and its capabilities for server-side rendering. You set up a basic Nuxt.js application, explored its folder structure, and created your first page. Nuxt.js simplifies the development process of Vue applications and enhances performance and SEO through server-side rendering.

In the next lesson, we will explore more advanced features of Nuxt.js, such as middleware and API integration. 