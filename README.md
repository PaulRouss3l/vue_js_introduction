# Introduction

This presentation is a support for the vue.js conference at the **language-learning-and-innovation** hackathon.

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

> (need a text editor ? try [Sublime text](https://www.sublimetext.com/3) or [VS code](https://code.visualstudio.com/))

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

Javascript(JS) is a programming language, that allow us to change the html page once loaded. With JS we can interact with the user; create, edit or delete the content of our page and communicate with servers.

So imagine we want something that change over time or with user inputs, like displaying the current date. We can do it with Javascript :

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

# Course List

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

## The Vue Directives

Ok, but maybe we want to have more info on the courses provided, let's change the data we have a bit to include a description :

```html
<script>
var app = new Vue({
  el: '#app',
  data: {
    title: 'Hello Vue !',
    courses: [
      {title: "Math", description: "Math course for beginner"},
      {title: "English", description: "English lesson to improve your Grammar"},
      {title: "French", description: "Learn French through history"},
      {title: "Programming", description: "Learn programming from scratch"},
      {title: "History", description: "Medieval period in europe"},
      {title: "Science", description: "Learn how to make soap"},
    ],
    description: '',
  }
})
</script>
```

We have to change `{{ course }}` into `{{ course.title }}` to help vue js understand what to print.
We also want to add a container to display the description when the course is clicked.

```html
<div class="container" id="app">
  <h1>{{ title }}</h1>
  <ul class="list-group">
    <li v-for="course in courses" class="list-group-item">
      {{ course.title }}
    </li>
  </ul>
  <div id="description" class="card card-body mt-3">{{ description }}</div>
</div>
```

Now we have to detect click on courses to put its description, in the container.
`<div id="description" class="card card-body mt-3">{{ description }}</div>`

We will use 'v-on' for that. v-on is a [directive](https://012.vuejs.org/guide/directives.html).
v-on is a way to catch events. The event we need is when the user click on the element, in vue js it's : `v-on:click`.
`<li v-for="course in courses" class="list-group-item" v-on:click="displayDescription">`

Once we got the click event, we have to remember which element have been clicked on, for this we will use another directive : `v-bind:id`, to add an id to the container.
From :

```html
<li v-for="course in courses" class="list-group-item" v-on:click="displayDescription" v-bind:id="course.title">
```

It will generate :

```html
<li id="Math" class="list-group-item">
  Math
</li><li id="English" class="list-group-item">
  English
</li><li id="French" class="list-group-item">
  French
</li><li id="Programming" class="list-group-item">
  Programming
</li><li id="History" class="list-group-item">
  History
</li><li id="Science" class="list-group-item">
  Science
</li>
```

So with that code, when the user click on a course, it will call this function : `displayDescription`
let's code this function :

```html
<script>
var app = new Vue({
  el: '#app',
  data: {...},
  methods: {
    displayDescription: function (event) {
      this.description = event.target.id;
    }
  }
})
</script>
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
          <li v-for="course in courses" class="list-group-item" :id="course.title" v-on:click="displayDescription">
            {{ course.title }}
          </li>
        </ul>
        <div id="description" class="card card-body mt-3">{{ description }}</div>
      </div>

      <script>
        var app = new Vue({
          el: '#app',
          data: {
            title: 'Hello Vue !',
            courses: [
              {title: "Math", description: "Math course for beginner"},
              {title: "English", description: "English lesson to improve your Grammar"},
              {title: "French", description: "Learn French through history"},
              {title: "Programming", description: "Learn programming from scratch"},
              {title: "History", description: "Medieval period in europe"},
              {title: "Science", description: "Learn how to make soap"},
            ],
            description: '',
          },
          methods: {
            displayDescription: function (event) {
              this.description = event.target.id;
            }
          }
        })
      </script>
    </body>
  </html>
  ```

</details>

What does this code ? When you click a course, The course name is displayed behind the list.
Well we want the description, not the name ! Let's tweak our function a bit :


```html
<script>
var app = new Vue({
  el: '#app',
  data: {
    title: 'Hello Vue !',
    courses: [
      {title: "Math", description: "Math course for beginner"},
      {title: "English", description: "English lesson to improve your Grammar"},
      {title: "French", description: "Learn French through history"},
      {title: "Programming", description: "Learn programming from scratch"},
      {title: "History", description: "Medieval period in europe"},
      {title: "Science", description: "Learn how to make soap"},
    ],
    description: '',
  },
  methods: {
    displayDescription: function (event) {
      // this is will go through all the courses we have, and find the ones with the same title
      clicked_course = this.courses.find(course => course.title == event.target.id);
      // clicked_course has a title and a description, here we only want the description 
      this.description = clicked_course.description;
    }
  }
})
</script>
```

Now it's display the description !

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
          <li v-for="course in courses" class="list-group-item" :id="course.title" v-on:click="displayDescription">
            {{ course.title }}
          </li>
        </ul>
        <div id="description" class="card card-body mt-3">{{ description }}</div>
      </div>

      <script>
        var app = new Vue({
          el: '#app',
          data: {
            title: 'Hello Vue !',
            courses: [
              {title: "Math", description: "Math course for beginner"},
              {title: "English", description: "English lesson to improve your Grammar"},
              {title: "French", description: "Learn French through history"},
              {title: "Programming", description: "Learn programming from scratch"},
              {title: "History", description: "Medieval period in europe"},
              {title: "Science", description: "Learn how to make soap"},
            ],
            description: '',
          },
          methods: {
            displayDescription: function (event) {
              // this is will go through all the courses we have, and find the ones with the same title
              clicked_course = this.courses.find(course => course.title == event.target.id);
              // clicked_course has a title and a description, here we only want the description 
              this.description = clicked_course.description;
            }
          }
        })
      </script>
    </body>
  </html>
  ```

</details>

## The Vue Components

Let's say, it's not enough,
the school want to provide different courses for each subject :

```javascript
  data: {
    title: 'McSchool University inc.',
    courses: [
      { subject: 'Math', courses: [
        { title: 'Math101', description: 'Basic Algebra' },
        { title: 'Math102', description: 'Complex Algebra' },
        { title: 'Math103', description: 'Very Difficult Algebra' },
      ]},
      { subject: 'English', courses: [
        { title: 'English101', description: 'The lyrics of a pop song' },
        { title: 'English102', description: 'The etymology behind pokemons' },
        { title: 'English103', description: 'Why is there 3 "Bilbo the hobbit" films although there\'s only one book?' },
      ]},
      { subject: 'French', courses: [
        { title: 'French101', description: 'French slang' },
        { title: 'French102', description: 'How to ask for food in a bakery' },
        { title: 'French103', description: 'Mais ou est donc passé Ornicar ?' },
      ]},
    ],
    description: '',
  },
```

As stated earlier, we are lazy and don't want to do the same thing twice, we let the computer(or Vue.js) do it for us. Vue.js has a thing that will help us : [The Components](https://vuejs.org/v2/guide/components.html).

We will transform the app we had in a Component. This way we will use this component for each subject.

### Creating a component

to create a component  we need :
1. an html template, the html content of our component

```javascript
let template = `<div>
  <h2>{{ title }}</h2>
  <ul class="list-group">
    <li v-for="course in courses" class="list-group-item" :id="course.title" v-on:click="displayDescription">
      {{ course.title }}
    </li>
  </ul>
  <div id="description" class="card card-body mt-3">{{ description }}</div>
</div>`;
```

2. The Vue component :

```javascript
Vue.component('course-displayer', {
  data: function () {
    return {
      'description': ''
    }
  },
  props: ['title', 'courses'],
  template: template,
  methods: {
    displayDescription: function (event) {
      clicked_course = this.courses.find(course => course.title == event.target.id);
      this.description = clicked_course.title + ': ' + clicked_course.description;
    }
  }
});
```

So what's new ?
- we have `'course-displayer'` which is the name of the component.
- `data` has become a function but is the same
- `props: ['title', 'courses']` this is telling vue we expect 2 parameters a `title` and a `courses`
- `template` we use the variable we have defined earlier
- the `methods` part didn't changed too much

3. The Vue app

```javascript
var app = new Vue({
  el: '#app',
  data: {
    title: 'McSchool University inc',
    subjects: [
      { subject: 'Math', courses: [
        { title: 'Math101', description: 'Basic Algebra' },
        { title: 'Math102', description: 'Complex Algebra' },
        { title: 'Math103', description: 'Very Difficult Algebra' },
      ]},
      { subject: 'English', courses: [
        { title: 'English101', description: 'The lyrics of a pop song' },
        { title: 'English102', description: 'The etymology behind pokemons' },
        { title: 'English103', description: 'Why is there 3 "Bilbo the hobbit" films although there\'s only one book?' },
      ]},
      { subject: 'French', courses: [
        { title: 'French101', description: 'French slang' },
        { title: 'French102', description: 'How to ask for food in a bakery' },
        { title: 'French103', description: 'Mais ou est donc passé Ornicar ?' },
      ]},
    ],
  },
});
```

4. The usage of this component

```html
<div class="container" id="app">
  <course-displayer v-for="subject in subjects" v-bind:title='subject.subject' v-bind:courses='subject.courses'></course-displayer>
</div>
```

Let's break this down :
We still have our app container

```html
  <div class="container" id="app">
```

Then we have `<course-displayer>`, this is a new container, it represent our new component !

After there's this : `v-for="subject in subjects"`. That means vue is going to take what's in `subjects`from the `data` section and loop over it, creating a new component for each entry, putting the entry data in `subject`

Remember the `props` we had in the component ? They are here :

```html
  v-bind:title='subject.subject' v-bind:courses='subject.courses'
```

So for each component, we will give the `subject` and the `courses` from `subject` to the component.

Let's put it back together :

1. `<course-displayer>` is calling the `course-displayer` component
2. `v-for="subject in subjects"` the `subjects` data comes from the app.

```javascript
var app = new Vue({
  el: '#app',
  data: {
    subjects: [...]
  });
```

3. We will have one component per entry in `subjects`
4. `v-bind:title='subject.subject' v-bind:courses='subject.courses'` Thoses components will have:
  - a `title` prop that comes from `subject.subject`
  - a `courses` prop that comes from `subject.courses`

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
        <course-displayer v-for="subject in subjects" v-bind:title='subject.subject' v-bind:courses='subject.courses'></course-displayer>
      </div>

      <script>
        let template = `<div>
                        <h2>{{ title }}</h2>
                        <ul class="list-group">
                          <li v-for="course in courses" class="list-group-item" :id="course.title" v-on:click="displayDescription">
                            {{ course.title }}
                          </li>
                        </ul>
                        <div id="description" class="card card-body mt-3">{{ description }}</div>
                      </div>`;
        Vue.component('course-displayer', {
          data: function () {
            return {
              'description': ''
            }
          },
          props: ['title', 'courses'],
          template: template,
          methods: {
            displayDescription: function (event) {
              clicked_course = this.courses.find(course => course.title == event.target.id);
              this.description = clicked_course.title + ': ' + clicked_course.description;
            }
          }
        });

        var app = new Vue({
          el: '#app',
          data: {
            title: 'McSchool University inc',
            subjects: [
              { subject: 'Math', courses: [
                { title: 'Math101', description: 'Basic Algebra' },
                { title: 'Math102', description: 'Complex Algebra' },
                { title: 'Math103', description: 'Very Difficult Algebra' },
              ]},
              { subject: 'English', courses: [
                { title: 'English101', description: 'The lyrics of a pop song' },
                { title: 'English102', description: 'The etymology behind pokemons' },
                { title: 'English103', description: 'Why is there 3 "Bilbo the hobbit" films although there\'s only one book?' },
              ]},
              { subject: 'French', courses: [
                { title: 'French101', description: 'French slang' },
                { title: 'French102', description: 'How to ask for food in a bakery' },
                { title: 'French103', description: 'Mais ou est donc passé Ornicar ?' },
              ]},
            ],
          },
          methods: {
            displayDescription: function (event) {
              clicked_course = this.courses.find(course => course.title == event.target.id);
              this.description = clicked_course.description;
            }
          }
        });

      </script>
    </body>
  </html>
  ```

</details>

Thanks for Reading

# Questions
