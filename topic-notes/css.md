# CSS Notes

### Resources
http://getbem.com/naming/ - Naming Best Practice

### Background
- CSS or **Cascading Style Sheets** is a language used to **style** HTML content on a web page.
- You can use Chrome DevTools to inspect webpages and analyse its styling (Command + Option + C).

### Anatomy
- In the style sheet, CSS rules - known as **selectors**, can be broken up into the following components:
    - **selector** (the html element being styled)
    - **declaration** (the CSS rule)
        - **property** (the attribute of the CSS rule)
        - **property value** (the value of the attribute)

``` CSS
p { /* selector */
    margin: 10px;  /* declaration */
    font-size: /* property */ 12px;
    color: blue; /* property value */ 
}
```

### Units
- Absolute Units of Measurement
    - `cm` - centimeters
    - `mm` - millimeters
    - `in` - inches (1in = 96px = 2.54cm)
    - `px` - pixels (1px = 1/96th of 1in)
    - `pt` - points (1pt = 1/72 of 1in)
    - `pc` - picas (1pc = 12 pt)

- Relative Units of Measurement
    - `em` - Relative to the font-size of the element (2em means 2 times the size of the current font)	
    - `ex` - Relative to the x-height of the current font (rarely used)	
    - `ch` - Relative to the width of the "0" (zero)	
    - `rem` - Relative to font-size of the root element	
    - `vw` - Relative to 1% of the width of the viewport*	
    - `vh` - Relative to 1% of the height of the viewport*	
    - `vmin` - Relative to 1% of viewport's* smaller dimension	
    - `vmax` - Relative to 1% of viewport's* larger dimension	
    - `%` - Relative to the parent element

### Styling Types

There are 3 types of styling:

##### 1. Inline Styling
``` HTML
<h1 style="color: red;font-size:50px;">Heading</h1>
```

##### 2. Internal Styling
- CSS can also be written within the **style element** which is usually contained within the **head element** of the HTML document.

``` HTML
<html>
    <head>
        <style>
            <!--- CSS Style Selectors --->
            p {
                color: red;
                font-size: 20px;
            }
        </style>
    </head>
</html>
```

##### 3. External Styling
- CSS can be written in a separate **.css file**, allowing HTML and CSS code to be interpreted more easily by humans.
- In order for the HTML file to execute the **.css** style selectors, the **.css** file must be **linked** to the HTML file. This can be done using the **link element** `<link>`.

``` HTML
<link href="css/style.css" type="text/css" rel="stylesheet">
```
- In the above example, the **link element** is linking to the style sheet. The attributes are as follows:
    - **href** - hypertext reference (can be absolute or relative).
    - **type** - the type of document.
    - **rel** - the relationship between the HTML file and the linked file.
- The stylesheet can either be an absolute or relative path.


### CSS Selector Syntax

##### IDs
- HTML element IDs are selected with a `#` prefix.

``` HTML
<h1 id="large-title"> ... </h1>
```
``` CSS
#large-title {
    font-weight: bold;
}
```


##### Classes
- HTML element classes are selected with a `.` prefix.
- e.g. `<p class="brand">Sole Shoe Company</p>` is selected with `.brand`.
<br>

##### Multiple Classes
- HTML elements can have **multiple classes**. This means their styles can be mixed and matched.
``` HTML
<p class= "green bold">This text is green AND bold</P>
```
``` CSS
.green {
    color: green;
}
.bold {
    font-weight: bold;
}
```


##### Elements/Tags
- HTML elements are selected as is without the brackets.
- e.g. `<p>` = `p`, `<h1>` = `h1`, `<article>` = article.

### Combinations

#### Combinators

There are four types of combinations in CSS:
- descendant selector (space)
- child *(direct descendant)* selector (>)
- general sibling selector (~)
- adjacent *(directly following)* sibling selector (+)

##### Chaining

- CSS allows you to chain selectors to identify descendant/sibling elements in your HTML.

``` HTML
<ol class="Favourite-Cuisine">
    <li>Italian</li>
    <li>Thai</li>
    <li>French</li>
</ol>
```
``` CSS
.Favourite-Cuisine li {
    text-transform: capitalize;
}
```

##### Selector Class Chaining

- CSS also allows you to chain selectors in order to refer to specific element/class combinations.

``` HTML
<h1 class="Main">Main Heading</h1>
<h1 class="Sub">Subheading</h1>
```

