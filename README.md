# CSS Responsive Course: Conquering Responsive Layout

- **Author: Kevin Powell**
- **Course**: [Conquering Responsive Layout 21-Day Challenge](https://courses.kevinpowell.co/courses/conquering-responsive-layouts/)
<!-- - **Written Material**:
- **Repo**:
- **Topics covered**: -->

---

## Concepts

- **HTML/CSS by default is responsive**: It's us (as developers) to insert some CSS code incorrectly that takes away the responsiveness.

---

## Lesson

#### Day 01 - 01 Using percentages for widths(Percentage vs Fixed Widths)

- Use '%' instead of 'fixed widths': Block elements by default are 100% to their parent.

- Set margin to centre the element

```css
.content {
  width: 80%;
  margin: 0 auto;
}
```

#### Day 01 - 02 Avoiding to set heights(Paddings vs Fixed Heights)

- Use 'padding' instead of 'fixed heights'.

---

#### Day 02 - em vs rem

- **Reference video: [CSS em and rem explained](https://www.youtube.com/watch?v=_-aDOAMmDHI&feature=youtu.be)**

- **Reference video**: [Why you shouldn't set font-sizes using em](https://www.youtube.com/watch?time_continue=142&v=pautqDqa54I&feature=emb_logo)

- **em**

  - 'em' always looks for the font size of the parent element. If you didn't set one, by default the browser’s font size is 16px. So if you set 'padding: 5em', it will be '80px (16px \* 5)'.
  - However, if you use 'em' for properties other than font-size (e.g. margins, paddings, widths etc), it looks at the font-size of 'that element (itself)'.

    ```css
    .col--em h1 {
      /* Assume that we didn't set any font-size on the parent element (16px by default) */
      font-size: 2.5em;
      /* Looks at its parent: This would be 40px (16px * 2.5) */
      margin-bottom: 1em;
      /* Looks at 'font-size' in this element: This is also 40px (2.5em * 1) */
    }
    ```

- **rem**
  - To avoid the compounding effects, we use 'rem' (refer to the root element. e.g. the font size in the HTML element)
  - This applies to all the properties (e.g. font-size, margins, paddings, widths).
  - If you want the consistency of spacing (margins) & paddings, then use rem. (If you want to use a more adoptable spacing & paddings, then consider using 'em'.)

**Conclusion**: Using em and rem would be extremely useful with 'media query' (compared to the fixed units 'px'). You might be able to simply change the font-size of the parent element, and all the other properties (paddings, margins) will adapt to different sizes based on the screen sizes.

---

#### Day 03 - Using fixed 'max-width'

- max-width: Set a 'fixed max-width' avoid things scratch out the whole screen when your screen size becomes too large.

---

#### Day 04 - CSS Units: vh, vw, vmin, vmax

- **Reference video: [CSS Units: vh, vw, vmin, vmax](https://www.youtube.com/watch?v=IWFqGsXxJ1E)**

- 'vh' and 'vw' are based on the '% of the viewport' (while '%' in 'width' and 'height' is based on the parent element)

- 'vw' is super handy for setting up the font-size of your titles (it's responsive to your viewport width). You can build a set size of a very small screen and a set size of a very large screen, but anything in between can be tackled by this 'vw'.

```css
.hero-title {
  font-size: 8vw;
}
```

- 'vmin' looks at the smaller of the two units

- 'vmax' looks at the bigger of the two units

#### Day 04 (additional) - Box-sizing

(why everyoen sets 'box-sizing: border-box' to universal selector '\*')

- **Reference video**: [box-sizing: border-box explained](https://www.youtube.com/watch?v=WlGQdgy-M6w)

- By default, box-sizing is set to 'content-box'
- By changing it to 'border-box': paddings and borders will now be included inside the elements (makes your styling more predictable)

```css
* {
  box-sizing: border-box;
}

/* Another way to do it: To avoid accidentally setting 'box-sizing' in certain element to overwrite the universal selector on the top */
* {
  box-sizing: inherit;
}

html {
  box-sizing: border-box;
}
```

- **Additional Reading**: [Inheriting box-sizing Probably Slightly Better Best-Practice](https://css-tricks.com/inheriting-box-sizing-probably-slightly-better-best-practice/)

---

#### Day 05-07 - Challenge #3

- Initial setup of the CSS file

```css
*,
*::before,
*::after {
  box-sizing: border-box;
}

body {
  margin: 0;
}
```

- How to use Google fonts

1. Go to the Google fonts and pick the [font](https://fonts.google.com/specimen/Roboto?sidebar.open&selection.family=Roboto:wght@300;900) and then copy the embedded code.
2. HTML

```html
<link
  href="https://fonts.googleapis.com/css2?family=Roboto:wght@300;900&display=swap"
  rel="stylesheet"
/>
```

3. CSS

```css
.container {
  font-family: "Roboto", sans-serif;
}
```

- Remember to use width (% to parent), margin (0 auto), padding, fixed max-width

- How to style a link as a button

```css
a {
  display: inline-block;
  text-decoration: none;
  text-transform: uppercase;
  background: #38cfd9;
  border: #38cfd9;
  border-radius: 31.5px;
  font-size: 21px;
  font-weight: bold;
  padding: 16px 48px;
  letter-spacing: 0.05em;
  color: black;
}

a:hover,
a:focus {
  opacity: 0.75;
}
```

---

#### Day 08 - Flexbox

- 'display: flex': Change the element to a flex container, and the children elements inside become 'flex items'.
- By default, div has 100% width.
- By default, 'flex-direction' = 'row'.
- By default, flex items want to be as small as they can (depends on the size of the HTML elements inside the div). So by setting 'width: 100%' of 'flex items', the child elements will display equally no matter the content size of the HTML elements.

```css
.row {
  display: flex; /* By setting 'display: flex', we change this element to a flex container */
  flex-direction: row; /* Default: 'flex-direction' = 'row */
}

.col {
  /* these are 'flex items', children of 'flex container' */
  width: 100%;
}
```

- Adding space on flex items: .col + .col

```css
.col + .col {
  /* .col + .col: Only applies to '.col' when it has a '.col' before it (i.e. our 2nd & 3rd .col) */
  margin-left: 30px;
}
```

---

#### Day 09 Ensuring the image is responsive

```css
img {
  max-width: 100%;
}
```

---

#### Day 12 Navigation with Flexbox

Method 1: Add additional class in HTML & CSS

```html
<nav class="nav">
  <ul class="nav__list">
    <li class="nav__item"><a href="#" class="nav__link">Home</a></li>
    <li class="nav__item"><a href="#" class="nav__link">About</a></li>
    <li class="nav__item"><a href="#" class="nav__link">Contact</a></li>
    <li class="nav__item nav__item--push-right">
      <!-- Added a new class 'nav__item--push-right' here -->
      <a href="#" class="nav__link">Sign In</a>
    </li>
    <li class="nav__item">
      <a href="#" class="nav__link nav__link--button">Sign up</a>
    </li>
  </ul>
</nav>
```

```css
.nav__item--push-right {
  margin-left: auto;
}
```

Method 2: Create another nav list in HTML & use flexbox (dispaly & justify-content) in CSS

```html
<nav class="nav">
  <ul class="nav__list">
    <li class="nav__item"><a href="#" class="nav__link">Home</a></li>
    <li class="nav__item"><a href="#" class="nav__link">About</a></li>
    <li class="nav__item"><a href="#" class="nav__link">Contact</a></li>
  </ul>
  <ul class="nav__list">
    <li class="nav__item">
      <a href="#" class="nav__link">Sign In</a>
    </li>
    <li class="nav__item">
      <a href="#" class="nav__link nav__link--button">Sign up</a>
    </li>
  </ul>
</nav>
```

```css
.nav {
  display: flex;
  justify-content: space-between;
}

/* Additional styling to fix the spacing issue (right-most nav item)  */
/* .nav__item {
  margin-right: 1em;
} */

.nav__item + .nav__item {
  margin-left: 1em;
}
```

---

#### Day 13 min(), max(), and clamp()

- Can I use

  - min: https://caniuse.com/#search=min
  - clamp: https://caniuse.com/#search=clamp

- YouTube Video: [min(), max(), and clamp()](https://www.youtube.com/watch?v=U9VF-4euyRo&feature=youtu.be)

- For example, 'width: 70%; max-width: 600px;' can be simplied as 'width: min(600px, 70%);'

- min(): At any given time, the screen will adjust to which one is smaller - '600px' vs '70% width of the parenet element'.
  - In smaller screen sizes, it's '70%' width of the parent element.
  - In bigger screen sizes (when 600px is smaller than '70%' width of the parent element), it's 600px.

```css
.content {
  margin: 0 auto;
  /* width: 70%;
  max-width: 600px; */
  width: min(600px, 70%);
}
```

- max(): Opposite to min(). At any given time, the screen will adjust to which one is bigger - '600px' vs '70% width of the parenet element'.

```css
.content {
  margin: 0 auto;
  /* width: min(600px, 70%); */
  width: max(600px, 70%);
}
```

- clamp(): Must have 3 values (min, ideal-size, max).
  - Probably won't use clamp() with the width a lot, as it will cause issues to set a min-width on smaller screens (mobile).

```css
/* clamp with width */
p {
  background: lightyellow;
  width: clamp(100px, 50%, 200px);
}

/* clamp with font-size */
h1 {
  font-size: clamp(1em, 5vw, 3em);
}
```

---

#### Day 14 More on Flexbox

- YouTube Video: [Flexbox Tutorial Playlist](https://www.youtube.com/playlist?list=PL4-IK0AVhVjMSb9c06AjRlTpvxL3otpUd)

```css
/* Vertically centre a div in your screen */
.container {
  margin: 25vh auto 0;
  /* top: 25vh, bottom: 0, right/left: auto */
  height: 50vh;
  width: 50vw;
}
```

1. Flex containers

- 'display: flex': If you don't turn the div into a flex container, by default it will display the children divs in columns.

- flex-direction (default: row): Once you turn a div into a flex container (without specifying the 'flex-direction'), the children divs (now as 'flex items') will be displayed in rows.

- flex-flow: Shorthand for 'flex-direction' & 'flex-wrap'

- justify-content (default: 'flex-start'): aligns the flexible container's items when the items do not use all available space on the main-axis (on rows if 'flex-direction': row, on columns if 'flex-direction: column')

- align-items (default: 'stretch'): Specifies the default alignment for items inside the flexible container (based on the cross axis).

```css
.container {
  display: flex;
  flex-direction: row; /* row (by default) */
  flex-wrap: nowrap; /* nowrap (by default) */

  /* Shorthand for 'flex-direction' & 'flex-wrap': flex-flow */
  flex-flow: row nowrap;

  justify-content: flex-start; /* flex-start (by default) */
  align-items: stretch; /* stretch (by default) */
}
```

- align-items (baseline): Useful when flex items have different 'font-size' or sidebar

```html
<div class="container">
  <div class="item">Flex item 1</div>
  <div class="item">Flex item 2</div>
  <div class="item">Flex item 3</div>
  <div class="item big">Flex item 4</div>
</div>
```

```css
.container {
  display: flex;
  flex-flow: row nowrap;
  justify-content: flex-start;
  align-items: baseline;
}
```

- align-content (default: stretch): Modifies the behaviour of the flex-wrap property. It is similar to align-items, but instead of aligning flex items, it aligns flex lines.
  - cross-axis
  - Only useful when you have multi-line content ( multiple lines of items)
  - Will overwrite 'align-items'

2. Flex items

- flex-grow (default: 0): Takes up the available space. If set to 0, will stay as the 'flex-basis' size.
- flex-shrink (default: 1): Specifies how the item will shrink relative to the rest of the flexible items inside the same container.
- flex-basis: More like a max-width (will shrink if screen sizes become smaller)
- flex (default: 0 1 auto): sets the flexible length on flexible items and is a shorthand for 'flex-grow', 'flex-shrink' and 'flex-basis'. If the element is not a flexible item, the flex property has no effect.

```css
.one {
  flex-grow: 2;
  flex-shrink: 1;
  flex-basis: 50px;

  /* Shorthand */
  flex: 2 1 50px;

  /* Further Shorthand */
  flex: 50px;
  /* Same as 'flex: 0 1 50px;' because 'flex-grow' and 'flex-shrink' will be set to '1' by default */
}
```

- align-self (default: auto - The element inherits its parent container's align-items property, or "stretch" if it has no parent container): specifies the alignment for the selected item inside the flexible container.

```css
.container {
  display: flex;
  flex-flow: row nowrap;
  align-items: flex-start;
}

.two {
  align-self: flex-end;
}
```

- Order (default: 0): Specifies the order of a flexible item relative to the rest of the flexible items inside the same container. If the element is not a flexible item, the order property has no effect.

```css
.two {
  order: 1;
  /* Item 2 will go to the end, as item 1 and 3 doesn't have an order on it */
  order: 0;
  /* Item 2 will go to its naturally nesting place */
  order: -1;
  /* Item 2 will go to the beginning, as item 1 and 3 doesn't have an order on it */
}
```

3. Flex layout

- Starter file: https://codepen.io/kevinpowell/pen/xrWKBE
- Finished file: https://codepen.io/kevinpowell/pen/xrWKBE

```css
```

```css
```

```css
```

```css
```

---

#### Day 15

```css
```

```css
```

```css
```

```css
```

```css
```

---

©2020 Ellie Chen - All Rights Reserved.
