## Part 4 Outline

## Exercise:
Your friend needs some help building their webpage.  They have the basic structure set up, but they need your help wiring IDs and classes to their appropriate elements on the page. Look through the ```<style></style>``` section at the top and then apply the various IDs and classes appropriately to the elements in the ```<body>```.

```
<!DOCTYPE html>
<html>
<head>
    <title>My Cool Homepage</title>
    <style>

        body{
            margin: 0;
            padding: 0;
        }

        #title-area{
            padding: 15px;
            margin-bottom: 15px;
            width: 100%;
            height: 50px;
            text-align: center;
        }

        #nav{
            display: flex;
            justify-content: center;
        }

        #nav h1{
            color: red;
            animation-name: animateLogo;
            animation-duration: 10s;
            animation-iteration-count: infinite;
            font-family: sans-serif;
        }

        .navLink{
            display: inline-block;
            width: 150px;
            text-align: center;
        }

        .navLink > a{
            text-decoration: none;
            color: #000;
        }

        #blog{
            width: 70%;
            margin: 0 auto;
        }

        .post{
            border: 1px solid #000;
            margin: 15px;
            padding: 15px;
        }

    </style>
</head>
<body>

    <div>
        <h1>My Cool Homepage</h1>
    </div>

    <div>
        <div><a href="#">Home</a></div>
        <div><a href="#">Links</a></div>
        <div><a href="#">Downloads</a></div>
        <div><a href="#">About Me</a></div>
    </div>


    <div>
        <div>
            <h2>My Latest Blog Post</h2>    
            <h4>November 23, 9791</h4>
            <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Non, quisquam. Maxime alias quod saepe corrupti dicta id, porro dolorum esse odit veritatis, doloremque nobis error nostrum consectetur ipsam totam nesciunt!</p>
        </div>

        <div>
            <h2>Some Other Post</h2>
            <h4>October 11, 1984</h4>
            <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Non, quisquam. Maxime alias quod saepe corrupti dicta id, porro dolorum esse odit veritatis, doloremque nobis error nostrum consectetur ipsam totam nesciunt!</p>
        </div>  

        <div>
            <h2>A Really Ancient Post</h2>
            <h4>January 17, 1207</h4>
            <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Non, quisquam. Maxime alias quod saepe corrupti dicta id, porro dolorum esse odit veritatis, doloremque nobis error nostrum consectetur ipsam totam nesciunt!</p>
        </div>          


    </div>


</body>
</html>
```

## JavaScript

### Motivation
We can use JavaScript to take in input from a user and make changes to the state of our page. We're eventually going to take our cloud project and rework it so that instead of just running when the user loads the page, we can create a button that will allow the user to turn on and off the animation.

### Chrome Developer Tools
One big themes of this course is making the transition from a person who passively consumes web content to someone who produces their own web pages. You already used part of Chrome Developer tools on the first day to inspect the code generating your favorite website.  Now we're going to dive deeper into these tools that will help you inspect and build websites.  Chrome Developer tools play a big role in our exploration of JavaScript.

### Open Dev Tools
Here's the keyboard shortcut for opening the Chrome Developer Tools / Console: Control+Shift+J

### JavaScript
JavaScript is a programming language that, along with CSS and HTML, allows us to build interactive web pages.

Here are the main categories or **types** of things that we'll be interacting with in JavaScript.

Picture JavaScript as a vast ocean.  There are a number of different fish swimming around in this ocean.  In reality, this is a bit more complicated, but for our purposes, these are the fish in our sea:
(Note, don't get hung up on the specifics or syntax of functions yet in case you are unfamiliar with them - we'll explore functions in more detail next week.)

* Strings - strings are text or characters, including numbers, and spaces, wrapped with single or double quotation marks
```
"Welcome to class"
"Goodnight Moon"
" "
'Berkeley '
' Berkeley '
"A"
'b'
'12345'
"12345"
```
* Numbers
```
4
-50
100
5.522
```
* Boolean - true or false
```
true
false
```
* Document Objects - All of the html elements we've already worked with.  Essentially any piece of a webpage that we want to target for some sort of interaction or modification.
```
<h1>My Header</h1>
<div id="redBox"></div>
<a href="#">Link to Nowhere</a>
```
* Function - a way to wrap some code in a reusable chunk
```
function changeBodyColor(){
  document.body.style.backgroundColor = 'red';
}

function addNums(num1, num2){
  return num1 + num2;
}
```

