# More CSS concepts (Advanced Selectors, Animation and More)

## Targeted Selectors:

### Direct Child
```css
    div > p{
      background: #ddd;
    }
```
- Selects only ```p``` that is a direct child of the div
- Here ```p`` inside ```<ul></ul>``` wouldnt be selected since it is not a direct child of div
- But ```<p></p>``` outside ```<ul></ul>``` would be selected.
```html
<div>
  <ul>
    <li><p>asfgsfg</p></li> 
  <ul> 
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
- P Element directly after div which get applied the above styles
```html
  <div>\
    <p>lorem aksdjkfakj ajksdf </p>
  </div>
    <p> Hey MR. Tambourine</p>
```
- Here the Last P will only get selected.

### By Attribute:
```css
    /* By attribute */
    a[target] {
      background: red;
    }
```
- Here the a tag with target attributed will get this style applied.

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
- **Use Case**: When we have a form and there is fields that are required and marked with asterisk
- Implementation:
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
- Asterisk is not in the markup but the content in after style is added after the label element. 

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
