## Part 3 Outline
### Exercise

* Open the Sublime application on your computer (if you can't find Sublime, click the Windows icon in the lower left hand corner of the screen. In the text box that appears, type ```Sublime```. You should see Sublime appear in the applications list).
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
* Save as an HTML document on the Desktop. Remember the file format:
```xxxx.html```
* Simultaneously open your newly saved webpage in Chrome.

😎 ProTip You can quickly generate an empty HTML template in Sublime. After you have already saved your file as a *.html file somewhere on your local computer, type <h. You will see a menu appear. If you press the tab key, the HTML template will autocomplete.

* Now, create three ```<div>``` elements in the ```<body>``` section of your HTML document.  Don't forget to write your code **between** the opening ```<body>``` tag and the closing ```</body>``` tag.
* Style the div elements accordingly:

```
The first div should be 50px high by 50px wide and have a green background color.

The second div should be 100px high by 150px wide and have a blue background color.

The third div should be 200px high by 250px wide and have a yellow background color.

```
♻ **Review:** How can you apply different styles to different divs?  Remember: use **class selectors**.  Here's an example of a class selector if you forgot how to do that:

```
<!DOCTYPE html>
<html>
    <head>
        <title></title>
        <style>

          .yellowSun{
            background: yellow;
            border: 3px solid orange;
            width: 100px;
            height: 100px;
            border-radius: 100%;
            margin: 0 auto;
          }

        </style>
    </head>
<body>

    <div class="yellowSun"></div>

</body>
</html>

```

💃 If you finish early, add some margins to your divs to spread them out!

## Making our website more dynamic: Pseudo Classes and CSS Animations

### Pseudo Classes

You can rerender your style completely when a mouse hover event happens using a CSS Pseudo Class.

In this example, we declare a style for an ```h2``` element normally, and then further down in the CSS redeclare the style for a different state (in this case a hover event or the hover pseudo class).

```
h2{
    background-color: yellow;
}

h2:hover{
    background-color: red;
}
```
Here's a translation of the above CSS into English: "Normally, make h2 elements have a yellow background color. But, when someone hovers over h2 elements with their mouse, change the background color to red."

The pseudo class declaration replaces style declarations from the previous declaration.  We can selectively alter properties, while leaving others intact.  For example, maybe we always want to keep our h2's font size 72px, width at 100% of the container, and text aligned center, but want to change the background color on a hover event:

```
h2{
    font-size: 72px;
    width: 100%;
    text-align: center;
    background-color: yellow;
}

h2:hover{
    background-color: red;
}
```
We reference only the properties we want to update or change. Everything else stays the same!

You can totally transform a previously declared style using a pseudoselector. Let's experiment with pseudoselectors on the divs you created for the warmup exercise!  Try the following:

* On a hover event, change the size of one of your divs.
* On a hover event, change the color of one of your divs.
* On a hover event, change the border-radius on one of your divs.

### CSS animations

CSS animations let us create some really impressive effects using only CSS (no Flash or JavaScript!).  CSS animations are a more powerful version of the CSS psuedo classes. Right of the bat, we can drastically improve the way our pseudoselector state change looks! We can use the CSS ```transition``` property to **ease** the transition between states.  In this example, I created a class style called ```myRedBox```.  On a hover event, ```myRedBox``` turns into a smaller circle with a green background:

```
.myRedBox{
    width: 100px;
    height: 100px;
    background: red;
    margin: 15px;
}

.myRedBox:hover{
    border-radius: 100%;
    width: 50px;
    height: 50px;
    background: green;
}

```

The current transition is jarring.  But if I add the ```transition``` property to the original style, I can improve it:

```
.myRedBox{
    transition: ease 1s;
    width: 100px;
    height: 100px;
    background: red;
    margin: 15px;
}

.myRedBox:hover{
    border-radius: 100%;
    width: 50px;
    height: 50px;
    background: green;
}

```

```1s``` stands for "1 second" similar to the px declarations you've already seen.

Experiment with different times and updates using ```transition```!

### @keyframes

The ```@keyframes``` CSS declaration lets us literally create an animation frame by frame.  Each frame contains a different CSS style for a different state of our animation.

Let's take one of our example divs from earlier:

```
.redBox{
    width: 100px;
    height: 100px;
    background: red;
}

```
If we want to animate the ```redBox``` we can declare an animation in our CSS file, and then add that animation to the ```redBox```. We use a new declaration called **keyframes** to label our animation:

Inside the ```@keyframes``` declaration, we specify how we want our CSS to look at different moments in time.  Don't forget to name your animation!

```
@keyframes changingColorAnimation{
}
```

```@keyframes``` let us build different CSS styles for different moments in time. We can start at 0% and declare different styles all the way through 100% of the animation's completion, just like a cartoon animator creates different images for different moments in time:

For example, if we want our box to transition from red to blue to green and back to red, we can write something like this:

```
    @keyframes changingColorAnimation{

     10%{
         background: blue;
         }

     50%{
         background: green;
        }

     100%{
         background: red;
         }
    }

```
The percentage refers to the amount of the animation that has completed.  You could theoretically write a new CSS style for every integer between 1 and 100 in this case.

♻ **Review:** Do you remember the concept of HTML **nesting**?  CSS keyframes literally nests multiple CSS styles into one segment of CSS.

Now all we have to do is add this keyframe property to our previously declared style for our div, using the ```animation-name``` property.:

```
.redBox{
    width: 100px;
    height: 100px;
    background: red;
    animation-name: changingColorAnimation;
    animation-duration: 5s;
    animation-iteration-count: 2;
}

```

We also need to add additional properties telling how long to run the animation, and how many times to repeat it.

Experiment with other animation style declarations and properties:

```
    animation-duration: 5s;
    animation-delay: -1s;
    animation-iteration-count: infinite;
```

### Project: Sky animation
For this week's project, you're going to use your knowledge of CSS animations to build a simple sky animation.

* Download this image:
https://cdn172.picsart.com/228360378035212.png?r1024x1024
* Save it on your desktop as ```cloud.png```.  The website will try to download it with some crazy filename - make sure you change the name!
* Create a new HTML document
* Write a CSS element selector for ```body``` to set the background to blue.  (Tip: blue is fine, but we can fine tune our color using a hex code color: ```#6565a4``` is even better).
* Add the cloud image to your webpage using an ```<img>``` tag.  Remember the ```src="cloud.png"``` attribute!
* The image is a little big for the webpage.  Write a class  selector to change the ```width``` property of your image to make it smaller. (300px will probably do it but feel free to experiment with the size).
* Don't forget to add your new class as an attribute on your image!
* In your class selector for your image, also set the following properties in addition to width:
```
position: absolute;
left: 0%;
top: 30%;
```
* If you wrote your class selector correctly and applied to the image tag, you should see a cloud on the screen in about that position.
* Now, write a ```@keyframes``` declaration to create the animation.  In this case, we want our cloud to start at 0% left on the page and progress to 100% left (move from the left side of the page all the way to the right side). The simplest animation would translate like this into English:  "At 0% animation completion, set left to 0%.  At 100% animation completion, set left to 100%."

Stretch goals:
* Add more clouds of different sizes and shapes! Create a storm!
* Add in the sun!  Animate the background color to create a sunrise.  Use [CSS Box Shadow Properties](https://codersblock.com/blog/creating-glow-effects-with-css/) to add glow to the sun.
* Add in a plane!
* Add in trees, mountains, lakes - create a scene!
* Read more about CSS Animations [here](https://www.w3schools.com/css/css3_animations.asp)

### End of Class
* Submit your work for class credit.  On your desktop, create a folder with your name.  Put your work into that folder.  Drag the folder into the shared folder [here](https://drive.google.com/drive/folders/1xwPCotd3c9eIDqwDBhg_UEZ_QJETePuR?usp=sharing).

### Further Exploration
 * [FreeCodeCamp exercises](https://www.freecodecamp.org): “Front End Development Certifications” > “HTML5 and CSS” – complete all of the exercises there (through “Use RGB to Mix Colors”)
* Read more about CSS Animations [here](https://www.w3schools.com/css/css3_animations.asp)
