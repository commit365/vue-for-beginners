# Lesson 13: Working with Forms

In this lesson, we will explore how to create and manage forms in Vue.js. We will cover handling form submissions and validating user input to ensure that the data collected from users is accurate and meets specific criteria.

## Creating Forms with Vue.js and Handling Form Submission

### Step 1: Creating a Simple Form

To create a form in Vue.js, you can use standard HTML form elements and bind them to your Vue instance using the `v-model` directive for two-way data binding. Here’s an example of a simple form that collects a user's name and email:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Vue.js Form Example</title>
    <script src="https://cdn.jsdelivr.net/npm/vue@2"></script>
</head>
<body>
    <div id="app">
        <form @submit.prevent="handleSubmit">
            <div>
                <label for="name">Name:</label>
                <input type="text" id="name" v-model="name" required>
            </div>
            <div>
                <label for="email">Email:</label>
                <input type="email" id="email" v-model="email" required>
            </div>
            <button type="submit">Submit</button>
        </form>
        <p v-if="submitted">Form submitted! Name: {{ name }}, Email: {{ email }}</p>
    </div>

    <script>
        const app = new Vue({
            el: '#app',
            data: {
                name: '',
                email: '',
                submitted: false
            },
            methods: {
                handleSubmit() {
                    this.submitted = true;
                    // Here you can handle form submission, e.g., send data to an API
                }
            }
        });
    </script>
</body>
</html>
```

### Explanation of the Code

- **Form Elements**: The form contains input fields for the user's name and email, each bound to the Vue instance's data properties using `v-model`.
- **Prevent Default Submission**: The `@submit.prevent` directive prevents the default form submission behavior, allowing you to handle the submission with a method instead.
- **Handling Submission**: The `handleSubmit` method sets the `submitted` property to true, which can be used to display a confirmation message.

### Step 2: Handling Form Submission

In the `handleSubmit` method, you can perform actions such as sending the collected data to an API or processing it further. For example, you might use the Fetch API or Axios to send the data to a server.

## Validating User Input in Forms

### Step 1: Basic Validation

You can perform basic validation using HTML attributes like `required`, `minlength`, and `pattern`. In the example above, both the name and email fields are marked as required. You can also add custom validation logic in your Vue component.

### Step 2: Custom Validation Logic

To implement custom validation, you can create computed properties or methods that validate the input data. Here’s an updated version of the form that includes custom validation for the email field:

```html
<div id="app">
    <form @submit.prevent="handleSubmit">
        <div>
            <label for="name">Name:</label>
            <input type="text" id="name" v-model="name" required>
        </div>
        <div>
            <label for="email">Email:</label>
            <input type="email" id="email" v-model="email" required>
            <span v-if="emailError" style="color: red;">Invalid email format</span>
        </div>
        <button type="submit" :disabled="emailError">Submit</button>
    </form>
    <p v-if="submitted">Form submitted! Name: {{ name }}, Email: {{ email }}</p>
</div>

<script>
    const app = new Vue({
        el: '#app',
        data: {
            name: '',
            email: '',
            submitted: false
        },
        computed: {
            emailError() {
                // Simple regex for email validation
                const re = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
                return !re.test(this.email) && this.email.length > 0;
            }
        },
        methods: {
            handleSubmit() {
                this.submitted = true;
                // Here you can handle form submission, e.g., send data to an API
            }
        }
    });
</script>
```

### Explanation of the Code

- **Computed Property for Validation**: The `emailError` computed property checks whether the email input matches a simple regex pattern for valid email formats. It returns `true` if the email is invalid and `false` otherwise.
- **Displaying Error Messages**: If the email is invalid, an error message is displayed below the email input field.
- **Disabling the Submit Button**: The submit button is disabled if there is an email error, preventing users from submitting the form with invalid data.

### Step 3: Advanced Validation Libraries

For more complex validation scenarios, you can use libraries like [VeeValidate](https://vee-validate.logaretm.com/) or [Vuelidate](https://vuelidate.js.org/). These libraries provide powerful validation features and can help you manage form validation more effectively.

## Conclusion

In this lesson, you learned how to create forms in Vue.js, handle form submissions, and validate user input. Understanding how to work with forms is essential for building interactive applications that collect user data.

In the next lesson, we will explore computed properties and watchers in Vue.js.