``` CSS
h1.Sub {
    font-weight: 500;
}
```

- You can also specify elements which **follow** other elements using `+`.

``` CSS
h1 + p {
    color: black;
}
```

##### Unrelated Selectors

- Unrelated selectors can be assigned the same properties and values.
- They can be separated with a **comma** for brevity.

``` CSS
h1, 
p,
.title,
#special {
font-family: Georgia;
}
```

### Specificity

- Best practice in CSS is to style elements while using the **lowest degree** of specificity, so that if an element needs a new style, it is easy to override.
- Therefore, it's best to start styling with your most **common** styles and work down.
- As a general rule of thumb, the more specific a selector, the higher priority.
- e.g. nested elements under a class will take precedence over a selector of just the element - `.class <tag>` > `<tag>`.

##### !Important Rule
In addition to all other specificity rules, `!important` will override **everything** already assigned to the selector.

``` CSS
p.corrections {
    color: red !important;
}
```

##### Priority Order

- `!Important` Rule
- Inline Styling
- Embedded (.html) and External Styling (.css)
    - IDs
    - Classes
    - Elements/Tags

###Common Visual Rules

- `font-family` - Set Typeface
    - Times New Roman (HTML Default)
    - Courier New
    - Garamond
    - etc.
    - Try to limit a page to 2 or 3 typefaces.
    - Use `" "` for typefaces with spaces like `"Courier New"`.

- `font-size` - Set font size
    - 1px - 1 pixel
    - 1em - 1 unit (proportionate)

- `font-weight` - Set font weight
    - normal
    - bold
    - bolder
    - lighter
    - 0 - 900 (400 normal)

- `text-align` - Align text to **parent** element
    - left
    - center
    - right

- `color` - foreground color
- `background-color` - background color
- `opacity` - transparency of element
    - 0 - invisible
    - 1 - fully visible
    - 0 - 1
- `background-image` - set an image as a background
    - url("relative/absolute link")
- `list-style` - set bullet point style
    - circle
    - square

### Box Model

- All HTML elements are contained within a 'box'.
- This 'box' can be adjusted to suit your styling requirements.
- The components of the 'box' from inside to out are:
    - content
    - padding
    - border
    - margin

##### Common Properties

- `height`/`width` - control the size of the box
- `padding` - adjust the area surrounding the content.
    - This property accepts any unit of measure, e.g. px, em, etc.
    - You can specify the side with `padding-left`, `padding-right`, `padding-top`, or `padding-bottom`.
    - You can also just use `padding` with the side values in **clockwise order** - see below.

``` CSS
p.content-header {
  padding: 6px 11px 4px 9px;
  /* (top, right, bottom, left) */
}

p.content-header {
  padding: 5px 10px;
  /* (top&bottom,left&right) */
} 
```

- `border` - style the box border
    - *width* - thin, *medium*, thick, #px
    - *style* - *none*, dotted, solid
    - *color* - *color*
- `border-radius` - style the corners of the box - this can be used to turn the box into a circle if the radius matches half the width and height.

- `margin` - refers to the space just outside the box after padding and border.
    - Just like `padding`, margin can be specified with `margin-left`, `margin-top`, etc.
    - And just like `padding`, the same shortcuts can be used to put measurements in the `margin` attribute itself if all 4 sides need to be specified.
    - `margin` lets you center the element but you have to set a width for the element so it does not take up the full width of the page.

``` CSS
div.headline {
  width: 400px;
  margin: 0 auto;
  /* 0 sets top and bottom margin to 0 */
  /* auto sets left and right margins to center the 'headline' */
}
```

- Important note - With **adjacent margins**, top and bottom `margin`s will be **collapsed** while left and right `margin`s are added. The larger of the top and bottom `margin`s will be taken as the space between the elements.

- `min`/`max` `width`/`height` - elements can have limits placed on their size using min/max width/height when the browser is resized.
- Handy tip - You can use % view width and height to autofit the max width and height - `100vw` & `100vh`.

##### Overflow

The overflow property specifies what happens to an element's content if it exceeds the confines of its 'box'.

There are three properties:
- hidden - The overflowing content is no longer visible.
- scroll - A scrollbar appears for the user to scroll to view the full content.
- visible - The content flows outside of its box (This is the **default** setting).

##### Default Stylesheets (User Agent)

