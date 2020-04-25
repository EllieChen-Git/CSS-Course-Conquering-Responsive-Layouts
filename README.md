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

<!--


---

#### Day 09

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

```css
```

```css
```

```css
``` -->

---

©2020 Ellie Chen - All Rights Reserved.
