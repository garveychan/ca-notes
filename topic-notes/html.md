#HTML Notes

###Resources
http://getbem.com/naming/ - Naming Best Practice

###Background
- HTML stands for *HyperText Markup Language*.
- It is a declarative language i.e. static.
- It is a *markup* language which is a computer language that defines the structure and presentation of raw text.
- The computer can interpret raw text wrapped in HTML elements.
- *HyperText* is text displayed on a device that provides access to other text through links, also known as *hyperlinks*.
- HTML can then be layered with Cascading Style Sheets (CSS) and JavaScript to create visually compelling and dynamic websites.
- The current standard is **HTML5**.

###Anatomy
- HTML is composed of ***elements***.
- For example, you have a **paragraph element**,  which is made up of: 
    - An **opening** tag -  `<p>`.
    - The **content** - `Hello World!`.
    - A **closing** tag - `</p>`.

``` HTML
<p>Hello World!</p>
```
###Element Structure
- HTML is organised as a collection of family tree relationships.
- When an element is inside another element, it is considered the **child** of that element.
- The **child** is said to be **nested** inside the **parent** element.

``` HTML
<body>
    <p>Hello World!</p>
</body>
```

- In the above example, the paragraph element is the **child**, **nested** within the body element which is the **parent**.
- This can extend to **grandchildren**, **great-grandchildren**, and beyond.
- This relationship can be referred to as the **hierarchy**.

``` HTML
<body>
  <div>
    <h1>Sibling to p, but also grandchild of body</h1>
    <p>Sibling to h1, but also grandchild of body</p>
  </div>
</body>
```

- In the above example, the paragraph and heading elements are **siblings**.
- They are also **grandchildren** of the body element.

###Headings
- There are six different headings, or heading elements.
- `<h1>` through to `<h6>`, from largest to smallest.
- `<h1>` is generally used for main headings and the rest are subheadings.

``` HTML
<h1>This is a Main Heading</h1>
<h3>Subheading 3</h3>
```

###Divisions
- Generally shortened to **div**, this element represents a **container** that divides the page into sections.
- These are useful for grouping your HTML elements together.
- On their own, they don't have specific visual representations, but they prove useful when custom styles are added to our other elements.
- Divisions allow us to **group** certain elements together and apply the same style.
- The division element itself can be styled as a whole with CSS.

``` HTML
<body>
  <div>
    <h1>Why use divs?</h1>
    <p>Great for grouping elements!</p>
  </div>
</body>
```

###Attributes
- Attributes can be added to elements, expanding their **opening tags**.
- They can **provide information**, **change styling**, and other things.
- They are made up of two components - **name** and **value**.
- One common attribute is `id`.
- `id` helps us tag **different content** with the **same element** type.

``` HTML
<div id="intro">
  <h1>Introduction</h1>
</div>
```
###Paragraph/Span
- Displaying text in HTML can be achieved with either a **paragraph** `<p>` or a **span** `<span>`.
- **Paragraph** - Used to divide your content into ***blocks***.
- **Span** - Used to target a specific piece of text ***inline***.

``` HTML
<div>
  <h1>Technology</h1>
</div>
<div>
  <p><span>Self-driving cars</span> are anticipated to replace up to 2 million jobs over the next two decades.</p>
</div>
```

- In the above example, `<span>Self-driving cars</span>` is separated out from the rest of the paragraph.

###Styling

- HTML tags can be used to style text.
- Common ones include `<em>` for <em>italics</em> emphasis and `<strong>` for <strong>bold</strong>.

###Line Breaks
- `<br>` is an unclosed tag which sets a line break.
- This should be used because your browser will not interpret whitespace as spaces. In fact, they may even be collapsed.
- `<hr>` is an unclosed tag / semantic element which can be used to display a horizontal line between paragraph-level elements.

