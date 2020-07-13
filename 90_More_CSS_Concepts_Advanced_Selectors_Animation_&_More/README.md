# More CSS concepts (Advanced Selectors, Animation and More)

## Targeted Selectors:

### Direct Child
```css
    div > p{
      background: #ddd;
    }
```
- Selects only ```p``` that is a direct child of the div
- Here ```p``` inside ```<ul></ul>``` wouldn't be selected since it is not a direct child of div
- But ```<p></p>``` outside ```<ul></ul>``` would be selected.
```html
<div>
  <ul>
    <li><p>asfgsfg</p></li> 
  <ul> 
  <p>asfadfsd</p>
<div>
```

### Directly After:
```css
  /* Directly After */
  div + p {
    background: #333;
    color: #fff;
  }
```
- P Element directly after div will get applied with the above styles
```html
  <div>
    <p>lorem aksdjkfakj ajksdf </p>
  </div>
  <p> Hey MR. Tambourine</p>
```
- Here the Last ```<p></p>``` will only get selected.

### By Attribute:
```css
  /* By attribute */
  a[target] {
    background: red;
  }
```
- Here the ```<a></a>``` tag with target attribute will get this style applied.

```css
  /* By attribute */
  a[target="_self"] {
    background: red;
    color: white;
  }
```
- You can even target an element with attributes value

## nth child pseudo selectors
```css
  /* first-child (could be any element not just li) */
  li:first-child{
    background: red;
  }

  li:last-child{
    background: red;
  }

  /* Position 3 */
  li:nth-child(3){
    background: purple !important;
  }

  /* Every 3 */
  li:nth-child(3n+0){
    background: orange;
  }
```
- In the formula 3n+0, 3n is a counter and 0 is an offset (where we are starting)

```css
  /* Every 3 after 7 */
  li:nth-child(3n+7){
    background: yellow;
  }

  /* Every Odd */
  li:nth-child(odd){
    background: #ccc;
  }
  /* Every Even */
  li:nth-child(even){
    background: #ddd;
  }
```

## Before and After Pseudo Selector
- Allows us to insert content before or after an element.
- **Use Case**: When we have a form and there are fields that are required and marked with asterisk
- **Implementation**:
- CSS:
```css
  .is-required:after{
    content: '*';
    color: red;
    padding-left:2px;
  }
```
- Html:
```html
  <label class="is-required" for="name">Name</label>
  <input type="text">
```
- Asterisk is not in the markup but it is the content of after selector. It is a style that is added after the label element. 

### Before:
- Used in image overlay (dimming of image)
```css
    header:before{
      content: '';
      background: url('https://source.unsplash.com/weekly?water') no-repeat center center/cover;
      opacity: 0.3;
      position: absolute;
      top: 0; 
      left: 0;
      width: 100%;
      height: 100%;
      z-index:-1;
    }
```
- HTML:
```html
  <header>
    <h1>Hello World</h1>
    <p>Lorem ipsum dolor, sit amet consectetur adipisicing elit. Dignissimos, neque!</p>
  </header>
```
- Just Putting above styles in header would also dim the heading content.
- Due to before tag together with z-index, only background image is dimmmed.
- Note the empty string value set to the content property

## Box Shadows:

```css
  /* offset-x |offset-y| color */
  box-shadow: 10px 10px teal;

  /* offset-x |offset-y| blur-radius | color */
  box-shadow: 5px 5px 8px teal;
```
- 10px on the x-axis, 10 px on y-axis, teal is the color of the shadow
- blur radius blurs the shadow
- Adding negative value will add shadows to the top and left, right now it is in bottom and right. 

### Spread Radius:
- How far we want the shadows to spread
```css
  /* offset-x |offset-y| blur-radius | spread-radius| color */
  box-shadow: 3px 3px 10px 1px rgba(0,0,0,0.3);
```
- rgba can be used for the opacity effect

### Inner Shadow:
- like the shadow is inside
```css
    /* inset| offset-x |offset-y| color */
    box-shadow: inset 3px 3px 10px 1px teal;
```
- positive offset takes the shadow to top and left and the negative takes them to right and bottom in case of inner shadow

### Multiple Shadows:
- top-left and right-bottom:
```css
/* multiple shadows */
box-shadow: 3px 3px teal , -3px -3px oliv;
```
## Text Shadow:
```css
  h1.A{
    /* h-shadow|v-shadow|color */
    text-shadow: 0.2rem 0.2rem steelblue;
  }
```
- Diagonal shadow is formed by the combination of horizontal and vertical shadows

```css
  h1.A{
    /* h-shadow|v-shadow|color */
    text-shadow: 0.2rem 0.2rem steelblue;
  }
  h1.B{
    /* h-shadow|v-shadow|blur| color */
    text-shadow: 0.4rem 0.3rem 0.7rem steelblue;
  }
  h1.C{
    /* White Text: color is white but shadow is stylized */
    color: #fff;
    text-shadow: 0.2rem 0.2rem 1rem steelblue;
  }
  h1.D{
    /* Negative Values */
    text-shadow: -0.4rem -0.3rem 0.7rem steelblue;
  }
```

## CSS Variables (Custom Properties):
- You should define scope for your variable
- eg: 

