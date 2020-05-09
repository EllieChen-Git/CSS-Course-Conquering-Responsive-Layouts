# CSS Responsive Course: Conquering Responsive Layout

- **Author: Kevin Powell**
- **Course**: [Conquering Responsive Layout 21-Day Challenge](https://courses.kevinpowell.co/courses/conquering-responsive-layouts/)
- **Topics covered**: CSS basics, common & best practices, box-sizing, flexbox, media query, CSS units: 1. em vs rem, 2. vh, vw, vmin, vmax, 3. min(), max() and clamp().

---

## Lessons

- **HTML by default (before we write any CSS) is responsive**: It's us (as developers) to insert some CSS code incorrectly that takes away the responsiveness.

#### Day 01 - 01 Using percentages for widths(Percentage vs Fixed Widths)

- Use '%' instead of 'fixed widths': Block elements by default are 100% to their parent.

- Set margin to centre the element

```css
.content {
  width: 80%;
  margin: 0 auto;
}
```

#### Day 01 - 02 Avoiding setting heights(Paddings vs Fixed Heights)

- Use 'padding' instead of 'fixed heights'.

---

#### Day 02 - em vs rem

- **Reference video: [CSS em and rem explained](https://www.youtube.com/watch?v=_-aDOAMmDHI&feature=youtu.be)**

- **Reference video**: [Why you shouldn't set font-sizes using em](https://www.youtube.com/watch?time_continue=142&v=pautqDqa54I&feature=emb_logo)

- **em**

  - 'em' always looks for the font size of the parent element. If you didn't set one, by default the browser’s font size is 16px. Therefore, if you set 'padding: 5em', it will be '80px (16px \* 5)'.
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

Method 2: Create another nav list in HTML & use flexbox (display & justify-content) in CSS

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

- Finished file: https://codepen.io/kevinpowell/pen/xrWKBE

```css
/* sales-points container: flex container */
.sales-points {
  padding: 12vh 0;
  text-align: center;
  display: flex;
  justify-content: space-around;
  /* space-around: Creates space at the beginning & end of the div */
  flex-direction: column;
  /* Use media query: small screen (row), big screen (column) */
}

@media (min-width: 40rem) {
  .sales-points {
    flex-direction: row;
    /* Use media query: small screen (row), big screen (column) */
  }
}

/* sales-point: flex items */
.sales-point {
  flex-basis: 30%;
  /* Similar to width: 30% */
}
```

---

#### Day 15 Media Query Basics

- Use '@media (min-width:)' for mobile-first design
- Order is important: from smallest min-width to biggest min-width

```css
/* 600px or bigger */
/* Mobile first */
@media (min-width: 600px) {
  .example {
    background: pink;
  }
}

/* 600px or smaller */
/* Desktop first */
@media (max-width: 600px) {
  .example {
    background: green;
  }
}
```

- Refer to changes in Day-12 folder

```css
/* max-width: Desktop first lol */
@media (max-width: 600px) {
  .row {
    display: block;
    /* Change rows from 'display: flex' to 'display: blocks' */
  }

  /* Change the width of all child elements to 100% */
  .hero__text,
  .hero__img,
  .primary-content,
  .sidebar {
    width: 100%;
  }

  /* Add margin-top on the 1st child element */
  .hero__img {
    margin-top: 2em;
  }
}
```

---

#### Day 16 Media Query Breakpoints

How to set the breakpoints:

1. When the website layout starts to break: based breakpoints on content, not devices
2. Find the balance of breakpoints for the whole page (You don't want to set different breakpoints for different sections on the page)
3. Keep it simple (1~2 breakpoints should be enough). Don't over-exhaust yourself. The more breakpoints, the harder to maintain your code.
4. Commonly-used breakpoints: 600px, 960px (but still, refer to point 1, it really depends on how your site looks)

Additional Reading: [The 100% correct way to do CSS breakpoints](https://www.freecodecamp.org/news/the-100-correct-way-to-do-css-breakpoints-88d6a5ba1862/)

- media query is always a range.
- your website’s CSS has a shelf life of about three years

```css
@mixin for-phone-only {
  @media (max-width: 599px) {
    @content;
  }
}
@mixin for-tablet-portrait-up {
  @media (min-width: 600px) {
    @content;
  }
}
@mixin for-tablet-landscape-up {
  @media (min-width: 900px) {
    @content;
  }
}
@mixin for-desktop-up {
  @media (min-width: 1200px) {
    @content;
  }
}
@mixin for-big-desktop-up {
  @media (min-width: 1800px) {
    @content;
  }
}

/* usage */
.my-box {
  padding: 10px;

  @include for-desktop-up {
    padding: 20px;
  }
}
```

---

#### Day 17 Meta Viewport Tag

- Meta Viewport Tag: to ensure that your website is responsive

```html
<head>
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
</head>
```

---

#### Day 18 Flexbox challenge #4 - Solution & Common Practices

- Body: 'margin: 0' and font styles

```css
body {
  margin: 0;
  /* Body font is usually the one you use in most of your paragraphs */
  /* (i.e. Font 4 on design) in this case */
  font-family: "Roboto", sans-serif;
  font-size: 1.3rem;
  line-height: 1.6;
}
```

- Images (set max-width to ensure responsive images): Images will shrink in smaller screens, but not stretch in bigger screens.

```css
/* Make images responsive: */
/* Images will shrink in smaller screens, but not stratch in bigger screens */
img {
  max-width: 100%;
}
```

- Remove margins on bigger heading (h1 & h2): margin: 0;

```css
h1,
h2 {
  margin: 0;
  /* Or at least remove the margin-top */
  margin-top: 0;
}
```

- When setting big font sizes, remember to bring 'line-height' in.

```css
h1,
h2 {
  line-height: 1.1;
}

.intro__title {
  font-size: 60px;
}
```

- In general, the smallest screen size is 320px (iPhone 5), so we need a media query to make sure that our h1 heading size looks ok on mobile.

```css
.intro__title {
  font-size: 3rem;
}

/* Mobile first */
@media (min-width: 800px) {
  .intro__title {
    font-size: 3.75rem;
  }
}
```

- Always remember to add a fixed 'max-width' on the container to avoid text stretch over the screen (common issues in bigger screens)

```css
.container {
  width: 85%;
  margin: 0 auto;
  max-width: 1128px;
}
```

- Setting 'width: 100%' of 'flex items', so the child elements will display equally no matter the content size of the HTML elements.

```css
/* Mobile first */
@media (min-width: 800px) {
  .row {
    display: flex;
  }

  .col {
    width: 100%;
  }

  .col + .col {
    margin-left: 5em;
  }
}
```

- Setting min-height for wrapper & vertically align the heading

  - Min-height takes precedence over both height and max-height ensuring that you get the result you want and that it isn't accidentally overwritten later by a height or max-height call.

  - If you used 'height', then the wrapper will always remain that height even if there's more content. The content will overflow the wrapper and overlap with the footer. The wrapper will not expand to contain the extra content and the footer will not be pushed further down.

```css
.intro {
  min-height: 660px;
  /* Common: header occupies whole screen regardless of the devices */
  /* min-height: 100vh; */
  display: flex;
  align-items: center;
}
```

---

#### CSS Variables - An introduction to CSS custom properties

- YouTube Video: [CSS Variables - An introduction to CSS custom properties](https://www.youtube.com/watch?v=PHO6TBq_auI&feature=youtu.be)
- Definition: Global css properties that can be used throughout the site.
- Syntax: --varaible_namee: value (usually declare in the root selector)

```css
:root {
  --dark-colour: #00bd9d;
  /* Syntax: --varaible_name: value */

  --ff-ss: "Merriweather Sans", sans-serif;

  --mw: 800px;
  --w: 90%;
  --gap: 2em;
}

body {
  color: var(--dark-colour);
  /* Syntax: css_property: var(--varaible_name)*/
  color: var(--dark-colour, steelblue);
  /* Can also add a fallback after it */
}
```

---

#### Day 19 & 20 Mobile navigation challenge

- How to remove list style

```css
ul {
  margin: 0;
  padding: 0;
  list-style: none;
}
```

- Links by default is inline element, so margin-top and margin-bottom won't work on them

```css
.nav__item {
  /* Do it here */
  margin-top: 0.75em;
}

.nav__link {
  /* not here */
}
```

- Create simple hover & focus effects on nav items

```css
.nav__link:hover,
.nav__link:focus {
  opacity: 0.65;
}
```

- Style a nav-link item as button

```css
.nav__link--button {
  /* right-left padding is bigger than top-bottom padding */
  padding: 0.25em 0.75em;
  /* Reverse text-colour & background colour */
  background: #fff;
  color: #23424a;
  /* border-radius: 100px */
  border-radius: 100px;
}
```

- Desktop nav bar style

```css
.nav {
  display: flex;
  align-items: center;
  justify-content: flex-end;
  /* Use flex-end to push all the nav items to the right of the screen */
  position: relative;
}

.nav__item {
  /* Use margin on left to spread the items out */
  margin: 0 0 0 1.5em;
  /* top-right-bottom-left */
}

/* Can also add this to centre the primary nav-list */
.nav__list--primary {
  margin: 0 auto;
}
```

#### Day 21 The Final Challenge

Steps

Done

- Create HTML structure & content
- Set CSS box-sizing
- Create CSS variables for colour consistency
- Set CSS body properties (fonts, margin, paragraph text colour)
- Set CSS containers & apply to HTML: responsive width (%), fixed max-width, center (margin)
- Set CSS image properties: set max-width to ensure responsive images
- Set background colours & text colours for each section

In progress

- Start mobile-first design
- After finishing mobile design, then start table & desktop design

<!-- ---
```css
```

```css
```

```css
```

---

#### Resource

- Free: Kevin Powell - [HTML & CSS Crash Course](https://scrimba.com/course/ghtmlcss)
- \$39: Kevin Powell - [Responsive Web Design Bootcamp](https://scrimba.com/course/gresponsive/) -->

---

©2020 Ellie Chen - All Rights Reserved.
