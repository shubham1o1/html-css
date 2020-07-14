# News Grid Website

- UI for a news website
- Sticky Navbar
- Overlay in showcase using before selector
- Grid 
- Utility classes for bg color
- Footer also has grid
- Article Page 
- Responsive

## Setup and Favicon:
- Favicon Creating site: http://tools.dynamicdrive.com/favicon/
- Put the Favicon in the root folder and not in the img folder
- Adding Link to favicon from the dynamicdrive site: 
```html
  <link rel="shortcut icon" type="image/x-icon" href="favicon.ico">
```
- Adding Social Links with fontawesome
```html
  <div class="social">
    <a href="http://facebook.com" target="_blank"><i class="fab fa-facebook fa-2x"></i></a>
    <a href="http://twitter.com" target="_blank"><i class="fab fa-twitter fa-2x"></i></a>
    <a href="http://instagram.com" target="_blank"><i class="fab fa-instagram fa-2x"></i></a>
    <a href="http://youtube.com" target="_blank"><i class="fab fa-youtube fa-2x"></i></a>
  </div>
```

## Core Styles, Variables and Navbar:
### justify-self vs justify-content
- former is for individual items and the latter for the parent's alignment

### Changing fontawesome's icon's style:
```css
  #main-nav .social i {
    color: #777;
    margin-right: .5rem;
  }
```

## Showcase with Overlay and Button Styles:

### Showcace HTML:

```html
<!--  Showcase -->
<header id="showcase">
  <div class="container">
    <div class="showcase-container">
      <div class="showcase-content">
        <div class="category category-sports">Sports</div>
        <h1>Some Sports Article</h1>
        <p>Lorem ipsum, dolor sit amet consectetur adipisicing elit. Saepe amet optio fuga quas nisi recusandae nobis quidem cumque a excepturi.</p>
        <a href="article.html" class="btn btn-primary">Read More</a>
      </div>
    </div>
  </div>
</header>
```
- Remember the component: **showcase -> container -> showcase-container -> showcase-content -> category, category-sports, btn, btn-primary**

- We put the background in the **before** pseudo selector. The before pseudo selector is going to be positioned absolute. If you position something absolute it is going to positioned inside the first relative container. So, we have the following style for the showcase:
```css
/*  Showcase */
#showcase {
  color: #fff;
  background: #333;
  padding: 2rem;
  position: relative;
}
```

- before selector:
```css
#showcase:before{
  content: '';
  background: url('../img/featured.jpg') no-repeat center center/cover;
  position: absolute; 
  /* position is absolute because we are laying it on top of showcase */
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  opacity: 0.4;
}
```
- You see through the image to the dark background.
- The text is also translucent

- The showcase container:
```css
#showcase .showcase-container {
  display: grid;
  grid-template-columns: repeat(2, 1fr); 
  /* Even though there is only one item, doing (2, 1fr)
   is going to set that item in the half width */

  justify-content: center; /*horizontal center */
  align-items: center; /*vertical center */

  height: 50vh;
}
```

- Showcase content to disable dimming of the text:
```css
#showcase .showcase-content{
  /* Bringing text to the front so
  it's opacity is not dimmed */
  z-index: 1;
}
```

- Category Styling:
```css
/* For highlighting category label*/
.category {
  display: inline-block;
  color: #fff;
  font-size: 0.55rem;
  text-transform: uppercase;
  padding: 0.4rem 0.6rem;
  border-radius: 15px;
  margin-bottom: 0.5rem;
}

.category-sports {background: var(--sports-color);}
.category-ent {background: var(--ent-color);}
.category-tech {background: var(--tech-color);}
```

- Button styling
```css
.btn {
  display: inline-block;
  border: none;
  background: var(--dark-color);
  color: #fff;
  padding: 0.5rem 1.5rem;
}

.btn-light{background: var(--light-color);}
.btn-primary{background: var(--primary-color);}
.btn-secondary{background: var(--secondary-color);}
```
---

## Home Articles Grid:

### Style Classes and the first article:
```html
  <!-- Home Articles -->
  <section id="home-articles" class="py-2">
    <div class="container">
      <h2>Editors Picks</h2>
      <div class="articles-container">
        <article class="card">
          <img src="img/articles/ent1.jpg" alt="">
          <div>
            <div class="category category-ent">Entertainment</div>
            <h3>
              <a href="article.html">Lorem ipsum dolor sit amet.</a>
            </h3>
            <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Nemo ab doloremque dolor tenetur facere ipsum deserunt delectus asperiores vitae? Quia!</p>
          </div>
        </article>
  ...
```
- ```card``` is something that manages content rather than letting texts and images freely float. 
- ```card``` is a grid container and the div inside it is another grid container.
- we added .container inside .container

