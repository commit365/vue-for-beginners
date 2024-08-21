# Lesson 8: Computed Properties and Watchers

In this lesson, we will explore computed properties and watchers in Vue.js. These features allow you to manage and respond to data changes effectively, enhancing the reactivity of your applications.

## Defining Computed Properties for Derived State

### What are Computed Properties?

Computed properties are special properties in Vue.js that are defined using the `computed` option. They allow you to create derived state based on the data in your Vue instance. Computed properties are cached based on their dependencies, meaning they will only re-evaluate when their reactive dependencies change.

### Example of Computed Properties

Here’s a simple example demonstrating how to use computed properties:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Computed Properties Example</title>
    <script src="https://cdn.jsdelivr.net/npm/vue@2"></script>
</head>
<body>
    <div id="app">
        <input v-model="base" placeholder="Enter a number">
        <p>Double: {{ double }}</p>
    </div>

    <script>
        const app = new Vue({
            el: '#app',
            data: {
                base: 0
            },
            computed: {
                double() {
                    return this.base * 2;
                }
            }
        });
    </script>
</body>
</html>
```

In this example, the `double` computed property calculates the double of the `base` value. As you type into the input field, the displayed double value updates automatically.

### Benefits of Computed Properties

- **Performance**: Computed properties are cached based on their dependencies. They are only recalculated when their dependencies change, making them more efficient than methods for derived state.
- **Readability**: Using computed properties can make your templates cleaner and more readable by encapsulating complex logic.

## Using Watchers to Respond to Data Changes

### What are Watchers?

Watchers are a way to perform asynchronous or expensive operations in response to changing data. They allow you to "watch" a specific data property and execute a function when that property changes.

### Example of Watchers

Here’s an example demonstrating how to use watchers:

```html
<div id="app">
    <input v-model="message" placeholder="Type something">
    <p>Reversed: {{ reversedMessage }}</p>
</div>

<script>
    const app = new Vue({
        el: '#app',
        data: {
            message: '',
            reversedMessage: ''
        },
        watch: {
            message(newValue) {
                this.reversedMessage = newValue.split('').reverse().join('');
            }
        }
    });
</script>
```

In this example, we have a watcher on the `message` property. Whenever `message` changes, the watcher executes the function, which reverses the string and updates `reversedMessage`.

### When to Use Watchers

- **Asynchronous Operations**: Use watchers when you need to perform asynchronous operations, such as API calls, in response to data changes.
- **Complex Logic**: If you have complex logic that doesn’t fit well into a computed property, a watcher can be a good solution.

### Example of an Asynchronous Watcher

Here’s an example of an asynchronous watcher that simulates an API call:

```html
<div id="app">
    <input v-model="query" placeholder="Search...">
    <p>Results: {{ results }}</p>
</div>

<script>
    const app = new Vue({
        el: '#app',
        data: {
            query: '',
            results: []
        },
        watch: {
            query: function(newQuery) {
                this.fetchResults(newQuery);
            }
        },
        methods: {
            fetchResults(query) {
                // Simulate an API call
                setTimeout(() => {
                    this.results = query ? [`Result for "${query}"`] : [];
                }, 500);
            }
        }
    });
</script>
```

In this example, the watcher on `query` triggers the `fetchResults` method whenever the user types in the input field, simulating an API call to fetch search results.

## Conclusion

In this lesson, you learned about computed properties and watchers in Vue.js. Computed properties allow you to define derived state efficiently, while watchers enable you to respond to data changes with custom logic. Understanding these concepts is essential for building dynamic and reactive Vue applications.

In the next lesson, we will explore how to create and use components in Vue.js.