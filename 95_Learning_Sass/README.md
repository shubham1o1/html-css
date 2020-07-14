# Learning Sass:

## What is Sass?
- Syntactically Awesome Stylesheets
- CSS Preprocessor / Precompiler
- Enhances the functionality of CSS
- Other preprocessors include Less and Stylus
- Allows us to use CSS like a programming language (cut down repeated code, structure things in a more efficient way)

### How does Sass Work?
- Sass usess .scss(*preferred*) or .sass file extensions
- The browser does NOT read Sass, it must be compiled
- Sass files are compiled to normal CSS files
- There are many different types of Sass compilers (cli & gui)
- EG of Compiler: Node Sass(With NPM), Koala(GUI), VSCode Extensions

### What Does Sass Offer?
- *Variables, Conditionals, Nesting, Inheritance, Partials/Imports, Operators & Calculations, Functions & Mixins, Color Functions*
- Nesting helps organize like markup 
- Importing other CSS file is also possible

### .scss vs .sass
- .scss is usually preferred over .sass as it uses the same syntax as regular css
- .sass uses ident for scope definition
![scssvssass](notes-images/scssvssass.png)

## Environment Setup With Node-Sass:
- Install node
- run ```npm init -y``` inside your sandbox folder to create a **package.json** file. 
- Install sass as : ```npm install node-sass```
- Create a script in **package.json**: 
```json
  "scripts": {
    "sass": "node-sass -w scss/ -o dist/css/ --recursive"
  },
```
- So, now we can run sass, watch scss folder and output to dist/css folder

- Running sass so it can constantly watch over the folder: ```npm run sass```
- terminal:

```
_Sass/my-code$ npm run sass

> my-code@1.0.0 sass /home/bomb/Documents/projects/html_css/modern_html_css/95_Learning_Sass/my-code
> node-sass -w scss/ -o dist/css/ --recursive
```

- Pressing ```ctrl+s``` has the following output in console:
```
=> changed: /home/bomb/Documents/projects/html_css/modern_html_css/95_Learning_Sass/my-code/scss/main.scss
Rendering Complete, saving .css file...
Wrote CSS to /home/bomb/Documents/projects/html_css/modern_html_css/95_Learning_Sass/my-code/dist/css/main.css
```
- the file ```main.css``` is created inside ```dist/css``` which is **css** equivalent to **scss**. We include this in our html.
- When you are ready to deploy you just take the dist folder

---

## Koala Sass Compiler 
---<SKipped>---