- Major web browsers often have *user agent* stylesheets which set **default** values for certain elements.
- It is best practice to start your stylesheet with the following code to give yourself a **clean slate** to work with.

``` CSS
* {
  margin: 0;
  padding: 0;
}
```

##### Display & Visibility

- Elements can be set as **visible** or **hidden** with the `visibility` property.
- Note the browser will still leave a space where the element is hidden.
- This is different from `Display: none` which removes the element entirely.

### Box Sizing

- A common problem with boxes is that the default setting is for them to be **sized in addition** to the content.
- I.e. the padding, border and margins are added on top of the content so it makes it difficult to track the dimensions of the box.
- This behaviour is set by the `box-sizing` property.
- The **default** value is `content-box` which is where the padding, border, margins are added to the content.
- We can change this to `border-box` to preserve the margins, padding, border specified in our declaration. The **content** will then **autofit** itself.

``` CSS
* {
  box-sizing: border-box;
}
/* Added to top of stylesheet. */
```

### Adjusting HTML Flow

- HTML generates elements based on position in code, from left to right and top to bottom.
- There are 5 CSS properties which can adjust how HTML elements are positioned:
    - `position`
    - `display`
    - `z-index`
    - `float`
    - `clear`

##### Position

- Block level elements like a div will default to the top left.
- This default can be changed by setting its `position` property in CSS with one of the four following values:
    - `static` - Default
    - `relative`
    - `absolute`
    - `fixed`   
- `relative` positioning requires **offset** properties and corresponding values (%, px, em). It offsets the element from its **default** position.
    - `top` - moves element down.
    - `bottom` - moves element up.
    - `left` - moves element right.
    - `right` - moves element left.
- `absolute` positioning requires the same **offset** properties. It sets the position offset relative to the nearest **non-static element**.
    - the element will still move when the page scrolls.
- `fixed` positioning ties the element to a position on the **page**.
    - the element will remain fixed no matter how you scroll.

##### Z-index

- Z-index property sets the level of **depth** for an element.
- The **greater** the z-index, the **greater** the priority.
- Note the **position** of the element must be **relative** to be adjusted.

##### Display

- Display property dictates if an element can share horizontal space with other elements.
- The most important three values are:
    - inline
    - block
    - inline-block
    - flex

- **Inline elements** have a box that wraps tightly around their content, only taking up the amount of space necessary to display their content and not requiring a new line after each element.
    - You cannot set their height/width.
    - Any element can be turned into an inline element (even paragraphs and divs).

``` CSS
h1 {
  display: inline;
}
```

- **Block elements** fill the entire width of the page by default. Examples include div, header, footer.
    - You can turn inline elements into block elements.

``` CSS
strong {
  display: block;
}
```

- **Inline-block** elements combine features of both inline and block elements. They are essentially blocks that can appear next to each other.
    - The example below renders three rectangle blocks side by side.
``` HTML
<div class="rectangle">
  <p>I’m a rectangle!</p>
</div>
<div class="rectangle">
  <p>So am I!</p>
</div>
<div class="rectangle">
  <p>Me three!</p>
</div>
```
``` CSS
.rectangle {
  display: inline-block;
  width: 200px;
  height: 300px;
}
```

##### Float

- The `float` property can be used to simply set an element as far **left** or as far **right** as possible.
    - `left` or `right` - property values.
    - Note width must be specified or the block will automatically assume the full width of the page and float will do nothing.

##### Clear

- Float elements can bump into each other on the page if they have different heights.
- The `clear` property allows us to specify how they behave if they do bump into one another.
    - `left` - left side of the element will not touch any other element within the same containing element.
    - `right` - right side of the element will not touch any other element within the same containing element.
    - `both` - neither side of the element will touch another element.
    - `none` - the element can touch either side.

### Colors