###Lists
- There are two types of lists - **Ordered** and **Unordered**.
    - Unordered Lists:
        - You can use `<ul>` and `<li>` tags to identify unordered lists.
        ``` HTML
        <ul>
            <li>Limes</li>
            <li>Tortillas</li>
            <li>Chicken</li>
        </ul>
        ```
    - Ordered Lists:
        - You can use `<ol>` and `<li>` tags to identify unordered lists.
        ``` HTML
            <ul>
                <li>Preheat the oven to 350 degrees.</li>
                <li>Mix whole wheat flour, baking soda, and salt.</li>
                <li>Cream the butter, sugar in separate bowl.</li>
                <li>Add eggs and vanilla extract to bowl.</li>
            </ul>
        ```

###Images
- The `<img>` tag allows you to add an image to a webpage.
- This tag is a **self-closing** tag.
``` HTML
<img src="image-location.jpg" />
```
- Self-closing tags may include or omit the final slash — both will render properly.

- The `<img>` tag has a **required attribute** - `src`.
- `src` represents the **source** of the image, either a **local address** or a **URL** (Uniform Resource Locator).

#####Image Text
``` HTML
<img src="#" alt="A field of yellow sunflowers" />
```
- The above example shows the use of an `alt` attribute.
- The **alternate attribute** in the example describes the image.
- This attribute is added for any of the following reasons:
    - If the image fails to load, the user can get a description of the image.
    - Visually impaired users can hear the description with a *screen reader*.
    - Search Engine Optimisation can *read* the description.

###Audio and Video
- Similar to the **image** tag, the **audio** and **video** elements can be used to embed audio and video in the webpage.
- These elements require both an **opening** and **closing** tag.

##### Audio

``` HTML
<audio autoplay controls>
  <source src="iAmAnAudioFile.mp3" type="audio/mp3">
</audio>
```
- In the above example, we have used a **source element** to define the audio link. **src** can still be embedded within the **audio element**.
- We have also set **autoplay** so the audio plays immediately and **controls** to provide audio controls.

##### Video
``` HTML
<video src="myVideo.mp4" width="320" height="240" controls autoplay loop>
  Video not supported
</video>
```
- In the above example, 'myVideo.mp4' is the **source**, **width** and **height** denote the **pixel** size of the video in the browser, and **controls** instructs the browser to include basic controls i.e. play, pause, skip.
- **Autoplay** and **Loop** also perform implied functionality.
- The text 'Video not supported' will be displayed if the video cannot be loaded.
- Note that the **source** can be embedded in the **video** element as well.

###Document Structure

#####Declaration
- HTML files must be declared for use in web browsers with a **document type declaration** at the start of each file. Files should also end with the *.html extension.
``` HTML
<!DOCTYPE html>
```
- The HTML file then requires a **HTML element** `<html>` within which structure and content are encapsulated.
``` HTML
<html>
  <!---structure & content--->
</html>
```

#####Head
- The HTML element usually begins with the **Head element** `<head>` which contains your webpage's **metadata**. This data is not displayed on your webpage and is typically used for **Search Engine Optimisation** among other reasons.

``` HTML
<html>
  <head>
    <!--- metadata --->
  </head>
</html>
```

#####Title
- Within the Head element, you will usually find a **Title Element** `<title>` which specifies the title of the browser tab.

``` HTML
<html>
  <head>
    <title>
      <!--- Browser Tab Name --->
    </title>
  </head>
</html>    
```
###Links

- HTML gives you the ability to **link** to other webpages using the **anchor element** `<a>`, otherwise known as a **hyperlink**. You must use the **href attribute** to specify where you wish to link your anchor.

``` HTML
<a href="https://www.google.com">This is a link to Google</a>
```

#####New Tab
- Adding a **target attribute** to the **anchor element** with a value of **"_blank"** allows you to specify that the link opens in a **new tab**.

``` HTML
<a href="https://www.google.com" target="_blank">This link to Google will open in a new tab"</a>
```

