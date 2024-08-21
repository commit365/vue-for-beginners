# Lesson 15: Styling Vue Components

In this lesson, we will explore how to style Vue components effectively. We will cover applying styles using scoped CSS to ensure styles are encapsulated within components and using CSS frameworks to enhance the styling of your Vue applications.

## Applying Styles to Components Using Scoped CSS

### What is Scoped CSS?

Scoped CSS allows you to apply styles that are specific to a single Vue component without affecting other components. When you use scoped styles, the styles defined in a component are only applied to that component, preventing style conflicts and ensuring better maintainability.

### How to Use Scoped CSS

To use scoped CSS in a Vue component, you can add the `scoped` attribute to the `<style>` tag within the component. Here’s an example:

```html
<template>
    <div class="greeting">
        <h1>{{ message }}</h1>
        <button @click="changeMessage">Change Message</button>
    </div>
</template>

<script>
export default {
    data() {
        return {
            message: 'Hello, Vue!'
        };
    },
    methods: {
        changeMessage() {
            this.message = 'Message has been changed!';
        }
    }
};
</script>

<style scoped>
.greeting {
    text-align: center;
    color: blue;
}

button {
    background-color: green;
    color: white;
    border: none;
    padding: 10px 20px;
    cursor: pointer;
}

button:hover {
    background-color: darkgreen;
}
</style>
```

### Explanation of the Code

- **Scoped Styles**: The `<style scoped>` tag ensures that the styles defined within it only apply to the elements in this component. For example, the `.greeting` class and button styles will not affect other components.
- **Styling Elements**: The styles center the text, change the color of the message, and style the button with a background color and hover effect.

## Using CSS Frameworks with Vue.js

### What are CSS Frameworks?

CSS frameworks are pre-prepared libraries that help you design web applications faster and more efficiently. They provide a set of predefined styles and components that you can use to create responsive and visually appealing user interfaces.

### Popular CSS Frameworks

Some popular CSS frameworks that work well with Vue.js include:

- **Bootstrap**: A widely used framework that provides a responsive grid system, components, and utilities.
- **Tailwind CSS**: A utility-first CSS framework that allows you to build custom designs quickly.
- **Bulma**: A modern CSS framework based on Flexbox, offering a simple and clean design.

### How to Use a CSS Framework in Vue.js

#### Step 1: Install the CSS Framework

You can install a CSS framework using npm. For example, to install Bootstrap, run the following command:

```bash
npm install bootstrap
```

#### Step 2: Import the CSS Framework

After installing the framework, you need to import it in your main entry file (e.g., `main.js` or `App.vue`). For Bootstrap, you can add the following line to your `main.js`:

```javascript
import 'bootstrap/dist/css/bootstrap.min.css';
```

#### Step 3: Use Framework Classes in Your Components

Now you can use the framework's classes within your Vue components. Here’s an example of a component styled with Bootstrap:

```html
<template>
    <div class="container text-center">
        <h1 class="display-4">{{ message }}</h1>
        <button class="btn btn-primary" @click="changeMessage">Change Message</button>
    </div>
</template>

<script>
export default {
    data() {
        return {
            message: 'Hello, Bootstrap with Vue!'
        };
    },
    methods: {
        changeMessage() {
            this.message = 'Message has been changed!';
        }
    }
};
</script>

<style scoped>
/* Additional scoped styles can be added here */
</style>
```

### Explanation of the Code

- **Bootstrap Classes**: The component uses Bootstrap classes like `container`, `text-center`, `display-4`, and `btn btn-primary` to style the elements. This allows for quick styling without writing custom CSS.
- **Responsive Design**: By using a CSS framework, your application can easily adapt to different screen sizes and devices.

## Conclusion

In this lesson, you learned how to style Vue components using scoped CSS to prevent style conflicts and maintain encapsulation. You also explored how to integrate CSS frameworks like Bootstrap into your Vue applications to enhance styling and create responsive designs quickly.

In the next lesson, we will dive deeper into advanced Vue.js features, including custom directives and mixins.