### Without grid inside a grid:
```html
  <article class="card">
    <div class="category category-sports">Sports</div>
    <h3>
      <a href="article.html">Lorem ipsum dolor sit amet.</a>
    </h3>
    <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Nemo ab doloremque dolor tenetur facere ipsum deserunt delectus asperiores vitae? Quia!</p>
  </article>
```
- We removed a div inside card(grid)

### Adding Cards:
```css
.card {
  background: #fff;
  padding: 1rem;
}
```
## Styling Home Articles
```css
#home-articles .articles-container {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-gap: 1rem;
}
```
- ```#home-articles .articles-container > *:first-child {``` Anything that is direct direct **(> *)**
- Implementing grid  inside a grid:
```css
#home-articles .articles-container > *:first-child,
#home-articles .articles-container > *:last-child{
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  grid-gap: 1rem;
  align-items: center; /* center the image */
  grid-column: 1 / span 2;
}

#home-articles .articles-container > *:last-child{
  grid-column: 2 / span 2;
}
```

### Changing color of heading & link
- Has to be specific, just element/class/id selector wont do
```css
.bg-dark h1,
.bg-dark h2,
.bg-dark h3,
.bg-dark a,
.bg-primary h1,
.bg-primary h2,
.bg-primary h3,
.bg-primary a,
.bg-secondary h1,
.bg-secondary h2,
.bg-secondary h3,
.bg-secondary a {
  color: #fff;
}
```

### Setting card's background:
```css
.bg-primary {
  background: var(--primary-color);
  color: #fff;
}
.bg-dark {
  background: var(--dark-color);
  color: #fff;
}
.bg-secondary {
  background: var(--secondary-color);
  color: #fff;
}
```

## Footer with Grid:
- It is also a grid container
- Set the background, set image width and set text color:
```css
#main-footer{
  background: var(--dark-color);
  color: #fff;
}

#main-footer img {
  width: 150px;
}

#main-footer a {
  color: #fff;
}
```

- Set the grid with 4 item
```css
#main-footer .footer-container {
  display: grid;
  grid-template-columns: repeat(4,1fr);
  grid-gap: 1.5rem;
}
```

- Span last item (copyright item across the width)
```css

#main-footer .footer-container > *:last-child{
  background: #444;
  grid-column: 1 / span 4;
  padding: 0.5rem;
  text-align: center;
  font-size: 0.75rem;
}
```

-Adjust input email and subscibe button to have equal width
```css
#main-footer .footer-container input[type='email'] {
  width: 90%;
  padding: 0.5rem;
  margin-bottom: 0.5rem;
}

#main-footer .footer-container input[type='submit'] {
  width: 90%; /* same as input email */
}
```

## About Page and Page Container:
- Layout for page:
```html
  <section id="about">
    <div class="container">
      <div class="page-container">
        
      </div>
    </div>
  </section>
```
- Page container is a grid container with main content and sidebar layout
- It can be used for other pages as well

### Sidebar Markup:
```css
<aside class="card bg-primary">
  <h2>Join Our Club</h2>
  <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Optio, nam.</p>
  <a href="#" class="btn btn-dark btn-block">Join Now</a>
</aside>
```

### Page container style:
```css
.page-container {
  display: grid;
  grid-template-columns: 5fr 2fr;
  margin: 2rem 0;
  grid-gap: 1.5rem;
}

.page-container > *:first-child{
  grid-row: 1 / span 3;
}
```
- grid row spanning - top to 3 rows. Grid will repeat the pattern for 3 rows

## Article page:
- Similar to about page

### Meta Data and Small Tag:
```html
<!-- metadata -->
<div class="meta">
  <small>
    <i class="fas fa-user"></i>Written By John Doe January 12, 2020
  </small>
  <div class="category category-ent">Entertainment</div>
</div>
```
- Small is used for displaying something with reduced size
- We have used flexbox for meta info ```(small and div)``` elements
```css
#article .meta {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background: #eee;
  padding: 0.5rem;
}

#article .meta .category {
  margin-top: 0.4rem;
}
```

## Responsive Media Queries:
