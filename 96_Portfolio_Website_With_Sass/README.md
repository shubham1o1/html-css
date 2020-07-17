# Portfolio Website with Sass

- Multiple Pages (Home, about, contact, work)
- Icons
- Visual Effects using transitions
- Progress Bars (from scratch with HTML and CSS)
- Logos, testimonials
- Image Overlay with transition
- Responsive

## Project Setup:

- Files(CSS, IMG, JS) and Sass's environment (node-sass) setup
- Variable Partials:

```scss
// Variables
$website-width: 1280px;
$main-color: #ffbc00;
$light-color: #f4f4f4;
$dark-color: #333;
$medium-color: #ccc;
$bg-image: url("../img/showcase.jpg");
```

- Bg-image url is set w.r.t main.css file

## Header and Main Nav:

- Anything with class of btn- with be in effect:

```scss
button[class^="btn."]:hover {
}
```

## Specialize and Stats Section

```scss
  // Home section B
  &-b {
    .stats {
      display: grid;
      grid-template-columns: repeat(4, 1fr);

      li {
        line-height: 2;

        &.stats-title {
          font-size: 1.5rem;
        }

        &.state-number {
          font-size: 2rem;
          font-weight: bold;
        }
      }

      div {
        padding-bottom: 3rem;

        &:nth-child(odd) {
          background: $medium-color;
        }
      }
    }
  }
}
```

## Creating Progress Bars:

- HTML

```html
<div class="progress">
  <div style="width: 70%;"></div>
</div>
```

- SCSS

```scss
&-b {
  .progress {
    overflow: hidden;
    height: 20px;
    background: $medium-color;
    border-radius: 5px;
    margin-bottom: 0.6rem;

    div {
      height: 100%;
      color: #fff;
      text-align: center;
      background: $main-color;
    }
  }
}
```

## Responsice Media Queries:

- Stacking repeat(4,1fr) with 1fr for smartphones

```scss
// Stack Grid Columns
#home-a .specials,
#home-b .stats,
#home-c .process,
#about-d .testimonials,
#contact-b .contact-info,
.items {
  grid-template-columns: 1fr;
}
```
