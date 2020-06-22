# Introduction

## What internet is made of ? How to create internet content

Most of the internet you know is made of HTML. Hypertext Markup Language (HTML) is just a way to describe to your browser how you want your content organized and displayed.

### What does HTML look like

```html
<!doctype html>
<html lang=en>
  <head>
    <meta charset=utf-8>
    <title>The title of my page, displayed in the tab of my browser</title>
  </head>
  <body>
    <h1>Hello World !</h1>
    <p>This is displayed in the window of my browser</p>
  </body>
</html>
```

Please, try this out :

- open a text editor and create a new file named index.html

> (want a new text editor ? try [Sublime text](https://www.sublimetext.com/3) or [VS code](https://code.visualstudio.com/))

- copy/paste the content above
- open the file you created in your browser (just double click on it)

Well It's a start but as you can see, HTML can't do everything, there're 2 things it can't do : Design and Dynamic content.

### Design

For this we will use CSS (Cascading Style Sheets). CSS is just a way to 'paint' the content described by HTML.

Let's try to put the text in red and change the size of the title:

```css
#red {
    color: red;
  }
h1 {
    font-size: 16px;
}
```

> `#red` is the things we want to affect (here, all what's in `<p id="red"></p>`), `color` is the property of `p` we want to change and `red` is how we want to change it.  

<details>
  <summary>Result</summary>

  ```html
  <!doctype html>
  <html lang=en>
    <head>
      <meta charset=utf-8>
      <title>The title of my page, displayed in the tab of my browser</title>
      <style>
      #red {
        color: red;
      }
      h1 {
        font-size: 16px;
      }
      </style>
    </head>
    <body>
      <h1>Hello World !</h1>
      <p id="red">This is displayed in the window of my browser</p>
    </body>
  </html>
  ```

</details>

### Dynamic content

Javascript(JS) is programming language, that allow us to change the html page once loaded. With JS we can interact with the user; create, edit or delete the content of our page and communicate with servers.

So imagine we want something that change over time or over which user is using it, like displaying the current date. We can do it with Javascript

```html
<p id="date"></p>
<button type="button" onclick="displayDate()">Try it</button>

<script>
function displayDate() {
  document.getElementById("date").innerHTML = Date();
}
</script>
```

> Here we added a new date 'container' which is empty and a button. Then we use JS to fill it with the current date when the user click on a button.

<details>
  <summary>Result</summary>

  ```html
  <!doctype html>
  <html lang=en>
    <head>
      <meta charset=utf-8>
      <title>The title of my page, displayed in the tab of my browser</title>
      <style>
      #red {
        color: red;
      }
      h1 {
        font-size: 16px;
      }
      </style>
    </head>
    <body>
      <h1>Hello World !</h1>
      <p id="red">This is displayed in the window of my browser</p>
      <p id="date"></p>
      <button type="button" onclick="displayDate()">Try it</button>

      <script>
      function displayDate() {
        document.getElementById("date").innerHTML = Date();
      }
      </script>
    </body>
  </html>
  ```

</details>

> HTML, CSS and JS can do a lot, if you want to learn more about it you can go [there](https://www.w3schools.com/default.asp).

Most of the need we have for a new website are the same, so instead of reinventing the wheel everytime, we can use frameworks.

## The Vue.js Framework

[Vue.js](https://vuejs.org/) is one of the 3 most popular Javascript Frameworks. the other 2 are React.js(Facebook) and Angular.js(Google). Vue.js is more lightweight and focus mostly on single page app (eg. infinite scroll pages).

## The Bootstrap Framework

[Bootstrap](https://getbootstrap.com/docs/4.5/getting-started/introduction/) is a CSS framework, that allow us to have a basic, not-too-ugly design quickly.

# Course list

## Setup

Now that we have efficients tools, let's try to make something with them. We will try to create a list of available courses in Vue.js.

We want to add Vue.js and Bootstrap :

```html
  <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.0/css/bootstrap.min.css" integrity="sha384-9aIt2nRpC12Uk9gS9baDl411NQApFmC26EwAOH8WgZl5MYYxFfc+NcPb1dKGj7Sk" crossorigin="anonymous">
  <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
```

Here's an example content :

```html
<div class="container">
  <h1>Course List</h1>
  <ul class="list-group">
    <li class="list-group-item">Math</li>
    <li class="list-group-item">English</li>
    <li class="list-group-item">French</li>
    <li class="list-group-item">History</li>
    <li class="list-group-item">Programming</li>
  </ul>
</div>
```

> let's strip our app of the JS and CSS bits while we are here:

<details>
  <summary>Result</summary>

  ```html
  <!doctype html>
  <html lang=en>
    <head>
      <meta charset=utf-8>
      <title>The title of my page, displayed in the tab of my browser</title>
      <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.0/css/bootstrap.min.css" integrity="sha384-9aIt2nRpC12Uk9gS9baDl411NQApFmC26EwAOH8WgZl5MYYxFfc+NcPb1dKGj7Sk" crossorigin="anonymous">
      <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
    </head>
    <body>
      <div class="container">
        <h1>Course List</h1>
        <ul class="list-group">
          <li class="list-group-item">Math</li>
          <li class="list-group-item">English</li>
          <li class="list-group-item">French</li>
          <li class="list-group-item">History</li>
          <li class="list-group-item">Programming</li>
        </ul>
      </div>
    </body>
  </html>
  ```
</details>

Ok, so here we should see Bootstrap working :

- separation between items
- centered table
- round edges

## The Vue App

Vue is using Javascript, so let's initiate vue in JS:

```html
<script>
var app = new Vue({
  el: '#app',
  data: {
    title: 'Hello Vue !'
  }
})
</script>
```

Vue is launching for a specific html container, here we have:

- `el: '#app',` meaning it will launch in the container with the id `app`.
- `data`, we will put the data that might change here.
- `title: 'Hello Vue !'`, we will use this as a title.

Let's add the `app` id to our div:

```html
<div class="container" id="app">
```

let's use Vue to display title instead of html:

```html
<h1>{{ title }}</h1>
```

<details>
  <summary>Result</summary>

  ```html
  <!doctype html>
  <html lang=en>
    <head>
      <meta charset=utf-8>
      <title>The title of my page, displayed in the tab of my browser</title>
      <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.0/css/bootstrap.min.css" integrity="sha384-9aIt2nRpC12Uk9gS9baDl411NQApFmC26EwAOH8WgZl5MYYxFfc+NcPb1dKGj7Sk" crossorigin="anonymous">
      <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
    </head>
    <body>
      <div class="container" id="app">
        <h1>{{ title }}</h1>
        <ul class="list-group">
          <li class="list-group-item">Math</li>
          <li class="list-group-item">English</li>
          <li class="list-group-item">French</li>
          <li class="list-group-item">History</li>
          <li class="list-group-item">Programming</li>
        </ul>
      </div>
      <script>
      var app = new Vue({
        el: '#app',
        data: {
          title: 'Hello Vue !'
        }
      })
      </script>
    </body>
  </html>
  ```

</details>

So here we should have `Hello Vue !` display at the top of our page, if so Vue is working !

Ok, but the school want to provide more courses, so let's add our courses with vue.

```html
<script>
var app = new Vue({
  el: '#app',
  data: {
    title: 'Hello Vue !',
    courses: [
      "Math",
      "English",
      "French",
      "History",
      "Programming",
      "Science",
    ]
  }
})
</script>
```

But what if the school have 100 courses ? Most developers are [lazy](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself) and Vue will help us for this too :

```html
<ul class="list-group">
  <li v-for="course in courses" class="list-group-item">
    {{ course }}
  </li>
</ul>
```

<details>
  <summary>Result</summary>

  ```html
  <!doctype html>
  <html lang=en>
    <head>
      <meta charset=utf-8>
      <title>The title of my page, displayed in the tab of my browser</title>
      <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.0/css/bootstrap.min.css" integrity="sha384-9aIt2nRpC12Uk9gS9baDl411NQApFmC26EwAOH8WgZl5MYYxFfc+NcPb1dKGj7Sk" crossorigin="anonymous">
      <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
    </head>
    <body>
      <div class="container" id="app">
        <h1>{{ title }}</h1>
        <ul class="list-group">
          <li v-for="course in courses" class="list-group-item">
            {{ course }}
          </li>
        </ul>
      </div>
      <script>
        var app = new Vue({
          el: '#app',
          data: {
            title: 'Hello Vue !',
            courses: [
              "Math",
              "English",
              "French",
              "History",
              "Programming",
              "Science",
            ]
          }
        })
      </script>
    </body>
  </html>
  ```

</details>