# Lesson 6: Working with Templates

In this lesson, we will explore Vue.js templates and the template syntax. We will also learn how to use directives like `v-if`, `v-else`, and `v-for` to control rendering and display data dynamically.

## Understanding Vue.js Templates and the Template Syntax

### What is a Vue.js Template?

Vue.js uses an HTML-based template syntax that allows you to declaratively bind the rendered DOM to the underlying component instance's data. All Vue templates are syntactically valid HTML, which means they can be parsed by standard browsers and HTML parsers.

### Template Syntax Basics

The most basic form of data binding in Vue.js is text interpolation using the double curly braces syntax (`{{ }}`). For example:

```html
<span>{{ message }}</span>
```

In this example, the content of the `<span>` will be replaced with the value of the `message` property from the Vue instance. Whenever `message` changes, the displayed content will automatically update.

### Using JavaScript Expressions

Vue templates support JavaScript expressions inside the curly braces. For example:

```html
<p>{{ number + 1 }}</p>
<p>{{ ok ? 'YES' : 'NO' }}</p>
```

These expressions are evaluated in the context of the Vue instance's data, allowing you to perform calculations and conditional logic directly in your templates.

## Using Directives: `v-if`, `v-else`, and `v-for`

### What are Directives?

Directives are special attributes in Vue.js that start with the `v-` prefix. They provide functionality to manipulate the DOM based on the data in your Vue instance. Some commonly used directives include `v-if`, `v-else`, and `v-for`.

### Conditional Rendering with `v-if` and `v-else`

The `v-if` directive is used to conditionally render elements based on a boolean expression. If the expression evaluates to `true`, the element is rendered; otherwise, it is not included in the DOM.

#### Example of `v-if`

```html
<div id="app">
  <p v-if="isAvailable">Item is available!</p>
  <p v-else>Item is not available.</p>
</div>

<script>
const app = new Vue({
  el: '#app',
  data: {
    isAvailable: true
  }
});
</script>
```

In this example, if `isAvailable` is `true`, the first paragraph will be displayed. If it is `false`, the second paragraph will be shown instead.

#### Using `v-else-if`

You can also use `v-else-if` to create multiple conditional branches:

```html
<div id="app">
  <p v-if="stock > 10">In stock</p>
  <p v-else-if="stock > 0">Very few left!</p>
  <p v-else>Out of stock</p>
</div>

<script>
const app = new Vue({
  el: '#app',
  data: {
    stock: 5
  }
});
</script>
```

In this example, the displayed message will depend on the value of `stock`.

### Looping with `v-for`

The `v-for` directive is used to render a list of items by iterating over an array. It allows you to create multiple elements based on the data in your Vue instance.

#### Example of `v-for`

```html
<div id="app">
  <ul>
    <li v-for="item in items" :key="item.id">{{ item.name }}</li>
  </ul>
</div>

<script>
const app = new Vue({
  el: '#app',
  data: {
    items: [
      { id: 1, name: 'Apple' },
      { id: 2, name: 'Banana' },
      { id: 3, name: 'Cherry' }
    ]
  }
});
</script>
```

In this example, the `v-for` directive iterates over the `items` array and creates a list item for each element. The `:key` attribute is used to provide a unique identifier for each item, which helps Vue optimize rendering.

## Conclusion

In this lesson, you learned about Vue.js templates and the template syntax, including how to use directives like `v-if`, `v-else`, and `v-for` to control rendering and display data dynamically. Understanding templates and directives is essential for creating interactive and responsive Vue applications.

In the next lesson, we will explore more about handling user input and events in Vue.js.