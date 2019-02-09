## Part 2 Outline
### Exercise

* Open the Sublime application on your computer (if you can't find Sublime, click the Windows icon in the lower left hand corner of the screen.  In the text box that appears, type ```Sublime```.  You should see Sublime appear in the applications list).
* Paste in our basic HTML starter document:
```
<!DOCTYPE html>
<html>
    <head>
        <title></title>
        <style></style>
    </head>
<body>
</body>
</html>
```
* Save as an HTML document on the Desktop.  Remember the file format: ```xxxx.html```
* Simultaneously open your newly saved webpage in Chrome.
* Add a title to your page (remember: it will appear in the top of your tab).

### Sublime
Sublime is code editing program.  Most importantly, Sublime provides **syntax highlighting** meaning it adds color to our code to help us visualize its structure.  **Syntax** refers to the structure of our code and the rules that govern that structure.  

**Can you remember some rules about HTML code from last session?**

```
<h1> My header </h1>
<h1 class="fancyStyle"> My styled header</h1>
<a href="http://www.google.com">Link to Google</a>

```
♻ Review: Where is HTML syntax nested in our document?

**What about CSS syntax?**

```
h1{
    background: green;
    color: white;
    margin: 15px;
}
```
♻ Review: Where is CSS syntax nested in our HTML document?

Sublime can help us catch small syntax errors that we would otherwise have to search for ourselves.

### Exercise: Fix the Syntax Errors
Copy and paste the following template into a fresh file in Sublime.  Save the file as an HTML file.  You should see the code appear with different colors after you save it. What does this file look like in the browser?  Spoiler alert: it's not pretty because it has a lot of syntax errors.  It's your job to correct the syntax errors and make the page work.

😎 **ProTip** You can quickly view your code in the web browser.  In Sublime, right click anywhere in your HTML document, then select "View in Browser".
```

 <!DOCTYPE html>

  <html>
    <head>
      <title>My Homepage</title>
      <style>

        body{
            background: yellow;
        }

        p{
          color: red;
          font-size: 14px;
          padding: 15 px;
          border: 3px solid green;
          background-color: white;

        h2{
          font-family: sans-serif
          color: green

        h3{
          font-family: sans-serif;
        }

      </style>
    </head>

    <body>
      <h2>Welcome to my homepage!

      <h3>What do you want to see? Choose a link below:<h3>

      <a href="https://www.berkeleypubliclibrary.org target="_blank">Berkeley Public Library</a>
      <a href="https://duckduckgo.com" target="_blank">Search the Web</a>
      <a href="http://www.unsplash.org">Cool free pictures</a>

      <p> Welcome to my wonderful website on the wonderful world wide web!  I hope you enjoy what you find here! </p>

    </body>
  </html>
  ```


### CSS: Class and ID Selectors
**Class selectors** are used to apply styling to elements that appear multiple times on a page.  You started experimenting with class selectors last class:

```
.highlightedText{
    background-color: yellow;
    font-family: sans-serif;
    font-weight: 900;
    color: black;
}
```
**ID selectors** are used to identify a single part of the page.  For example, the "main" part of the page that stores content, or a navigation bar that appears only once per page.

```
#main{
    width: 100%;
    background: black;

}
```


### Using divs

The ```<div>``` is a powerful HTML tag.  We can use it to mark out pieces, literally **divisions** of our website to target for styling:

Add a ```<div>``` to your website.  What do you see when you reload the page?
```
<div> </div>
```
Nothing changes! We have to add content and styling to make use of the ```<div>```

Let's create another custom CSS styling class.  We will call it ```fancyStyle```.  Let's add it to our div:

```
<div class="fancyStyle"> </div>
```
Save and refresh the page.  What do you expect to see?

We have to add some styling to fancyStyle:
```
.fancyStyle{
    width: 200px;
    height: 300px;
    background: blue;
}
```

Save and refresh the page.  Now what do you see?

Experiment with other CSS properties:
```
width: 50px;
height: 50px;
background-image: url("");
border: 6px dotted purple;
border-left: 1px solid green;
```

### Creating a custom element with a div
Let's build a custom red circle element using a class style and a div.
First, let's demarcate our div in the HTML document:

```
<div> </div>
```

Now let's add a custom class that we will build in the ```<style></style>``` section of our HTML document:

```
<div class="redCircle"> </div>
```

When we refresh the page, we don't see anything because we haven't declared and styles for ```redCircle```.  Plus, our div is empty anyway!

Add our style:
```
.redCircle{
    background: red;
    border-radius: 100%;
    width: 100px;
    height: 100px;
}
```

### Creating a simple layout with CSS Flexbox
Let's use our knowledge of divs and CSS to create a basic website layout.  Our goal is to create a website with a navigation section at the top, a main section for our content, and a sidebar.

First, in a fresh HTML document, set up the HTML structure.  Since we're demarcating a number of sections of our website that only appear once, we'll drop in ID divs:

```
<!DOCTYPE html>
<html>
    <head>
        <title></title>
        <style></style>
    </head>
<body>
    <div id="nav">
    </div>
    <div id="container">
        <div id="main">
        </div>
        <div id="sidebar">
        </div>
    </div>
</body>
</html>
```

😎 **ProTip** You can quickly generate an empty HTML template in Sublime.  After you have already saved your file as a ```.html``` file somewhere on your local computer, type ```<h```. You will see a menu appear.  If you press the tab key, the HTML template will autocomplete.

Now let's add styling to bring our elements to life:
The nav section should stretch across the entire top of the page and be about 100px high:
```
#nav{
    width: 100%;
    height: 120px;
    background-color: green;
}
```

We can use the ```display: flex``` property to make the other sections inside the container easy to lay out:
```
#container{
    display: flex;
    align-items: stretch;
    width: 100%;
    background-color: red;
}
```

Now specify the dimensions of the #main and #sidebar areas:
```
#main{
    width: 65%;
    background: yellow;
}
#sidebar{
    width: 35%;
    background: purple;
}
```

Now you have all of the basics to make a great website!

😎 If you're already caught up, check out this document about [CSS Flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/) to create even more exciting layouts.

### Bonus: PseudoSelectors
You can rerender your style completely when a mouse hover event happens using a **CSS Pseudo Selector**.

In this example, we declare a style for an ```h2``` element normally, and then further down in the CSS redeclare the style for a different state (in this case a hover event).

```
h2{
    background-color: yellow;
}

h2:hover{
    background-color: red;
}

```
Here's a translation of the above CSS into English: "Normally, make h2 elements have a yellow background color.  But, when someone hovers over h2 elements with their mouse, change the background color to red."

You can totally transform a previously declared style using a pseudo selector.  Experiment with it!   

### Project
Start building your personal webpage.
* Start with the empty HTML document
* Be sure to add a title!
* Add some headers and paragraphs.
* Add an image
* Add some links to outside websites
* Style some elements using class and ID selectors
* Add and style a ```<div>```

Stretch goals:
* Build multiple pages and link them together
* Do further experimentation with [CSS Flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)


### Further Exploration
 * [FreeCodeCamp exercises](https://www.freecodecamp.org): “Front End Development Certifications” > “HTML5 and CSS” – complete all of the exercises there (through “Use RGB to Mix Colors”)
