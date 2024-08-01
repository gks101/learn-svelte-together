---
marp: true
theme: default
---

# 000 The Evolution of Reactivity: From Static Pages to Svelte

<!-- 
- Welcome everyone to our presentation on "The Evolution of Reactivity: From Static Pages to Svelte"
- We'll be exploring how web development has progressed over the years, focusing on how we handle dynamic content and user interactions
-->

---

## 1. Static HTML Pages (Early 1990s)

- Pages were entirely static
- Content was hard-coded in HTML

```html
<html>
  <body>
    <h1>Welcome to my website</h1>
    <p>This content never changes without a full page reload.</p>
  </body> 
</html>
```

- Changes required manually updating the HTML file and re-uploading

<!-- 
- Let's start at the beginning with static HTML pages
- In the early days of the web, pages were completely static
- All content was hard-coded in HTML
- To make any changes, developers had to manually edit the HTML file and re-upload it to the server
- This was time-consuming and inflexible for dynamic content
-->

---

## 2. Server-Side Scripting (Mid 1990s)

- Languages like Perl and PHP introduced dynamic content generation on the server

```php
<?php
  $current_time = date("H:i:s");
  echo "<p>The current time is: $current_time</p>";
?>
```

- Still required page reloads for updates

<!-- 
- The mid-90s saw the introduction of server-side scripting languages like Perl and PHP
- These allowed for dynamic content generation on the server
- The example shows how PHP could be used to display the current time
- While this was an improvement, it still required full page reloads for updates
-->

---

## 3. Early Client-Side Scripting (Late 1990s)

- Introduction of JavaScript in 1995
- Primarily used for simple tasks like form validation

```html
<script>
function validateForm() {
  var x = document.forms["myForm"]["fname"].value;
  if (x == "") {
    alert("Name must be filled out");
    return false;
  }
}
</script>
```

<!-- 
- JavaScript was introduced in 1995, bringing interactivity to the client-side
- Initially, it was primarily used for simple tasks like form validation
- The example shows a basic form validation function
- This was the beginning of more responsive web pages, but still limited in scope
-->

---

## 4. The AJAX Era (Early 2000s)

- Enabled asynchronous data fetching without full page reloads

```javascript
var xhr = new XMLHttpRequest();
xhr.onreadystatechange = function() {
  if (xhr.readyState == 4 && xhr.status == 200) {
    document.getElementById("result").innerHTML = xhr.responseText;
  }
};
xhr.open("GET", "data.php", true);
xhr.send();
```

<!-- 
- AJAX (Asynchronous JavaScript and XML) was a game-changer
- It allowed parts of a web page to be updated without reloading the entire page
- The example shows how to make an asynchronous request using XMLHttpRequest
- This led to more dynamic and responsive web applications
-->

---

## 5. The jQuery Era (2006)

- Simplified DOM manipulation and AJAX requests

``` javascript
window.onload = function() {
    var buttons = document.getElementsByTagName("button");
    for (var i = 0; i < buttons.length; i++) {
        buttons[i].onclick = function() {
            var paragraphs = document.getElementsByTagName("p");
            for (var j = 0; j < paragraphs.length; j++) {
                paragraphs[j].style.display = "none";
            }
        };
    }
};
```
```javascript
$(document).ready(function() {
    $("button").click(function() {
        $("p").hide();
    });
});
```

<!-- 
- jQuery simplified DOM manipulation and AJAX requests
- The example compares vanilla JavaScript with jQuery for hiding paragraphs
- jQuery's syntax was much more concise and easier to use
- It became extremely popular, powering a large percentage of websites
-->

---

## 6. The Rise of MVC Frameworks (2010)

- Frameworks like Ruby on Rails, ASP.NET MVC, AngularJS, Django ...
- Introduced more structured approaches to building web applications

```html
<!-- View -->
<div ng-app="myApp" ng-controller="MyController">
  <input ng-model="name">
  <p>Hello, {{name}}!</p>
</div>

<script>
var app = angular.module('myApp', []);
// Controller
app.controller('MyController', function($scope) {
  $scope.name = 'World';  // Model
});
</script>
```

<!-- 
- Around 2010, we saw the rise of MVC (Model-View-Controller) frameworks
- Examples include Ruby on Rails, ASP.NET MVC, and AngularJS
- These frameworks introduced more structure to web application development
- The example shows a simple AngularJS application with two-way data binding
-->

---

## 7. The React Revolution (2013)

- Component-based architecture
- Virtual DOM for efficient updates

```jsx
import React, { useState } from 'react';

function App() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>
        Increment
      </button>
    </div>
  );
}
export default App;
```

<!-- 
- React introduced a component-based architecture
- It used a Virtual DOM for efficient updates
-->

---

## 8. Vue.js: Simplifying Reactivity (2014)

- Reactive data binding
- Template-based components
- Easier learning curve compared to React

```vue
<template>
  <div>{{ message }}</div>
</template>

<script>
export default {
  data() {
    return {
      message: 'Hello Vue!'
    }
  }
}
</script>
```

<!-- 
- Vue.js aimed to simplify reactive programming
- It features reactive data binding and template-based components
- Vue is often considered easier to learn than React
- The example demonstrates a simple Vue component
-->

---

## 9. Svelte: Compile-time Reactivity (2016)

- Shifts reactivity to compile-time
- No virtual DOM
- Less boilerplate, more intuitive syntax

```js
<script>
  let count = $state(0);

  function increment() {
    count += 1;
  }
</script>

<button onclick={increment}>
	clicks: {count}
</button>
```

<!-- 
- Svelte introduced a new approach: shifting reactivity to compile-time
- It doesn't use a virtual DOM, which can lead to better performance
- Svelte has less boilerplate and a more intuitive syntax
- The example shows a simple counter component in Svelte
-->

---

# Thank You!

Any questions?

<!-- 
- Summarize the journey we've taken from static HTML to modern reactive frameworks
- Emphasize how each step brought more dynamism and better user experiences
- Open the floor for questions
-->