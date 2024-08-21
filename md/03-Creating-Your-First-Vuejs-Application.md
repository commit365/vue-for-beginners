# Lesson 3: Creating Your First Vue.js Application

In this lesson, you will create your first Vue.js application using Vue CLI. We will go through the steps to initialize a new Vue project and run it in your browser.

## Initializing a New Vue Project Using Vue CLI

### Step 1: Open Your Terminal

Open your terminal or command prompt. This is where you will run the commands to create your Vue project.

### Step 2: Create a New Vue Project

To create a new Vue project, use the following command. Replace `my-first-vue-app` with your desired project name:

```bash
vue create my-first-vue-app
```

### Step 3: Select a Preset

During the project creation process, Vue CLI will prompt you to select a preset. You have two options:

1. **Default (Vue 3)**: This preset includes Babel and ESLint, which are useful for most projects.
2. **Manually select features**: This option allows you to customize your setup by selecting specific features.

For beginners, it is recommended to choose the default preset. To do this, simply press `Enter`.

### Step 4: Wait for Installation

Vue CLI will create your project and install the necessary dependencies. This process may take a few moments. Once it’s complete, you will see a message indicating that the project has been created successfully.

### Step 5: Navigate to Your Project Directory

Change into your newly created project directory with the following command:

```bash
cd my-first-vue-app
```

## Running Your Application in the Browser

Now that your Vue project is set up, it’s time to run the application and see it in action.

### Step 1: Start the Development Server

In your project directory, run the following command to start the development server:

```bash
npm run serve
```

### Step 2: Access Your Application

After running the command, Vue CLI will compile your application and start a local development server. You will see output in the terminal similar to this:

```
 App running at:
 - Local:   http://localhost:8080/
 - Network: http://192.168.x.x:8080/
```

Open your web browser and navigate to `http://localhost:8080`. You should see the default Vue.js welcome page, which confirms that your application is running successfully!

### Step 3: Explore the Project Structure

Take a moment to explore the structure of your new Vue project. Here are some key files and directories:

- **`src/`**: This directory contains the source code for your application.
  - **`main.js`**: The entry point of your application where Vue is initialized.
  - **`App.vue`**: The root component of your application.
  - **`components/`**: A folder for your Vue components.

- **`public/`**: This directory contains static assets, such as the `index.html` file that serves as the main HTML file for your application.

- **`package.json`**: This file contains metadata about your project and lists the dependencies used.

## Conclusion

In this lesson, you successfully created your first Vue.js application using Vue CLI. You learned how to initialize a new project, run the development server, and explore the project structure.

In the next lesson, we will dive deeper into understanding the Vue instance and its lifecycle. Keep experimenting with your new application, and happy coding!