#####Relative Links
- You can also use the **href attribute** for **relative links**. These are links to files within the same folder. ```./``` tells the browser to look within the current folder.

``` HTML
<a href="./contact.html">Contact</a>
```

#####Wrapped Link
- With HTML, you can turn almost any element into a link by **wrapping** it with an **anchor element**.

``` HTML
<a href=".contact.html">
  <img src=".contact.png" alt="Contact Button"/>
</a>
``` 

``` HTML
<ul>
  <li><a href="#introduction">Introduction</a></li>
  <li><a href="#habitat">Habitat</a></li>
  <li><a href="#media">Media</a></li>
</ul>
```
- If setting a text link, make sure to wrap the **content** of the element rather than the element itself.

#####Same Page Link
- You can also link to a section of the page but setting an **id** and pointing to it with an **anchor tag**.

``` HTML
<p id="top"></p>

<a href="#top">Link to top paragraph</a>
```

###Document Standards

#####Indentation

- The World Wide Web Consortium (W3C) is responsible for maintaining style standards of HTML. W3C recommends 2 spaces / 1 tab of indentation when writing HTML code.

- Standard convention is to indent every nested element for readability.

``` HTML
<body>
  <h1>Whitespace</h1>    
  <div>
    <p>Whitespace and indentation make html documents easier to read.</p>
  </div>  
</body>
```

#####Comments

