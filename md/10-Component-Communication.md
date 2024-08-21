# Lesson 10: Component Communication

In this lesson, we will explore how components communicate with each other in Vue.js. We will learn about using props to pass data from parent components to child components and how to use events to communicate from child components back to parent components.

## Understanding Props for Passing Data to Child Components

### What are Props?

Props (short for properties) are a mechanism in Vue.js for passing data from a parent component to a child component. Props allow you to create reusable components that can receive dynamic data and render accordingly.

### Defining Props in Child Components

To define props in a child component, you can specify them in the `props` option of the component. Here’s an example of a child component that accepts a `message` prop:

```javascript
Vue.component('child-component', {
    props: ['message'],
    template: `<p>{{ message }}</p>`
});
```

### Passing Props from Parent to Child

In the parent component, you can pass data to the child component using the prop binding syntax. Here’s how to do it:

```html
<div id="app">
    <child-component message="Hello from Parent!"></child-component>
</div>

<script>
    Vue.component('child-component', {
        props: ['message'],
        template: `<p>{{ message }}</p>`
    });

    const app = new Vue({
        el: '#app'
    });
</script>
```

In this example, the parent component passes the string `"Hello from Parent!"` to the `child-component` through the `message` prop. The child component then renders this message.

### Example of Using Props with Dynamic Data

You can also pass dynamic data to child components. Here’s an example where the parent component has a data property:

```html
<div id="app">
    <input v-model="parentMessage" placeholder="Type a message">
    <child-component :message="parentMessage"></child-component>
</div>

<script>
    const app = new Vue({
        el: '#app',
        data: {
            parentMessage: 'Hello from Parent!'
        },
        components: {
            'child-component': {
                props: ['message'],
                template: `<p>{{ message }}</p>`
            }
        }
    });
</script>
```

In this example, the child component receives the value of `parentMessage` as a prop. As you type in the input field, the child component updates automatically to reflect the new message.

## Using Events to Communicate from Child to Parent Components

### What are Events?

Events in Vue.js allow child components to communicate with their parent components. When a child component needs to send data or notify the parent of an action, it can emit an event.

### Emitting Events from Child Components

To emit an event from a child component, you can use the `$emit` method. Here’s an example of a child component that emits an event when a button is clicked:

```javascript
Vue.component('child-component', {
    template: `
        <div>
            <button @click="sendMessage">Send Message to Parent</button>
        </div>
    `,
    methods: {
        sendMessage() {
            this.$emit('message-sent', 'Hello from Child!');
        }
    }
});
```

### Listening for Events in Parent Components

In the parent component, you can listen for the emitted event using the `v-on` directive (or the shorthand `@`). Here’s how to do it:

```html
<div id="app">
    <child-component @message-sent="receiveMessage"></child-component>
    <p>{{ receivedMessage }}</p>
</div>

<script>
    const app = new Vue({
        el: '#app',
        data: {
            receivedMessage: ''
        },
        methods: {
            receiveMessage(message) {
                this.receivedMessage = message;
            }
        },
        components: {
            'child-component': {
                template: `
                    <div>
                        <button @click="sendMessage">Send Message to Parent</button>
                    </div>
                `,
                methods: {
                    sendMessage() {
                        this.$emit('message-sent', 'Hello from Child!');
                    }
                }
            }
        }
    });
</script>
```

In this example, the parent component listens for the `message-sent` event emitted by the child component. When the event is received, the `receiveMessage` method is called, updating the `receivedMessage` data property.

### Summary of Component Communication

- **Props**: Used to pass data from parent to child components. Define props in the child component and pass data using the prop binding syntax.
- **Events**: Used to communicate from child to parent components. Emit events from the child component using `$emit` and listen for those events in the parent component.

## Conclusion

In this lesson, you learned about component communication in Vue.js. You explored how to use props to pass data to child components and how to use events to communicate from child components back to parent components. Understanding component communication is essential for building interactive and dynamic Vue applications.

In the next lesson, we will explore Vue Router and how to manage navigation in your Vue applications. Happy coding!
