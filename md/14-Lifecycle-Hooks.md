# Lesson 14: Lifecycle Hooks

In this lesson, we will explore lifecycle hooks in Vue.js. Lifecycle hooks allow you to run code at specific stages of a Vue component's lifecycle, enabling you to manage side effects and perform actions when components are created, updated, or destroyed.

## Understanding the Different Lifecycle Hooks in Vue.js

### What are Lifecycle Hooks?

Lifecycle hooks are special methods in a Vue component that are called at different stages of the component's lifecycle. These stages include creation, mounting, updating, and destruction. Understanding these hooks is essential for managing your application's behavior effectively.

### Common Lifecycle Hooks

Here are some of the most commonly used lifecycle hooks in Vue.js:

1. **`beforeCreate`**: Called after the instance is initialized but before data observation and event/watcher setup. This is typically used for initializing properties.

2. **`created`**: Called after the instance is created. At this point, you can access reactive data and methods. This is a good place to perform initial data fetching or setup.

3. **`beforeMount`**: Called right before the mounting begins. The `render` function is not yet called at this stage.

4. **`mounted`**: Called after the instance is mounted to the DOM. This is where you can perform DOM manipulations or start asynchronous tasks like API calls.

5. **`beforeUpdate`**: Called when data changes, before the DOM is re-rendered. This is useful for performing actions before the component updates.

6. **`updated`**: Called after the DOM has been re-rendered due to data changes. You can use this to perform actions after the component has updated.

7. **`beforeDestroy`**: Called right before the instance is destroyed. This is where you can perform cleanup tasks, such as removing event listeners.

8. **`destroyed`**: Called after the instance is destroyed. At this point, the component is no longer in the DOM.

### Example of Lifecycle Hooks

Here’s an example that demonstrates the use of various lifecycle hooks:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Vue Lifecycle Hooks Example</title>
    <script src="https://cdn.jsdelivr.net/npm/vue@2"></script>
</head>
<body>
    <div id="app">
        <h1>{{ message }}</h1>
        <button @click="changeMessage">Change Message</button>
    </div>

    <script>
        const app = new Vue({
            el: '#app',
            data: {
                message: 'Hello, Vue!'
            },
            beforeCreate() {
                console.log('Before Create: Instance is being created.');
            },
            created() {
                console.log('Created: Instance has been created.');
            },
            beforeMount() {
                console.log('Before Mount: Instance is about to be mounted.');
            },
            mounted() {
                console.log('Mounted: Instance has been mounted to the DOM.');
            },
            beforeUpdate() {
                console.log('Before Update: Data is about to change.');
            },
            updated() {
                console.log('Updated: Data has changed and DOM has been re-rendered.');
            },
            beforeDestroy() {
                console.log('Before Destroy: Instance is about to be destroyed.');
            },
            destroyed() {
                console.log('Destroyed: Instance has been destroyed.');
            },
            methods: {
                changeMessage() {
                    this.message = 'Message has been changed!';
                }
            }
        });
    </script>
</body>
</html>
```

### Explanation of the Code

- Each lifecycle hook logs a message to the console, allowing you to see the order in which they are called.
- The `changeMessage` method updates the `message` property, triggering the `beforeUpdate` and `updated` hooks.

## Using Lifecycle Hooks for Side Effects

### Performing Side Effects

Lifecycle hooks are often used to perform side effects, such as fetching data, setting up subscriptions, or interacting with third-party libraries. Here are some common use cases:

1. **Fetching Data**: You can use the `mounted` hook to fetch data from an API when the component is first rendered.

   ```javascript
   mounted() {
       fetch('https://api.example.com/data')
           .then(response => response.json())
           .then(data => {
               this.data = data;
           });
   }
   ```

2. **Setting Up Event Listeners**: You can set up event listeners in the `mounted` hook and clean them up in the `beforeDestroy` hook.

   ```javascript
   mounted() {
       window.addEventListener('resize', this.handleResize);
   },
   beforeDestroy() {
       window.removeEventListener('resize', this.handleResize);
   },
   methods: {
       handleResize() {
           console.log('Window resized!');
       }
   }
   ```

3. **Interacting with Third-Party Libraries**: If you are using a third-party library that requires initialization, you can do so in the `mounted` hook.

   ```javascript
   mounted() {
       this.chart = new Chart(this.$refs.canvas, {
           // Chart configuration
       });
   },
   beforeDestroy() {
       this.chart.destroy(); // Clean up the chart instance
   }
   ```

## Conclusion

In this lesson, you learned about lifecycle hooks in Vue.js and how they allow you to run code at specific stages of a component's lifecycle. You also explored how to use lifecycle hooks for side effects, such as fetching data, setting up event listeners, and interacting with third-party libraries.

Understanding lifecycle hooks is crucial for building efficient and responsive Vue applications. In the next lesson, we will explore custom directives in Vue.js.