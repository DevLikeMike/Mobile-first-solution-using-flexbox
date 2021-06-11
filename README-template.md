# Frontend Mentor - Interactive pricing component solution

This is a solution to the [Interactive pricing component challenge on Frontend Mentor](https://www.frontendmentor.io/challenges/interactive-pricing-component-t0m8PIyY8). Frontend Mentor challenges help you improve your coding skills by building realistic projects.

## Table of contents

- [Overview](#overview)
  - [The challenge](#the-challenge)
  - [Screenshot](#screenshot)
  - [Links](#links)
- [My process](#my-process)
  - [Built with](#built-with)
  - [What I learned](#what-i-learned)
  - [Continued development](#continued-development)
  - [Useful resources](#useful-resources)
- [Author](#author)
- [Acknowledgments](#acknowledgments)

## Overview

### The challenge

Users should be able to:

- View the optimal layout for the app depending on their device's screen size
- See hover states for all interactive elements on the page
- Use the slider and toggle to see prices for different page view numbers

### Screenshot

![](./screenshot.png)

### Links

- Live Site URL: [HERE](https://your-live-site-url.com)

## My process

### To get started

I start by building my folder system. I use SCSS so I try to build my global styles first then structure my colors into variables, then establishing my media query breakpoints. After my styling is ready to go, I like to build what I call "Helper" classes, essentially classes to quickly make a section flex or justify and align items to the center. These classes help speed up the styling process, but also keey a DRY style sheet.

### Built with

- Mobile-first workflow
- Semantic HTML5 markup
- SCSS
- Minimal Flexbox
- Vanilla JavaScript(Roughly 8 or so lines)

### What I learned

Though this challenge is considered to be a "junior" level two course it had some major take aways. The first being the slider component. The javascript of the range input is very simple, however the styling can be tricky. I opted to create a "progress bar" to show the fill side of the slider, and another empty to lay under the progress bar, only to be covered if the value increases. I feel like this approach is rudimentary, but very effective.

The html like so:

```html
<div class="bar-container">
  <!-- Set value initally to half -->
  <input type="range" min="0" max="30" id="slider" value="15" />
  <div class="emptybar"></div>
  <div class="progressbar"></div>
</div>
```

Styled like this(using SCSS):

```css
/* Container for range input */
.bar-container {
  position: relative;
  width: 100%;
  margin: 2rem auto;

  @include desktop {
    order: 3;
  }

  // SLIDER
  input[type="range"] {
    /* Remove the default range bar */
    -webkit-appearance: none;
    width: 100%;
    height: 10px;
    outline: none;
    border-radius: 9px;
  }
  /* Styles for thumb */
  input[type="range"]::-webkit-slider-thumb {
    -webkit-appearance: none;
    /* Creating the circle with size of 2.8 diameter */
    width: 2.8rem;
    height: 2.8rem;
    border-radius: 50%;
    border: 0;
    /* Set the background to use the arrows given in the images folder */
    background-image: url("../images/icon-slider.svg");
    background-size: fill;
    background-position: center center;
    background-repeat: no-repeat;
    /* Default the background to the dark cyan color */
    background-color: primary(cyan-dark);
    box-shadow: 0 10px 13px primary(cyan-dark);
    /* Transform to better align with range slider input */
    transform: translateY(5px);
    cursor: pointer;
    position: relative;
    /* Make sure thumb is over the progress and empty bar */
    z-index: 3;
  }

  /* Cyan color bar to the left of thumb */
  .progressbar {
    pointer-events: none;
    /* Width is initially set to fifty to match slider value */
    /* Width is adjusted in javascript (see index.html) */
    width: 50%;
    height: 10px;
    background-color: primary(cyan);
    border-radius: 20px;
    /* position to the slider-container element */
    position: absolute;
    left: 0;
    top: 50%;
    /* Position under the thumb but above the empty bar */
    z-index: 2;
  }

  .emptybar {
    pointer-events: none;
    /* Can take full width since its positioned under the rest */
    width: 100%;
    height: 10px;
    background-color: neutral(light-gray-blue1);
    border-radius: 20px;
    /* Position to slider container element, right of thumb */
    position: absolute;
    left: 0;
    top: 50%;
    /* empty < progress < thumb */
    z-index: 1;
  }
}
```

In addition to the slider, the only other "challenging" section of the challenge was moving the "cost" above the range input for desktop. I did this using flex box, and order properties, but it could easily be achieved with grid as well.

### Continued development

In the future, I would plan to better the practices of the slider, and look into libraries for react. Or possibly even create one to assist in styling said input ranges. This was definitely the hardest part of the challenge.

## Author

- Website - [Michael Hall](https://michaelhall.io)
- Frontend Mentor - [@devlikemike](https://www.frontendmentor.io/profile/yourusername)
- Twitter - [@devlikemike](https://www.twitter.com/devlikemike)
- Github - [@devlikemike](https://github.com/DevLikeMike)
