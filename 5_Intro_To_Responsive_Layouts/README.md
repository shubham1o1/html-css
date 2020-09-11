# Intro To Responsive Layouts

## Responsive Design:
- Using HTML/CSS to make a website or app layout adapt to different screen sizes
- It is a necessity to build responsive layouts
- Layouts should render on any form factor

## Practices to Use:
- Set the Viewport/scale
- Use fluid widths as oppose to fixed
- Media queries - Different CSS styling for different screen sizes
- Rem units over px
- Mobile first method

## Getting Started with Media Queries:
```css
  /* Smartphones */
  @media(max-width:500px){
    body{
      background: red;
    }
    #smartphone h1{
      display: block;
    }
  }
```
- you can put max-width/min-width and max-height/min-height inside the media query's parentheses
- Devices are defined by their width and height. 
- Setting max-width : 500px; the style inside media query applies for devices whose width is less than or equal to 500px.

### media query with width range:
```css
/* tablet */
@media(min-width: 501px) and (max-width:768px){
  body{
    background: blue;
  }
  #smartphone h1{
    display: block;
  }
}
```
- from device width of 501 to 768 will get the style applied
- 768 is standard width for tablets
- ```@media only screen and (max-width:500px)``` means that it applies for screens only. By default it is applied to all media(i.e. print, speech, ...). 

### Landscape:
- Query the height:
```css
  /* Landscape */
  @media(max-height: 500px){
    body{
      background: orange;
    }
    #landscape h1{
      display: block;
    }
  }
```

### Separate Style Sheets for Media Queries:
```html
<link rel="stylesheet" media="screen and (max-width:768px)" href="mobile.css">
```
- Loads the mobile.css if the screen is less than 768px wide

## Em and Rem Units:
- Em unit is multiplier of its parent container
- Rem unit is relative to the font size of root html element
- By default we have the following config(margin is set to 1em):
```css
p {
    display: block;
    margin-block-start: 1em;
    margin-block-end: 1em;
    margin-inline-start: 0px;
    margin-inline-end: 0px;
}
```
- the parent is div - box-1
```html
  <div id="box-1">
    <h3>Box One</h3>
    <p>Lorem ipsum dolor sit amet consectetur, adipisicing elit. Laboriosam, doloremque obcaecati totam aliquid, neque fuga soluta sunt temporibus nam inventore dolorem unde! Minima mollitia dolorum, magnam maiores porro dolore explicabo.</p>
  </div>
```
- Absolute root element is ```<html>```. Default is 16px which we can see at the computed value at dev tool.
- we can find in the dev tools that the default h3 is 1.17em i.e ~18.72 px

### Problems with em:
- Padding to 1em gets 1.5em padding when we previously set font-size to 1.5em
- Nested elements keeps on growing since em multiplies wrt parent elements
```css
    #box-1{
      font-size: 20px; /* h3 will be 1.3em i.e 20*1.3 */
    }
    #box-1 p{
      font-size: 1.5em; /* box-1's 20 time 1.5 is 30 */
      padding: 1em; /*since we added font-size so 1em is not 20 but 30 (1.5em) */
    }
    #box-1 ul{
      font-size: 1.2em; /*Nested element is higher since they multiply higher value */
    }
```
### rems:
- Self-explanatory css code:
```css
/* changing root elements size */
html{
  font-size: 10px; /* easier to calculate, 1.6rem is 16, 2rem is 20 */
  /* making more responsive by setting to percentage */
  font-size: 62.5%; /* overrides 0.625*16 is 10 */
}
#box-2 h3{
  font-size: 2rem; /* 32 -> 2*16(default roots font size) */
}

#box-2 p{
  font-size: 1.6rem; /* 16*1.6 */
  line-height: 1.7rem; /* 1.7*16 */
}
```
- Changing font size from browser has no effect on elements set by em unit but it has direct effect on rem elements

## Viewport Height (vh) and Viewport Width(Vw):
- Viewport : Whole area of the browser, the browser's body.
- Browser display : Vh * Vw dimension, 100 Vh and 100 Vw
- You can set your content you take up anywhere between 0-100 **Vh** and **Vw**
- Vh is used more than Vw since most of the time things go all the way in width

### Content Height:
- The body element doesn't take all of the viewport. It just takes as much height as the content present. 
- CSS
```css
  <style>
    *{
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }
    body{
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    }
    header{
      background: #333;
      color: #fff;
      height : 100%;
    }
  </style>
```
- Html
```html
<body>
  <header>
    <h1>Welcome to our Website</h1>
    <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Numquam eligendi totam harum neque error natus.</p>
    <a href="#" class="btn">Find Out More</a>
  </header>
</body>
```
- Here setting header height to 100% does not fill whole browser with the header's background
- It is because the body doesn't cover whole of the browser. And the body only occupies the part of the browser windows that has the content. 
- So, we need viewport height for this reason
- we can set height from 100% to 100vh the the browser window is now cover with header's background color. 
```css
  header{
    background: #333 url('https://source.unsplash.com/daily');
    color: #fff;
    height : 100vh;
  }
```
- This is a great tool for creating landing pages.

## Making the hotel website fully responsive

- Made a new CSS file: mobile.css
- Imported just below the style.css
```html
<link rel="stylesheet" href="css/style.css">
<link rel="stylesheet" media="screen and (max-width:768px" href="css/mobile.css">
```
- We added media attribute with max-width

- To stack set float to none.
```css
#navbar .logo {
  float: none;
  text-align: center;
}
```
- Basically mobile.css is overridding style.css
- if style is more specific it wont be overridden by less specific. eg: ```#navbar li``` wont override ```#navbar ul li```
- While floating we may have set the width to lesser value than 100%, so we must explicitly set them to 100% when we override with a style to stack elements.