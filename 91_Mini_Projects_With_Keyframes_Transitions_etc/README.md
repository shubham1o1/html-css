# Mini Projects with Keyframes Transitions

## Hamburger Menu Overlay:

- Responsive Menu
- Without javascript(click event)
- We have used the checkbox input and styling the checked state
- When we click the menu the checked state is styled and a menu is shown, when you uncheck it goes away
- Variable in style css can be used in menu css
```css
.menu-wrap{
  position: fixed;
  top: 0;
  left: 0;
  z-index: 1;
}
```
- ```position:fixed;``` with ```z-index``` puts the element in front of other elements and it is not effected by scolling, it remains in one fixed position

- We can use ~ selector to select different unrelated elements. 

## Knowledge Timeline:

- To perform calculation operation in CSS:
```css
  #timeline ul li div {
    width: calc(100vw - 90px);
  }
  ```

## CSS Dropdown Menu:
- HTML sandbox:
```html
  <nav id="navbar">
    <ul>
      <li><a href="#">Home</a></li>
      <li><a href="#">About</a></li>
      <li>Services <i class="fas fa-angle-down"></i> 
        <ul>
          <li><a href="#">Web Development</a></li>
          <li><a href="#">Website Design</a></li>
          <li><a href="#">Mobile Development</a></li>
          <li><a href="#">SEO</a></li>
        </ul>
      </li>
      <li>Blog <i class="fas fa-angle-down"></i> 
        <ul>
          <li><a href="#">HTML</a> <span>22 Posts</span></li>
          <li><a href="#">CSS</a> <span>16 Posts</span></li>
          <li><a href="#">JavaScript</a> <span>10 Posts</span></li>
          <li><a href="#">Python</a> <span>13 Posts</span></li>
          <li><a href="#">PHP</a> <span>10 Posts</span></li>
          <li><a href="#">Design</a> <span>21 Posts</span></li>
        </ul>
      </li>
      <li><a href="#">Contact</a></li>
    </ul>
  </nav>
```

- CSS SANDBOX:

```css
:root {
  --primary-color: coral;
  --secondary-color: chocolate;
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

html,
body {
  background: #f4f4f4;
  font-family: Arial, Helvetica, sans-serif;
}

#navbar ul {
  list-style: none;
}

#navbar ul li {
  color: #333;
  display: inline-block;
  padding: 1rem;
  position: relative;
}

#navbar ul li a {
  color: #333;
  text-decoration: none;
}

/* Hide nested ul by default */
#navbar ul li ul {
  display: none;
}

#navbar ul li:hover {
  cursor: pointer;
  background: var(--primary-color);
  color: #fff;
}

#navbar ul li:hover a {
  color: #fff;
}

/* Nested dropdown show */
#navbar ul li:hover ul {
  display: block;
  position: absolute;
  left: 0;
  width: 200px;
  margin-top: 1rem;
}

#navbar ul li:hover ul li {
  display: block;
  background: #e7e7e7;
}

#navbar ul li:hover ul li a {
  color: #333;
}

#navbar ul li:hover ul li:hover {
  background: #e0e0e0;
  color: inherit;
}

#navbar ul li:hover ul li span {
  float: right;
  color: #fff;
  background: var(--primary-color);
  padding: 0.2rem 0.5rem;
  text-align: center;
  font-size: 0.8rem;
  border-radius: 5px;
}

#navbar ul li:hover ul li:hover span {
  background: var(--secondary-color);
}

#showcase {
  display: flex;
  flex-direction: column;
  height: 300px;
  align-items: center;
  justify-content: center;
  text-align: center;
  padding: 0 2rem;
  background: coral;
}

#showcase h1 {
  color: #fff;
  font-size: 4rem;
}

@media(max-width: 600px) {
  #navbar ul li {
    display: block;
  }

  #navbar ul li:hover ul {
    width: 100%;
    position: relative;
  }
}
```