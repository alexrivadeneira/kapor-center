## Part 5 Outline

### Exercise
Here's a new HTML element:

```
<button> </button>
```

Figure out how to render this into the body of an HTML document.
Experiment with the following:
* Nest a text node inside the button (add text to the button)
* Can you select and style the element using CSS?
* Can you make this button into a link, wrapping it with an anchor tag?
* Read the [docs](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/button) and experiment with other attributes!

### Motivation/Project
Using JavaScript, we're going to add a button to the cloud project that lets the user trigger the animation.

## JavaScript functions

JavaScript functions are used to wrap a code block so that you can control when that code gets executed.  Here's the general format for a **function definition**.
```
function nameOfFunction(){
  // your code goes here
}
```
🕵 Note the ```//``` symbol "comments out" the line, so it won't get executed and you can write notes in English in your code. In this case, you would replace the line starting with ```//``` with your actual code.

To use your function, you need to invoke it, using the name of the function plus parentheses like so.  Below is a **function invocation**, meaning the code inside the block in our function definition would get executed when the computer runs this line of code:
```
nameOfFunction();
```

Here are some examples of simple function definitions.  Can you reason about what they do?

```
function doSomething(name){
    return 'Welcome to ' + name + ' Berkeley Public Library!!!';
}

function addNums(num1, num2){
  var someSum = num1 + num2;
  return someSum;
}

function changeColor(){
  body.style.backgroundColor = 'red';
}

```
Some functions can explicitly return a value, like the first and second functions in the example above.  Other functions might make changes to the state of our webpage, changing DOM elements, and not explicitly return anything (in that case, the function will actually return ```undefined```).

Your function can take an input.  If you build your function to take in input, you would declare that in the function definition.  In the examples above, ```addNums()``` and ```doSomething()``` both take inputs.  How many inputs do each of those functions take?

Here are some invocations using the function definitions written above.   These lines "turn on" and run the functions declared above. We can invoke a function as many times as we'd like.

```
doSomething('Bob');
addNums(1,2);
changeColor();

// We can keep invoking these as we wish:

doSomething('Mary');
doSomething('Beth');
addNums(100000,999);
changeColor();
changeColor();
changeColor();

```
Question: After we've run changeColor() once on a page, what will happen if we try to run it again?


### console.log() revisited
Remember those parentheses at the end of ```console.log()```?  ```console.log()``` is a function also! It's a built in function in JavaScript.  As you remember, ```console.log``` takes in an input, and spits that input out into the console that we can see in the Chrome Developer tools. You can pass expressions to ```console.log()``` that will get evaluated before they hit the console, including functions!

🙃 Reminder! Here's the keyboard shortcut for opening the Chrome Developer Tools / Console: Control+Shift+J

```
// review from last week:

console.log('Berkeley');
console.log(100);

console.log('Reading' + ' is cool!!');
console.log(100 + 1);

// now, more exciting complex expressions:

console.log(addNums(1,2));
console.log(addNums(100,1));
console.log(doSomething('Richard'));

```
```console.log()``` is really useful to let us debug functions and see if we're getting the expected output/return value!


### onclick events

During the warmup exercise, we experimented with the ```<button>``` HTML element.  Now let's use its ```onclick``` attribute to wire buttons to functions.

We can pass function invocations to the ```onclick``` attribute like so:

```
<button onclick="myFunction()">Click here to run the function!</button>
```

### Exercise - wiring functions and buttons
In the code below, we have some functions in the ```<script>``` section of the HTML document.  Can you figure out how to connect them the buttons via the ```onclick``` attribute?

Before you begin, notice the functions in this HTML document.  Do any of these functions take input or have output?  What type of function are these?  What's going on in the ```<body>``` section?

