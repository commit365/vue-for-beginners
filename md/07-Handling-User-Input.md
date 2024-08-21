# Lesson 7: Handling User Input

In this lesson, we will learn how to handle user input in Vue.js. We will explore the `v-model` directive for two-way data binding and how to handle events using the `v-on` directive.

## Using `v-model` for Two-Way Data Binding

### What is `v-model`?

The `v-model` directive in Vue.js is used for creating two-way data bindings on form input elements. This means that when the user types in an input field, the data in the Vue instance is automatically updated, and vice versa. This makes it easy to manage form data and keep the UI in sync with the underlying model.

### Example of `v-model`

Here’s a simple example demonstrating the use of `v-model` with an input field:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>v-model Example</title>
    <script src="https://cdn.jsdelivr.net/npm/vue@2"></script>
</head>
<body>
    <div id="app">
        <input v-model="message" placeholder="Type something...">
        <p>You typed: {{ message }}</p>
    </div>

    <script>
        const app = new Vue({
            el: '#app',
            data: {
                message: ''
            }
        });
    </script>
</body>
</html>
```

In this example, the input field is bound to the `message` property in the Vue instance. As you type in the input field, the paragraph below it updates in real-time to reflect the current value of `message`.

### Using `v-model` with Different Input Types

The `v-model` directive can be used with various input types, including text, checkboxes, radio buttons, and select dropdowns.

#### Example with Checkboxes

```html
<div id="app">
    <label>
        <input type="checkbox" v-model="isChecked"> Check me
    </label>
    <p>Checkbox is: {{ isChecked ? 'Checked' : 'Unchecked' }}</p>
</div>

<script>
    const app = new Vue({
        el: '#app',
        data: {
            isChecked: false
        }
    });
</script>
```

In this example, the checkbox is bound to the `isChecked` property. The paragraph updates to show whether the checkbox is checked or not.

#### Example with Select Dropdown

```html
<div id="app">
    <select v-model="selectedFruit">
        <option disabled value="">Please select one</option>
        <option>Apple</option>
        <option>Banana</option>
        <option>Cherry</option>
    </select>
    <p>Selected fruit: {{ selectedFruit }}</p>
</div>

<script>
    const app = new Vue({
        el: '#app',
        data: {
            selectedFruit: ''
        }
    });
</script>
```

In this example, the selected value from the dropdown is bound to the `selectedFruit` property.

## Handling Events with `v-on`

### What is `v-on`?

The `v-on` directive is used to listen to DOM events and execute methods when those events are triggered. This allows you to respond to user interactions, such as clicks, key presses, and form submissions.

### Example of Using `v-on`

Here’s a simple example demonstrating the use of `v-on` to handle a button click event:

```html
<div id="app">
    <button v-on:click="showMessage">Click me</button>
    <p>{{ message }}</p>
</div>

<script>
    const app = new Vue({
        el: '#app',
        data: {
            message: 'Hello, Vue!'
        },
        methods: {
            showMessage() {
                this.message = 'Button was clicked!';
            }
        }
    });
</script>
```

In this example, when the button is clicked, the `showMessage` method is called, updating the `message` property.

### Shorthand for `v-on`

You can use the `@` symbol as a shorthand for `v-on`. The previous example can be rewritten as follows:

```html
<button @click="showMessage">Click me</button>
```

### Handling Multiple Events

You can also handle multiple events using `v-on`. For example, you can listen for both `mouseover` and `mouseout` events:

```html
<div id="app">
    <div @mouseover="hover = true" @mouseout="hover = false">
        Hover over me!
    </div>
    <p>{{ hover ? 'Mouse is over!' : 'Mouse is out!' }}</p>
</div>

<script>
    const app = new Vue({
        el: '#app',
        data: {
            hover: false
        }
    });
</script>
```

In this example, the paragraph updates based on whether the mouse is hovering over the div.

## Conclusion

In this lesson, you learned how to handle user input in Vue.js using the `v-model` directive for two-way data binding and the `v-on` directive for handling events. These features are essential for creating interactive and responsive applications.

In the next lesson, we will explore computed properties and watchers in Vue.js.
