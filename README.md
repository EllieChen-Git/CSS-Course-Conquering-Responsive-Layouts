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

#### Day 01 - 01 Percentage vs Fixed Widths

- Use '%' instead of 'fixed widths': Block elements by default are 100% to their parent.

#### Day 01 - 02 Paddings vs Fixed Heights

- Use 'padding' instead of 'fixed heights'.

---

#### Day 02 - em vs rem

- **Reference video: [CSS em and rem explained](https://www.youtube.com/watch?v=_-aDOAMmDHI&feature=youtu.be)**

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

#### Day 03 - fixed 'max-width'

- max-width: Set a 'fixed max-width' avoid things scratch out the whole screen when your screen size becomes larger

---

©2020 Ellie Chen - All Rights Reserved.
