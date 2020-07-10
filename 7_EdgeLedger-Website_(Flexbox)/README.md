# EdgeLedger Website:

- Single page. 
- Use flex to align
- Little bit of JS for Google Map and Smooth Scrolling
- Image Overlay (darken the image)
- Sticky Menu
- Styling Fontawesome
- mobile responsive

## Importing Fonts in CSS :
```css
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@300&display=swap');
```

## Removing Space?? 
- Use negative margin/padding

## Line Height:

- normal : A normal line height. This is default	
- number : A number that will be multiplied with the current font-size to set the line height	
- length : A fixed line height in px, pt, cm, etc.	
- %	: A line height in percent of the current font size	
- initial :	Sets this property to its default value. 	
- inherit	: Inherits this property from its parent element. 

```css
div.a {
  line-height: normal;
}

div.b {
  line-height: 1.6;
}

div.c {
  line-height: 80%;
}

div.d {
  line-height: 200%;
}
```