Let's log some stuff to the console:

What happens when you type the following lines into the console and hit the return key?
```
1 + 100;
"Berkeley";
"Berkeley" + 100;
1 === 1;
1 === 2;
"Berkeley" === "El Cerrito";
5 > 3;
10000 < 1;
true === false;
true === true;
```

Each line gets evaluated and returns some value.
🤓 Congratulations! You're already writing JavaScript.

🤔 **Exercise**: From the list above, which **types** are we interacting with in each of the lines we just inputted into the console?


## Console.log()
In order to keep working with JavaScript in our actual HTML document, we're going to use a JavaScript built in function called ```console.log()```. We use ```console.log()``` when we want to send expressions to be evaluated from our webpage.

```console.log``` is a built in function in JavaScript.  For our purposes, it lets us send things to the console in Chrome Developer tools.  It's mostly used for debugging purposes.

### Script Tag
Now we're going to add another section to our HTML document, the script section.  Since we want the JavaScript most likely to run and change pieces of the HTML we've written, it's a good idea to put the ```<script>``` section at the bottom of and inside the ```<body>``` tag.

🤔 Exercise: Write some expressions and send them to the console using ```console.log()```;

```
console.log(1 + 2);
console.log("hi mom!");
```

### Architecting the solution: animating the cloud on demand
Putting aside the computer for a moment, let's think through the logic of adding a button.  Review from last class how the cloud moved across the screen.  How can we enable or disable that from happening?  How could we animate this "the hard way"?

### document.querySelector and variables
So far we've been interacting with numbers, booleans and strings.   Now let's access some part of the page, one of the Document Objects we talked about earlier (the elements that make up our HTML page you've been working with since the first day).
QuerySelector will return the first instance of the input that matches our request.

In order to be able to access and use the Document Objects later on, we need to assign them to variables.  A variable is a space in memory that the computer reserves for some data.  It lets us carve out some space to store data, and it's name is always a pointer or window to that data that we can access at any time.

```
var myHeader = document.querySelector('h1');
console.log(myHeader);
```

What do you see logged to the console?

```querySelector``` returns the first instance of an element that matches our selection.

We can also ask for specific elements by id or class:

```
var blogSection = document.querySelector('#blog');
console.log(blogSection);

var firstPost = document.querySelector('.post');
console.log(firstPost);
```


### Modifying styling with JavaScript

Let's use what we learned about ```querySelector``` and variables to make some changes to our CSS using JavaScript. Here's a starter template. Before you render it in the browser, check to see if you can reason about what it does:

```
<!DOCTYPE html>
<html>
  <head>
    <title></title>
    <style>
      .redBox{
        width: 100px;
        height: 100px;
        background-color: red;
        position: absolute;
        top: 0px;
        left: 0px;
      }
    </style>
  </head>
  <body>
    <div class="redBox"></div>
  </body>
</html>
```

Now let's change that red box ```div``` using JavaScript.  Add a ```<script></script>``` section nested inside and at the bottom of the ```<body>``` element.

Here's some JavaScript:  Can you reason about what it's doing?

For example: ```background-color``` translates to ```backgroundColor``` in JavaScript.

```
var redBox = document.querySelector('.redBox');
redBox.style.backgroundColor = 'blue';
```

The first line declares a new variable, or ```var```, literally reserving some space in memory on the computer, and then assigns using the ```=``` sign it to the expression ```document.querySelector('.redBox')```.


⚠️ Note in JavaScript, the style names aren't written with dashes, but instead using the **camel case convention**, which means three things:
* start with a lower case letter
* no spaces
* each word after the first word has an uppercase letter

### Further Exploration
 * [FreeCodeCamp exercises](https://www.freecodecamp.org): All of the JavaScript exercises.
* [W3Schools Intro to JavaScript](https://www.w3schools.com/js/js_intro.asp)
* Advanced: [You Don't Know JavaScript](https://github.com/getify/You-Dont-Know-JS)
