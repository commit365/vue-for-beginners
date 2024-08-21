# Lesson 2: Setting Up the Development Environment

In this lesson, we will set up your development environment for Vue.js. This includes installing Node.js and npm (Node Package Manager), as well as setting up Vue CLI (Command Line Interface) for project scaffolding.

## Installing Node.js and npm

Node.js is a JavaScript runtime that allows you to run JavaScript on the server side. npm is the package manager for Node.js, which you will use to install Vue.js and other libraries.

### Step 1: Download Node.js

1. **Visit the Node.js website**: Go to [nodejs.org](https://nodejs.org/).
2. **Choose the version**: You will see two versions available:
   - **LTS (Long Term Support)**: Recommended for most users as it is more stable.
   - **Current**: Includes the latest features but may not be as stable.
3. **Download the installer**: Click on the appropriate version for your operating system (Windows, macOS, or Linux).

### Step 2: Install Node.js

1. **Run the installer**: Open the downloaded file and follow the installation prompts.
2. **Accept the license agreement**: Make sure to read and accept the license agreement.
3. **Choose installation options**: You can typically leave the default options selected.
4. **Complete the installation**: Click "Install" and wait for the process to finish.

### Step 3: Verify Installation

To verify that Node.js and npm are installed correctly, open your terminal (Command Prompt on Windows, Terminal on macOS/Linux) and run the following commands:

```bash
node -v
```
This command will display the installed version of Node.js. 

```bash
npm -v
```
This command will display the installed version of npm. 

If both commands return version numbers, you have successfully installed Node.js and npm!

## Setting Up Vue CLI for Project Scaffolding

Vue CLI is a powerful tool that helps you create and manage Vue.js projects. It provides a simple way to set up a new Vue application with a pre-configured build system.

### Step 1: Install Vue CLI

With npm installed, you can install Vue CLI globally on your machine. Run the following command in your terminal:

```bash
npm install -g @vue/cli
```

The `-g` flag installs Vue CLI globally, making it accessible from any directory.

### Step 2: Verify Vue CLI Installation

After the installation is complete, verify that Vue CLI is installed correctly by running:

```bash
vue --version
```

This command will display the installed version of Vue CLI. If you see a version number, you are ready to start creating Vue projects!

### Step 3: Creating a New Vue Project

Now that you have Vue CLI installed, you can create a new Vue project. Run the following command, replacing `my-vue-app` with your desired project name:

```bash
vue create my-vue-app
```

During the project creation process, Vue CLI will prompt you to select a preset. You can choose the default preset, which includes Babel and ESLint, or manually select features based on your needs.

### Step 4: Navigate to Your Project Directory

Once the project is created, navigate into the project directory:

```bash
cd my-vue-app
```

### Step 5: Run the Development Server

To start the development server and see your Vue application in action, run:

```bash
npm run serve
```

After a few moments, you should see output in the terminal indicating that your application is running. Open your web browser and navigate to `http://localhost:8080` to view your new Vue.js application!

## Conclusion

In this lesson, we successfully set up your development environment for Vue.js by installing Node.js and npm, and setting up Vue CLI for project scaffolding. You are now ready to start building Vue applications!

In the next lesson, we will create your first Vue.js application and explore its structure.