```
<!DOCTYPE html>
<html>
    <head>
        <title></title>
        <style>
        #sun{
          width: 100px;
          height: 100px;
          background: yellow;
          border-radius: 100%;
          animation-duration: 5s;
          position: absolute;
          border: 3px dotted orange;
          bottom: 0%;
          left: 50%;
          animation-iteration-count: infinite;
        }

        @keyframes raiseTheSun{
          0%{
            bottom: 0%;
          }

          100%{
            bottom: 100%;
          }
        }
        </style>
    </head>
<body>
  <div id="sun"></div>

  <button>Sunrise!</button>
  <button>Turn Off the Lights!</button>
  <button>Build A Fence!</button>

  <script>
  function sunRise(){
    const sun = document.querySelector('#sun');
    sun.style.animationName = 'raiseTheSun';
  }

  function turnOffLights(){
    document.body.style.background = '#000';
  }

  function buildAFence(){
    document.body.style.border = '10px dotted tan';
  }

  </script>
</body>
</html>

```

Stretch goals:
* Change the actions that the buttons trigger
* Add another button and make it perform another action (write another function!)
* Add buttons that reverse the current actions
* What output do you see if you use ```console.log()``` to display the return value of these functions?

### Project: Control the Cloud Animation With a Button

1. Save and examine the starter code below - what do you have?  A good place to start is looking in the ```<body>``` to see the main structure of the page.  Also notice the ```<style>``` section has an animation in it.  What does that animation do?
2. Remember, to animate the cloud, we need to add the animation name to the selector that is used to build the cloud (the class ```cloudImage```).
Remember the CSS properties that let us build an animation:
```
/* CSS in the <style> section of the HTML document: */
animation-name: myAnimation;
animation-duration: 5s;
```
3. In the ```<script>``` section of the HTML document, Connect the ```blowWind()``` function to the button using the ```onclick``` attribute in the button element.
4. Throw a ```console.log()``` line into your ```blowWind()``` function to make sure the button is connected to the function.
5. We need to complete the ```blowWind()``` function.  In ```blowWind()```, you need to use ```document.querySelector``` to get the cloud div using its class, ```cloudImage```.  Assign the result of the querySelector function to a new variable.
6. Once you have the variable pointing to the cloud, update the cloud using the ```.style``` property.  For example, if I want to add an animation to an element in JavaScript I could do something like this:

```
myElement.style.animationName = "myAnimation";
```
7. Don't forget to also update the ```animationDuration``` property on a separate line.  Update it using a string like ```"5s"```.

```
<!DOCTYPE html>
<html>
<head>
    <title>I Wandered Lonely As a Cloud</title>
    <style>

    body{
        background: #6565a4;
    }

    .cloudImage{
        width: 300px;
        position: absolute;
        top: 50%;
        left: 0%;
    }

    @keyframes cloudAnimation{
        0%{
            left: 0;
        }
        100%{
            left: 100%;
        }
    }
    </style>
</head>
<body>
    <img src="https://cdn172.picsart.com/228360378035212.png?r1024x1024" class="cloudImage"/>

    <button>Click for a gust of air!!</button>

    <script>
        function blowWind(){

        }
    </script>

</body>
</html>
```

### Stretch goals:
* Check out the ```<input>``` HTML element.  Can you take in some user text input, for example, the user's request on how many seconds to run the animation? Check out some documentation about input [here](https://www.w3schools.com/html/html_forms.asp
* You can use the ```.value``` property on an input element to get the user input.  
* To test it out, create an ```<input>``` element, give it a unique ID, use ```document.querySelector``` to access that element in JavaScript, and then ```console.log()``` the resulting element's ```.value``` property.
* Remember: the CSS style ```animation-duration``` accepts a string in the format "some number plus the letter s", eg ```5s```.  So you'll have to figure out how to manipulate your strings to get this desired input.


### Further Exploration
* Check out other computer-related events at the [Library](https://www.berkeleypubliclibrary.org/events/computers)!
* [FreeCodeCamp exercises](https://www.freecodecamp.org): Keep going!
