# Lesson 21: Deploying Your Vue Application

In this lesson, we will explore how to prepare your Vue application for production and deploy it to popular platforms like Netlify and Vercel. We will cover the necessary steps to ensure a smooth deployment process.

## Preparing Your Application for Production

### Step 1: Build Your Application

Before deploying your Vue application, you need to build it for production. This process compiles and optimizes your application, generating static files that can be served by a web server. To build your application, run the following command in your terminal:

```bash
npm run build
```

This command will create a `dist` directory containing the optimized files for your application. Make sure to test your production build locally before deploying.

### Step 2: Previewing Your Build Locally

To preview your production build, you can use a simple static file server. Install the `serve` package globally if you haven't already:

```bash
npm install -g serve
```

Then, run the following command to serve your `dist` directory:

```bash
serve -s dist
```

Open your browser and navigate to `http://localhost:5000` (or the port specified in the terminal) to see your application running in production mode.

## Deploying to Platforms Like Netlify or Vercel

### Deploying to Netlify

Netlify is a popular platform for deploying static sites and offers a simple deployment process.

#### Step 1: Create a Netlify Account

If you don’t have a Netlify account, go to [Netlify](https://www.netlify.com/) and sign up for free.

#### Step 2: Deploying Your Application

There are two main ways to deploy your Vue application to Netlify:

1. **Drag and Drop Method**:
   - Go to the [Netlify Drop](https://app.netlify.com/drop) page.
   - Drag your `dist` folder into the browser window.
   - Netlify will automatically deploy your application and provide you with a live URL.

2. **Git-based Deployment**:
   - Push your code to a Git repository (GitHub, GitLab, or Bitbucket).
   - In your Netlify dashboard, click on "New Site from Git."
   - Connect your repository and select the branch to deploy.
   - Set the build command to `npm run build` and the publish directory to `dist`.
   - Click "Deploy Site" to start the deployment process.

#### Step 3: Add a Custom Domain (Optional)

Once your site is deployed, you can add a custom domain. Go to the "Domain settings" in your Netlify dashboard and follow the instructions to set up your domain.

### Deploying to Vercel

Vercel is another excellent platform for deploying Vue applications with seamless integration for Git repositories.

#### Step 1: Create a Vercel Account

If you don’t have a Vercel account, go to [Vercel](https://vercel.com/) and sign up for free.

#### Step 2: Deploying Your Application

1. **Import Your Project**:
   - Push your code to a Git repository.
   - In your Vercel dashboard, click on "New Project."
   - Import your repository from GitHub, GitLab, or Bitbucket.

2. **Configure Deployment Settings**:
   - Vercel will automatically detect that you are using Vue and enable the correct settings for deployment.
   - Review the settings and click "Deploy."

3. **Live URL**:
   - Once deployed, Vercel will provide you with a live URL for your application (e.g., `https://your-project-name.vercel.app`).

#### Step 3: Add a Custom Domain (Optional)

To add a custom domain, navigate to your project settings in the Vercel dashboard. Click on "Domains" and follow the instructions to add and configure your custom domain.

## Conclusion

In this lesson, you learned how to prepare your Vue application for production and deploy it to platforms like Netlify and Vercel. Both platforms offer simple and efficient deployment processes, allowing you to get your application live with minimal effort.

Deploying your application is a crucial step in the development process, and understanding how to do it effectively will help you share your work with the world. In the next lesson, we will explore best practices for maintaining and scaling your Vue applications.