- Comments begin with ```<!---``` and end with ```--->```.
- You can turn any line into a comment with **command + /**.

``` HTML
<!--- this is a comment --->
```

###Tables

- Tables can be used to display data.

``` HTML
<table></table>
```

- To display data within the table, we can use the following elements:
  - Table headings ```<th></th>```;
  - Table rows ```<tr></tr>```;
  - Table data ```<td></td>```.

- **Table headings** are used to set headings for both rows and columns. The difference between the two is defined by the **scope attribute** with values of ```"row"``` and ```"col"``` respectively.

``` HTML
<table>
  <tr>
    <th></th>
    <th scope="col">Saturday</th>
    <th scope="col">Sunday</th>
  </tr>
  <tr>
    <th scope="row">Temperature</th>
    <td>73</td>
    <td>81</td>
  </tr>
</table>
```
||Saturday|Sunday|
|---|---|---|
|Temperature|73|81|

- Table headings/data can also span multiple **columns** and **rows** with the ```colspan``` and ```rowspan``` attributes.

*Column span*
```HTML
<table>
  <tr>
    <th>Monday</th>
    <th>Tuesday</th>
    <th>Wednesday</th>
  </tr>
  <tr>
    <td colspan="2">Out of Town</td>
    <td>Back in Town</td>
  </tr>
</table>
```

|Monday|Tuesday|Wednesday|
|---|---|---|
|Out of Town|Out of Town|Back in Town|
Note - in a real HTML table, the 'Out of Town' cells are merged.

*Row span*

``` HTML
<table>
  <tr> <!-- Row 1 -->
    <th></th>
    <th>Saturday</th>
    <th>Sunday</th>
  </tr>
  <tr> <!-- Row 2 -->
    <th>Morning</th>
    <td rowspan="2">Work</td>
    <td rowspan="3">Relax</td>
  </tr>
  <tr> <!-- Row 3 -->
    <th>Afternoon</th>
  </tr>
  <tr> <!-- Row 4 -->
    <th>Evening</th>
    <td>Dinner</td>
  </tr>
</table>
```
||Saturday|Sunday|
|---|---|---|
|Morning|Work|Relax|
|Afternoon|Work|Relax|
|Evening|Dinner|Relax|

Note - in a real HTML table, the duplicate cells are merged.

**Table Head, Body, & Footer**
- Table data should be sectioned accordingly, similar to the overall HTML structure:
  - Head ```<thead>```
  - Body ```<tbody>```
  - Footer ```<tfoot>```

``` HTML
<table>
  <thead>
    <tr>
      <th>Quarter</th>
      <th>Revenue</th>
      <th>Costs</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Q1</th>
      <td>$10M</td>
      <td>$7.5M</td>
    </tr>
    <tr>
      <th>Q2</th>
      <td>$12M</td>
      <td>$5M</td>
    </tr>
  </tbody>
  <tfoot>
    <tr>
      <th>Total</th>
      <td>$22M</td>
      <td>$12.5M</td>
    </tr>
  </tfoot>
</table>
```

#####Styling

- Tables and their elements can be styled in CSS.

``` CSS
table, th, td {
  border: 1px solid black;
  font-family: Arial, sans-serif;
  text-align: center;
}
```

###Forms

#####Form Element
- Form elements can be used to collect information within the browser for processing.
- The **action attribute** determines where the information is sent.
- The **method attribute** is assigned a HTTP verb to be included in the HTTP request.

``` HTML
<form action="/example.html" method="post">
</form>
```

- The form element can also contain child elements.

``` HTML
<form action="/example.html" method="post">
  <h1>Form heading</h1>
  <p>Form paragraph</p>
</form>
```


#####Input Element
- The ```<input>``` element allows a user to input information.
- It does not require a **closing tag**.
<br>
There are several **type attributes** which determine the type of input field generated:
<br>
- With ```type="text"```, the input element will generate a text box for **text input**.
  - Note the **value attribute** can be pre-filled.
  - In the example below, "first-text-field"."already pre-filled" will be sent to "/example.html.
``` HTML
  <input type="text" name="first-text-field" value="already pre-filled">
```
- With ```type="password"```, the input element will generate a text box for **password input**.
``` HTML
  <input type="password" id="user-password" name="user-password">
```
- With ```type="number"```, the input element will be restricted to accepting **numbers only**.
  - Note, with the **step attribute**, we can set an increment for the input box's arrows.
``` HTML
  <input type="number" name="years" id="years" step="1">
```

- With ```type="range"```, you can generate a **slider** which limits the numbers available to the user.
  - You can use the **min** and **max** attributes to dictate the limits of the range.
``` HTML
  <input type="range" name="volume" id="volume" min="0" max="100" step="1">
```

- With ```type="checkbox"```, you can create a **checkbox** input element.
  - The **value attribute** should speak to the value generated by checking the box.

``` HTML
  <input type="checkbox" name="topping" id="pickle" value="pickle">
  <label for="pickle">Pickle</label>
```

- With ```type="radio"``` buttons, you can limit the choices that a user can input.

``` HTML
  <input type="radio" name="answer" id="five" value="five">
  <input type="radio" name="answer" id="two" value="two">
```

##### Dropdown Lists
- With **dropdown lists**, you can present a number of pre-populated options for selection which is simpler than a large number of radio buttons.
- This is done with the `<select>` element.

``` HTML
  <label for="lunch">What's for lunch?</label>
  <select name="lunch" id="lunch">
    <option value="pizza">Pizza</option>
    <option value="curry">Curry</option>
    <option value="salad">Salad</option>
    <option value="ramen">Ramen</option>
    <option value="tacos">Tacos</option>
  </select>
```
- Remember that when the form is submitted, it is the **value** which is sent, not the text.

#####Data Lists
- With **datalists**, you can adapt your input box to auto-populate based on pre-filled data.
- The user can choose to accept one of the options or use their own input.
- This is done with the `<datalist>` and `<option>` elements.
- The **input** attribute must have a `<list>` attribute to point to the **id** of the **datalist**.

``` HTML
  <label for="city">Favourite city?</label>
  <input type="text" list="cities" name="entercity" id="city">
  <datalist id="cities">
    <option value="Sydney">Sydney</option>
    <option value="Canberra">Canberra</option>
    <option value="Brisbane">Brisbane</option>
    <option value="Melbourne">Melbourne</option>
  </datalist>
```

##### Text Areas
- With **textareas**, you can a bigger text field for the user to input a large amount of text.
- This can be done with the `<textarea>` element with size defined by `rows` and `cols` attributes.
- Pre-filled text can be added as content within the element.

``` HTML
<label for="extra">Anything else you want to add?</label>
<br>
<textarea name="extra" id="extra" rows="3" cols="40">Let us know here!</textarea>
```

##### Submitting your form
- To allow a user to submit the form, you simply specify an **input element** with type **submit**.
- The **value attribute** specifies the text which shows on the button. No value specified will default to "Submit".

``` HTML
<input type="submit" value="Send">
```

##### Attribute linking

- The **name attribute** is used to link to the the **value attribute** which is submitted to the **action attribute** in the **form element**.
- I.e. *name + value* will be sent to the *action*.
``` HTML
  <input type="text" name="first-text-field" value="already pre-filled">
```
- The **id attribute** is used to identify an element.


##### Label Element

``` HTML
<form action="/example.html" method="POST">
  <label for="meal">What do you want to eat?</label>
  <br>
  <input type="text" name="food" id="meal">
</form>
```
- The **label element** usually precedes the **input element** and points to the **id attribute** of the **input element** with its **for attribute**.
- In the example above, the label is linked to the input element with the same id 'meal'.
- Clicking on the label element will **focus** the cursor on the associated input element.

###Form Validation
- There are differnet types of validation:
  - Server-side validation - The information is sent to another machine (usually a server) to check if it is valid.
  - Client-side validation - The information is verified in the browser (the client) before it is sent anywhere. An advantage of this is that malicious inputs can be identified before they are sent to the server.

#####Required
- An input can be specified as **required** before any form submission can occur.
- This is done with the `required` attribute in an input element.

``` HTML
<input type="text" name="food" id="food" required>
```

#####Min/Max
- Min and Max attributes can be used to set limit validations on the input.
- See the **Range** type input element for more details.

#####Text Length
- Text length can be limited using the `<minlength>` and `<maxlength>` attributes.

``` HTML
<input id="summary" name="summary" type="text" minlength="5" maxlength="250" required>
```

##### Pattern

- We can use the **pattern** attribute to require an input with a specifically assigned **regular expression (regex)**.
- E.g. we can use `[0-9]{14,16}` to specify that the input requires a **number** with **digits** between 14 and 16.
- Regex conventions can be found at https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions.

``` HTML
<input id="payment" name="payment" type="text" required pattern="[0-9]{14,16}">
```

###Semantic HTML

- Semantic HTML allows identify what specific elements within the code actually does.
- It is used for the following reasons:
  - **Easy to Understand** - provides meaning for humans to interpret.
  - **Accessibility** - allows screen readers and browsers to interpret the code better.
  - **SEO** - Search Engine Optimisation - Search engines can identify content within the page easier and weight the most important content appropriately.
- For example, `<div>` and `<span>` elements carry little meaning as they provide **no context** as to the **content** within the tags.
- `<header>`, `<nav>`, `<main>`, `<article>`, and `<footer>`
- Semantic elements identify the **context** behind the **content**. Examples include:
  - `<header>` - header;
  - `<nav>` - navigation section;
  - `<main>` - main body of the doc;
  - `<article>` & `<aside>` - content which stands on its own (articles, blogs, comments, etc.). An **aside** is information which enhances the article isn't required to understand.
  - `<section>` - section of the doc with items of the same theme (chapters, headings, etc.);
  - `<figure>` & `<figcaption>` - used to encapsulate an image/illustration/etc. with a caption. **Figcaption** will usually go within the figure.
  - `<footer>` - footer. 

#####Semantic Code
``` HTML
<header>
  <h1>
    Everything you need to know about pizza!
  </h1>
</header>
```

#####Non-Semantic Code
``` HTML
<div id="header">
  <h1>
    Everything you need to know about pizza!
  </h1>
</div>
```