- Colors in CSS can be described in 3 ways:
    - Named (Red)
    - Hex (#FFFFF) 
    - RGB (Red, Green, Blue) (255,255,255)
    - HSLA (Hue [0-360], Saturation [%], Lightness [%], Alpha [0-1])

- There are two types of color properties:
    - color (foreground)
    - background-color (background)

- You can also use `transparent` as a value to set zero opacity.

### Typography

- Typography is the art of arranging text on a page.
- `font-family` allows you to change the **typeface** of text.
    - Note when setting fonts, they must be installed on a user's computer.
    - The default HTML font is Times New Roman.
    - Limit fonts to 2 or 3 a page.
    - Double quotes are needed for fonts with spaces e.g. "Courier New".
- `font-weight` lets you set thin/thickness of font.
    - values include `normal`, `bold`, `bolder`, `lighter`, 0-900 (400 is normal).
- `font-style` lets you set the style of the font.
    - values include `normal`, `italic`, `oblique`.
- `word-spacing` adds spacing between your words.
    - the default is `0.25em` or `normal` and any value you specify will be **added** to this.
- `letter-spacing` or **tracking** is for setting space between characters.
- `text-transform` lets you transform the text with the following values:
    - capitalize
    - uppercase
    - lowercase
- `text-align` lets you set text alignment:
    - left
    - center
    - right
- `line-height` sets the height of the line.
    - the difference between the font size and the line height is called **leading**.
    - the property can take either a **unitless** number as a ratio of the font size or px, em, rem, etc.

##### Serif vs Sans Serif
- Serif has fancy strokes on ends of letters while Sans Serif omits them.

##### Fallback Fonts
- Fallback fonts are used if the specified typeface is not installed on the user's computer.

``` CSS
h1 {
  font-family: "Garamond", "Times", serif;
  /* If Garamond not installed use Times, */
  /* If Times not installed, use serif. */
}
```

##### Google Fonts
- You can use Google fonts to link to the font family for the user to download into their browser.

``` CSS
<head>
  <link href="https://fonts.googleapis.com/css2?family=Open+Sans:ital,wght@0,400;0,700;1,700&family=Playfair+Display:ital,wght@0,400;0,700;1,900" rel="stylesheet">
</head>
```

##### @Font-face
- You can also load fonts using the `@font-face` selector from absolute and relative paths.

``` CSS
/* latin */
@font-face {
  font-family: 'Space Mono';
  font-style: normal;
  font-weight: 700;
  src: url(https://fonts.gstatic.com/s/spacemono/v6/i7dMIFZifjKcF5UAWdDRaPpZUFWaHi6WZ3Q.woff2) format('woff2');
  unicode-range: U+0000-00FF, U+0131, U+0152-0153, U+02BB-02BC, U+02C6, U+02DA, U+02DC, U+2000-206F, U+2074, U+20AC, U+2122, U+2191, U+2193, U+2212, U+2215, U+FEFF, U+FFFD;
}
```

``` CSS
@font-face {
  font-family: 'Glegoo';
  font-style: normal;
  font-weight: 700;
  src: url(../fonts/Glegoo-Regular.ttf) format('truetype');
}
```

### Flexbox
- Flexible Box Layout, is a new tool developed for CSS which allows for simplified positioning of elements, whether individually or in groups.
- Flex containers have **two axes**:
    - Main axis (x - horizontal)
    - Cross axis (y - vertical)
- There are two components of a flexbox:
    - The flex items (Child elements of the flex container).
    - The flex container (The element which contains the flex items).
- Flexbox is set with the ```display``` property:

``` CSS
display:flex;
display:inline-flex;
```

- Inline-flex is similar to inline-block in that it allows multiple flex containers which behave like blocks on one line.

##### Justify Content (Horizontally)
- `justify-content` allows us to adjust positioning of our flex items on the main axis (left to right).
    - `flex-start` - items start from left with no space between.
    - `flex-end` - items start from right with no space between.
    - `center` - items centered with no space between.
    - `space-around` - items positioned with equal space before and after.
    - `space-between` - items positioned with equal space between them.
- This property does not change the size of the flex items.

##### Align Items (Vertically)
- `align-items` allows us to space flex items vertically.
    - `flex-start` - items start from the top of the parent container.
    - `flex-end` - items start from the bottom of the parent container.
    - `center` - items centered in the parent container.
    - `baseline` - aligns the bottom of each item i.e. 'baselines' them.
    - `stretch` - if possible, stretches each item from top to bottom (**will not** stretch items with specified height).
- This is predominantly for aligning elements within a single row.

##### Align Content (Vertically) - declared on flex containers
- Similar to how `align-items` let us align items on a single line, `align-content` allows us to space multiple lines in the flexbox.
    - `flex-start` - rows start from left with no space between.
    - `flex-end` - rows start from right with no space between.
    - `center` - rows centered with no space between.
    - `space-around` - rows positioned with equal space before and after.
    - `space-between` - rows positioned with equal space between them.

##### Flex Grow (Horizontally)
- Flex items will shrink proportionally when the flex container is too small.
- However, they will **not** expand if the container is larger as the **default value** of flex grow is **0**.
- `flex-grow` lets us specify if they should 'grow' to fill the space or not.
    - The value assigned to `flex-grow` is a number which specifies the **ratio** at which it grows compared to the other flex items.

``` CSS
.container {
  display: flex;
}
 
.side {
  width: 100px;
  flex-grow: 1;
}
 
.center {
  width: 100px;
  flex-grow: 2;
}
```
- In the above example, the center class will grow twice as much as the side class.
- The item **will not** grow if a `max-width` has been set.


##### Flex Shrink (Horizontally)
- `flex-shrink` specifies how a flex item shrinks when the container is too small.
- The default behaviour is for a flex item to shrink because the **default value** of this property is **1**.
- Remember, `min-width` takes precedence over `flex-shrink`.

``` CSS
.container {
  display: flex;
}
 
.side {
  width: 100px;
  flex-shrink: 1;
}
 
.center {
  width: 100px;
  flex-shrink: 2;
}
```
- In the above example, the center class will shrink **twice** as much as the side class.

##### Flex Basis (Horizontally)
- `flex-basis` lets us set the width of the flex item **before** it grows or shrinks.

``` CSS
.container {
  display: flex;
}
 
.side {
  flex-grow: 1;
  flex-basis: 100px;
}
 
.center {
  flex-grow: 2;
  flex-basis: 150px;
}
```

##### Flex Property (Horizontally)
- The `flex` property lets you set `flex-grow`, `flex-shrink`, and `flex-basis` all in one line (in that order).
- Note this is not to be confused with the `flex` value for the `display` property.

``` CSS
.small {
  flex: 1 2 100px;
}
```

##### Flex Wrap (Horizontally)
- `flex-wrap` allows us to specify how the flex items will **wrap** onto the next line rather than shrink within the existing one.
    - `wrap` - child elements that don't fit will wrap to the next line.
    - `wrap-reverse` - wrapped elements but from the bottom up i.e. first line becomes the last line.
    - `nowrap` - Prevents items from wrapping (**Default**).

##### Flex Direction
- `flex-direction` lets us adjust the main (horizontal) and cross (vertical) axes of the flex container.
    - `row` - **Default**, items positioned **left to right** starting in the **top left**.
    - `row-reverse` - Items positioned **right to left** starting in the **top right**.
    - `column` - Items positioned from **top to bottom** starting in the **top left**.
    - `column-reverse` - Items positioned from **bottom to top** starting in the **bottom left**.
- Note that changing the axes will change the **behaviour** of the other flex properties.

##### Flex Flow
- `flex-flow` lets you set the `flex-wrap` and `flex-direction` properties in one line.

``` CSS
div {
    flex-flow: column wrap;
}
```

##### Nested Flex
- Flex containers can be nested in other flex containers.

### Grids
- Grids are a powerful tool for us to lay out entire webpages.
- They are made up of **containers** and **items**.
- Grids are set with the `display` property.

``` CSS
.grid {
    display:grid;
}
```

- You can also set grids to be **inline** with `inline-grid`.

##### Columns
- By default, grids contain **one** column.
- To change this, we use `grid-template-columns` to define the **number** of columns and their **width**.

``` CSS
.grid {
  display: grid;
  width: 100px;
  grid-template-columns: 20px 40% 60px;
}
```

- In the above example, we have a middle column at **40% of 100px = 40px** flanked by columns of 20px and 60px width respectively.
- Note this will cause overflow, to be handled with another grid function.

##### Rows
- Rows are defined exactly like columns but with height.

##### Grid Template
- The `grid-template` property can be used to define both **rows** and **columns** at once!
- Note, **rows** come before **columns** and are separated by a forward slash `/` - think x and y.

``` CSS
.grid {
  display: grid;
  width: 1000px;
  height: 500px;
  grid-template: 200px 300px / 20% 10% 70%;
}
```

#####Fractions
- It's a good idea to use **fraction** units to specify height/width to stop elements from overflowing.
- Note the values can still contain **pixels** and other units with **fractions**. In this case, the fractions will be of the **remaining** space.

``` CSS
.grid {
  display: grid;
  width: 1000px;
  height: 400px;
  grid-template: 2fr 1fr 1fr / 1fr 60px 1fr;
}
```

##### Repeat()
- The **repeat()** function allows us to specify several repetitions of a **set** of rows or columns.

``` CSS
.grid {
  display: grid;
  width: 300px;
  grid-template-columns: repeat(3, 100px, 50px);
}
```

##### Minmax
- The **minmax** function allows us to set a **minimum** value and **maximum** value for heights/widths.

``` CSS
.grid {
  display: grid;
  grid-template-columns: 100px minmax(100px, 500px) 100px;
}
```

##### Grid Gaps
- **Grid gaps** can be specified to leave **space** between rows or columns.
    - `grid-row-gap` - specify row gap.
    - `grid-column-gap` - specify column gap.
    - `grid-gap` - used to specify both row and column gaps (respectively).
- Remember that if using **fractions**, they'll use the **available** space, **excluding** any gaps.

``` CSS
.grid {
    grid-gap: 20px 5px;
    /* grid gap: rows columns */
}
```
##### Multiple Grid Sections
- Grid items can span more than one section of the grid.
- You can either designate rows and cols separately or use **grid area** to define it all at once.
- Note, the starting row/column is **1**.
- To set an item to span more than one row or column, you can use:
    - `grid-row-start` - Sets the first **grid line** for your row.
    - `grid-row-end` - Sets the last **grid line** for your row.
    - `grid-row` - Shorthand to set both start and end for your row.
    - `grid-column-start` - Sets the first **grid line** for your column.
    - `grid-column-end` - Sets the last **grid line** for your column.
    - `grid-column` - Shorthand to set both the start and end for your column.
    - Remember we are applying these to grid **items** now, not the **grid** itself.

``` CSS
.item {
  grid-row: 4 / 6;
  /* grid row: start / end; */
}
```
- Note we can also use `span` to determine the **delta** rather than the **end** grid line.

``` CSS
.item {
  grid-row: 4 / span 2;
}

.item {
  grid-row: span 2 / 6;
}
```
- The span examples are exactly the same as the one at the top.

- To make life easier, you can use the **Grid Area** property to designate both row and column values.
    - Syntax is as follows:

``` CSS
.item {
  grid-area: 2 / 2 / 2 / 2;
  /* grid area: row start / col start / row end / col end ; */
}
```

### Advanced Grid

##### Grid Template Areas

- To simplify the process allocating different sections of the grid, we can use `grid-template-areas` to specify the **names** of each section:

``` CSS
.container {
  display: grid;
  max-width: 900px;
  position: relative;
  margin: auto;
  grid-template-areas: "head head"
                       "nav nav" 
                       "info services"
                       "footer footer";
  grid-template-rows: 300px 120px 800px 120px;
  grid-template-columns: 1fr 3fr; 
}
 
header {
  grid-area: head;
} 
 
nav {
  grid-area: nav;
} 
 
.info {
  grid-area: info;
} 
 
.services {
  grid-area: services;
}
 
footer {
  grid-area: footer;
} 
```

##### Grid Overlap

- Grid areas can overlap using grid lines and areas.
- Remember you can use `z-index` to determine the depth of each item.

##### Justify Items
- `justify-items` is a property that positions grid **items** along the inline, or row, axis. This means that it positions items from left to right across the web page.
- The most common values that `justify-items` accepts are:    
    - `start` — aligns grid items to the left side of the grid area (default).
    - `end` — aligns grid items to the right side of the grid area.
    - `center` — aligns grid items to the center of the grid area.
    - `stretch` — stretches all items to fill the grid area.

##### Justify Content
- `justify-content` is a property that positions grid **columns** within the **grid container**.
- You would apply this property to grid containers to specify how its items are aligned horizontally.
- You can also use the following values to specify the **space** around the grid items:
    - `start` — aligns grid columns to the left side of the grid area (default).
    - `end` — aligns grid columns to the right side of the grid area.
    - `center` — aligns grid columns to the center of the grid area.
    - `stretch` - stretches grid columns to fill the grid area.
    - `space-around` - equal amount of space around each item (there will be double the space between each item as they add up).
    - `space-between` - equal amount of space between each item (no space on either end).
    - `space-evenly` - equal amount of space between each item and at each end.

##### Align Items
- `align-items` is a property that positions grid **items** vertically within the **row**.
- The most common values that `align-items` accepts are:    
    - `start` — aligns grid items to the top of the grid area (**default**).
    - `end` — aligns grid items to the bottom of the grid area.
    - `center` — aligns grid items to the center of the grid area.
    - `stretch` — stretches all items to fill the grid area.

##### Align Content
- `align-content` is a property that positions grid **rows** within the **grid container**.
- You would apply this property to grid containers to specify how its items are aligned vertically.
- You can also use the following values to specify the **space** around the grid items:
    - `start` — aligns grid rows to the top of the grid area.
    - `end` — aligns grid rows to the bottom of the grid area.
    - `center` — aligns grid rows to the center of the grid area.
    - `stretch` — stretches all rows to fill the grid area (**default**).
    - `space-around` - equal amount of space around each item (there will be double the space between each item as they add up).
    - `space-between` - equal amount of space between each item (no space on either end).
    - `space-evenly` - equal amount of space between each item and at each end.

##### Justify and Align Self
- `justify-self` (row axis) and `align-self` (column-axis) will are **grid item** level properties which override the positioning specified at the container level.
- They will accept the following values:
    - `start` — positions grid items on the left side/top of the grid area.
    - `end` — positions grid items on the right side/bottom of the grid area.
    - `center` — positions grid items on the center of the grid area.
    - `stretch` — positions grid items to fill the grid area.

##### Implicit vs Explicit Grid
- We have thus far been **explicitly** defining the dimensions and behaviour of the grid.
- Changes may occur to the webpage which throw this out e.g. a list of products is expanded and covers 30 items whereas we've defined a grid of 15.
- In this case, CSS has a built-in **implicit** grid which defines the default behaviour in these scenarios.
- There are two properties to specify the size of grid tracks added **implicitly**:
    - `grid-auto-rows` - height of implicitly added rows.
    - `grid-auto-columns` - width of implicity added columns.
- These **auto** properties will accept the same units as `grid-template-rows` and `grid-template-columns`.
    - e.g. %, px, fr, repeat(), etc.
- There is also the `grid-auto-flow` property which can be used to specify the **flow behaviour** of newly added items:
- Its values are as follows:    
    - `row` — specifies the new elements should fill rows from left to right and create new rows when there are too many elements (**default**).
    - `column` — specifies the new elements should fill columns from top to bottom and create new columns when there are too many elements.
    - `dense` — this keyword invokes an algorithm that attempts to fill holes earlier in the grid layout if smaller elements are added.
    - You can also pair row and column with dense e.g. `grid-auto-flow: row dense;`.

### Transitions
- CSS allows us to specify how elements can **change** through the course of viewing the webpage.
- These are called **CSS transitions** and are a type of **state change**.
- We can control the following four aspects of an element's transition:
    - Which CSS properties transition.
    - How long a transition lasts.
    - How much time there is before a transition begins.
    - How a transition accelerates.

##### Duration
- To create a simple transition in CSS, we must specify two of the four aspects:
    - `transition-property` - The property that we want to transition.
    - `transition-duration` - The duration of the transition.

``` CSS
a {
  transition-property: color;
  transition-duration: 1s;
}
```

- Different properties transition in different ways, for example:
    - Color values, like color and background-color, will blend to a new color.
    - Length values like font-size, width, and height will grow or shrink.

- Duration is **defaulted** to **zero**.

##### Delay

- Much like duration, `transition-delay` can be specified to tell the transition to **wait** before starting.
- The **default** is also **zero**.

##### Timing Function
- The `transition-timing-function` describes the **pace** of the transition.
- Values include:
    - `ease` - start slow, speeds up in middle, slows down (**default**).
    - `ease-in` — starts slow, accelerates quickly, stops abruptly.
    - `ease-out` — begins abruptly, slows down, and ends slowly
    - `ease-in-out` — starts slow, gets fast in the middle, and ends slowly
    - `linear` — constant speed throughout

##### Transition Shorthand
- We can use `transition` to shorthand all of the above properties.
- They are specified in the following order: 
    - `transition-property`
    - `transition-duration`
    - `transition-timing-function`
    - `transition-delay`

``` CSS
transition: color 1.5s linear 0.5s;
```

- You can also **combine** elements using a **comma** `,`.
``` CSS
transition: color 1s linear, font-size 750ms ease-in 100ms;
```

- You can also use `all` to target **all properties** related to a selector's **state change**.
``` CSS
transition: all 1.5s linear 0.5s;
```