```css
  body{
    --light-color:#f4f4f4;
    background: var(--light-color);
  }
```
- here --light-color is a variable
- Scope:
```css
  :root{
    /* variable created in root scope can be used anywhere in the stylesheet */
    --light-color: #f4f4f4;
  }
```
### Sandbox:
```css
:root{
    /* variable created in root scope can be used anywhere in the stylesheet */
    --light-color: #f4f4f4;
    --primary-color: #333;
    --secondary-color: #ccc;

    --max-width: 1100px
  }

  .box{
    --box-1-width : 1;
    --box-2-width: 2;
  }

  *{
    margin: 0;
    padding: 0;
  }
  body{
    font-family: Arial, Helvetica, sans-serif;
    line-height: 1.4;
    background: var(--light-color);
  }

  header{
    background-color: var(--primary-color);
    border-bottom: 5px var(--secondary-color) solid;
    color: #fff;
    text-align: center;
  }

  .container{
    display: flex;
    margin: auto;
    max-width: var(--max-width) ;
  }

  .box{
    background-color: var(--primary-color);
    border-bottom: 5px var(--secondary-color) solid;
    color: #fff;
    padding: 1rem;
    margin: 1rem;
  }

  .box-1{flex: var(--box-1-width);}
  .box-2{flex: var(--box-2-width);}
```

## Keyframe Animation:

- You take a property that can be animated such as a width, a position, a color, a opacity and something like that where you have midpoints. 
- Width - 0 to 600 px, animation, grow, shrink, move, fade in, fade out
```css
  body{
    background: #333;
  }
  .box{
    background: white;
    width: 200px;
    height: 200px;
    position: relative;
    animation-name: animate1;
    animation-duration: 5s;
    animation-iteration-count: 2;
    /* animation-iteration-count: infinite; */

    /* Stays at the final state */
    animation-fill-mode: forwards;

    /* delays 2s to start the animation */
    animation-delay: 2s;

    /* reverse animation */
    animation-direction: alternate ;
    /* animation-direction: alternate-reverse ; */

    /* motion eg: start up fast then ease in  */
    animation-timing-function: ease-in-out;
  }

  @keyframes animate1 {
    from{
      width: 200px;
      top: 0;
    }
    to{
      width: 600px;
      background-color: red; /*color morphing occurs */
      top: 300px;
    }
```
- Easier way:
```css
  animation: animate1 5s forwards 1s ease-in-out ;
```

### Percentages:
- Instead of moving from one point to another, we can also use percentages
- Percentages define the percentage of duration of animation
- Here is the CSS sandbox
```css
  body{
    background: #333;
  }
  .box{
    background: #fff;
    width: 200px;
    height: 200px;
    position: relative;
    top: 0;
    left: 0;
    animation: animate1 5s forwards ease-in-out;
  }

  @keyframes animate1 {
    25%{
      top: 0;
      left: 300px;
      background: red;
      border-radius: 50% 0 0 0;
    }
    50%{
      top: 300px;
      left: 300px;
      background: green;
      border-radius: 50% 50% 0 0;
    }
    75%{
      top: 300px;
      left: 0;
      background: blue;
      border-radius: 50% 50% 50% 0;
    }
    100%{
      top: 0;
      left: 0;
      background: white;
      border-radius: 50% 50% 50% 50%;

    }

  }
```

## CSS Transitions:
- Happens on an event (Like hovering over link)
- ```transition-property: background;``` for specifying which property we want to have transition on a hover or something like that. We could do all or specify a specific property.
- ```transition-duration: 2s;``` duration for transition
- Specify the event to change background as:
```css
    .box:hover{
      background: red;
    }
```
- Now you'll notice a transition on background color when you hover
- ```transition-delay: 3s;``` Adds delay on start of transition
- ```transition-timing-function: ease-in-out;``` for the manner of transition
- **Single line:** ```transition: background 2s ease-in-out;```
- **Multiple Transiton:** ```transition: background, border-radius 2s ease-in-out;```
- **Another Multiple Transition Option:** ```transition: all 2s ease-in-out;```


### TRANSITIONAL PROPERTIES

#### Properties that have an identifiable halfway point

-  background-color 
-  background-position 
-  border-color 
-  border-width 
-  border-spacing 
-  bottom 
-  color
-  font-size 
-  font-weight 
-  height left 
-  letter-spacing 
-  line-height 
-  margin 
-  max-height 
-  max-width 
-  min-height 
-  min-width 
-  opacity 
-  outline-color 
-  outline-offset 
-  outline-width 
-  padding right 
-  text-indent 
-  text-shadow 
-  top 
-  vertical-align 
-  visibility 
-  width 
-  word-spacing 
-  z-index

## Transform Property:

REF: https://developer.mozilla.org/en-US/docs/Web/CSS/transform

- ```transform: rotate(25deg);``` rotates 25 degree
- ```transform: skew(25deg);``` skews diagonally
- ```transform: scale(2);``` doubling the size

### Transform with transitions:

```css
...
    transition: all 1s ease-in-out;
  }

  .box:hover{
    transform: rotate(180deg);
    transform: skew(25deg); /* Overwrites rotate */
    transform: scale(2); 
  }
```

### Translate to move around
- translate x and y to move items around xy axis
```css
  .box:hover{
    transform: translateX(100px);
    transform: translate(100px, 100px); */
    transform: translate3d(100px, 100px, 100px); /* increases performance */
  }
```