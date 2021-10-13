# Reading Notes 01:  Introductory HTML and JavaScript

## HTML

Browsers interpret plain text documents filled with HTML (HyperText Markup Language) stored on servers across the globe. There is nothing special about the document, it doesn't get compiled and it's not a binary file. Essentially a website can be built with a computer and a text editor. 

### Structure

#### Tags

HTML tags describe the structure of a webpage. Structural elements have both a opening tag and a closing tag. e.g. `<sometag>somecontent</sometag>` 


- `<head>` Comes before the body and is used to hold the title and meta data tags. Not visible in the main area of the webpage.
- `<title>` Defines the title of the webpage that is displayed in the browser tab.
- `<body>` Everything here is shown in the main browser widow.
- `<h1>` through `<h6>` Defines headings from the most important `<h1>` and decreasing in importance down to `<h6>`
- `<p>` Defines a paragraph of text.

Code excerpt from the book:

```html
<html>
  <body>
    <h1>This is the Main Heading</h1>
    <p>This text might be an introduction to the rest of the page. And if the page is a long one it might be split up into several sub-headings.<p>
    <h2>This is a Sub-Heading</h2>
    <p>Many long articles have sub-headings so to help you follow the structure of what is being written. There may even be sub-sub-headings (or lower-level headings).
    </p>
    <h2>Another Sub-Heading</h2>
    <p>Here you can see another sub-heading.</p>
  </body>
</html>
```

#### Attributes

Attributes are for giving extra information to elements. They fit inside of the opening tag and use a `keyword="value"` syntax, e.g. `<p lang="en-us">Paragraph in English</p>`

### Extra Markup

#### Doctypes

The doctype declaration is the very first line of the page and it lets the browser know which version of HTML we're dealing with here. Modern sites built with HTML5 will use `<!DOCTYPE html>` instead of longer doctype declarations for earlier versions of HTML that included links to the w3.org website.

#### Comments

Commenting code is a great way to document anything that is not generally obvious about your page. Comments do not show when the page is rendered with the browser but they are not private, anyone can view the source of the page where the comments are visible.

Code excerpt from the book:

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Comments in HTML</title>
  </head>
  <body>
    <!-- start of introduction -->
    <h1>Current Exhibitions</h1>
    <h2>Olafur Eliasson</h2>
    <!-- end of introduction -->
    <!-- start of main text -->
    <p>Olafur Eliasson was born in Copenhagen, Denmark in 1967 to Icelandic parents.</p>
    <p>He is known for sculptures and large-scale installation art employing elemental materials such as light, water, and air temperature to enhance the viewer's experience.</p>
    <!-- end of main text -->
    <!-- <a href="mailto:info@example.org">Contact</a> -->
  </body>
</html>
```

#### ID Attribute

The ID attribute lets you identify a unique element. This can be useful when referencing the element for styling with CSS or grabbing it for use in script. Elements can not share the same ID, each one must be unique.

`<p id="myUniqueParargraph">unique content</p>`

#### Class Attributes

Class attributes can be used in similar ways to ID attributes. Class attributes however can be assigned to more than one element, making them a way to group elements together for styling with CSS or working with in scripts. Elements can even belong to more than one class.

`<p class="important">important content</p>`

#### Behavior

##### Block Elements

Block level elements always begin a new line and don't, by default, sit side-by-side with other block elements. Visually they stack on one another in the browser window.

Examples:

- `<h1>`
- `<p>`
- `<ul>`
- `<li>`
- `<div>`

##### Inline Elements

Inline elements appear in-line with other elements. They don't cause a line break so they can fit right in with other content without interrupting a paragraph or list.

Examples:

- `<a>`
- `<em>`
- `<img>`
- `<span>`
- `<input>`


#### Grouping

##### DIV

The non-semantic element `<div>` can be used as a container to hold other elements especially for styling or other non-semantic uses. In the past `<div>` elements were used for structuring, styling, and organization but with [HTML5](#html5-layout) they can be reserved for those times when you need to style a specific group of elements that are not connected semantically.

##### SPAN

Similar to the way `<div>` elements have been historically overused the `<span>` element can be seen as the `<div>`'s counterpart. These elements can be used to give style to a group of inline content when no semantic meaning is required.

#### IFrames

The `<iframe>` or "inline frame" tag can be used to insert another webpage into your own page. This is commonly seen when embedding a map, and external app, or external media player. They can also be used for displaying parts of your own site (not only external pages).


#### Metadata

The `<meta>` tag is used in the document `<head>` and holds information about the webpage. Like other elements in the `<head>` metadata doesn't appear in the body of the page itself. There are a number of attributes that can be used with the `<meta>` tag. The name and content attributes are often used jointly to describe things like the page encoding, the author of the page, and how the page itself responds to be being resized.

Example :

```html
<head>
  <meta charset="utf-8" />
  <meta name="author" content="Ben Mills" />
  <meta name="description" content="Personal website of Ben Mills" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />

  <!-- Favicon: -->
  <link rel="apple-touch-icon" sizes="180x180" href="/apple-touch-icon.png" />
  <link rel="icon" type="image/png" sizes="32x32" href="/favicon-32x32.png" />
  <link rel="icon" type="image/png" sizes="16x16" href="/favicon-16x16.png" />
  <link rel="manifest" href="/site.webmanifest" />
  <link rel="mask-icon" href="/safari-pinned-tab.svg" color="#5bbad5" />
  <meta name="msapplication-TileColor" content="#da532c" />
  <meta name="theme-color" content="#ffffff" />
  <!-- End Favicon: -->

  <script defer src="../js/script.js"></script>
  <link href="../css/style.css" rel="stylesheet" />
  <title>ben's things</title>
</head>
```

#### Escape Characters

Certain characters that have special meaning in HTML can not be used without escaping them. So if you wanted to actually write \<angle-brackets\> the browser would interpret that as an HMTL tag. The ampersand symbol followed by a specific code. The codes come in two styles, either an ampersand plus a "#" symbol followed by a number and a semicolon, or just an ampersand and a keyword and a semicolon. Either way the escape code always starts with an ampersand and ends with a semicolon.

A few examples:

| Character | Named Escape | Decimal Escape | Unicode Hex |
| --------- | ------------ | -------------- | ----------- |
| \<        | `&lt;`       | `&#60;`        | `&#003C;`   |
| &         | `&amp;`      | `&#38;`        | `&#0026;`   |
| "         | `&quot;`     | `&#34;`        | `&#0022;`   |
| &copy;    | `&copy;`     | `&#169;`       | `&#00A9;`   |
| &trade;   | `&trade;`    | `&#8482;`      | `&#2124;`   |
| &spades;  | `&spades;`   | `&#9824;`      | `&#2660;`   |
| &clubs;   | `&clubs;`    | `&#9827;`      | `&#2663;`   |
| &hearts;  | `&hearts;`   | `&#9829;`      | `&#2665;`   |
| &diams;   | `&diams;`    | `&#9830;`      | `&#2666;`   |

### HTML5 Layout

Structural improvements via new elements in HTML5 make it easier to give clear semantic meaning to a webpage. Instead of filling a page with a million `<div>` tags we can use specific elements to make code easier to read for humans and assistive devices. Some of the new structural tags:

- `<nav>`
  - For organizing navigational elements.
  - Typically for site navigation.
- `<section>`
  - An element used to define the main parts of the page. 
  - Often sections are filled with multiple `<articles>`.
- `<article>` 
  - A container for a type of content that could stand alone.
  - Used for content that could be syndicated or subscribed to.
- `<aside>`
  - When used inside an `<article>` element it defines additional related material.
  - When used outside of an `<article>` it is meant to hold content related to the entire page.
- `<header>` 
  - Not to be confused with the `<head>`
  - Used for information placed at the top of each page.
  - Can also be used for content that belongs at the top of an `<article>` or `<section>`
- `<footer>`
  - Used for information to placed at the bottom of the page or the bottom of another element.
  - Typically used for copyright information.
- `<figure>`
  - Used for any content that is referenced in an `<article>`.
  - Images, videos, graphs, diagrams, code samples, and text that supports the main body of the article.
  - Can also contain a `<figcaption>` that is used for a description of the `<figure>`.
- A re-contextualized `<div>`
  - The `<div>` has been replaced with many new elements but still remains an important element when wrapping other elements together, especially for styling purposes.
  - Should only be used when no other suitable element to be used for grouping is available.

Code excerpt from the book:

```html
<div class="wrapper">
  <header>
    <h1>Yoko's Kitchen</h1>
    <nav>
      <!-- nav content here -->
    </nav>
  </header>
  <section class="courses">
    <!-- section content here -->
  </section>
  <article>
    <!-- article content here -->
  </article>    
  <aside>
    <!-- aside content here -->
  </aside>
  <footer>
    <!-- footer content here -->
  </footer>
</div><!-- .wrapper -->
```

### Process & Design

#### Who is the site for?

Target audience:
- Individuals with specific personal demographics and categories.
- Companies with different sizes and budgets, and being represented by an individual.

#### Why people visit your website.

- Key motivations or the underlying reason for the visit.
- Specific goals can be triggers making them come to the site now.

#### What you visitors are trying to achieve

A good plan is writing down a list of reasons someone might want to visit the site. Take those reasons and assign them to fictional visitors. This process can help guide site design choices.

#### What information your visitors need

Look at the list of reasons for visiting the site and define what they need. Come up with supporting information that can also be offered. If the site does not appear to have the relevant information the visitor is likely to leave.

#### How often people will visit your site

Determining how often your site will have visitors will help inform how up to date the site needs to be and how many resources will be required to offer the content.

#### Structural Organization

##### Site maps

Sorting the information that needs to appear on the website will make it possible to structure the shape of how the pages fit together into one site. Using a card sorting technique you can separate individual pieces of information into cards making it easier to organize.

##### Wireframes

A wireframe is useful to get a sense of how the individual pages might look structurally speaking. The wireframe is not about specific colors or fonts but about larger elements and how they fill the page.

##### Organizational Design

Visual design is all about communicating something. By organizing and prioritizing we can communicate the importance of piece of content. Keeping visual styles consistent across certain content types can teach the visitor to associate a certain style with a specific type of information. 

##### Visual Hierarchy

Contrast is a valuable technique for separating different sections. Contrast can be achieved with size, color and style.

##### Grouping and Similarity

- Proximity
- Closure
- Continuance
- White Space
- Color
- Borders

Using headings and being consistent with chunks of information that fills these groupings will go a long way to making it readable.

#### Designing Navigation

Keep the navigation concise, and uncluttered, and limit what qualifies as a topic. Let the previous design exercises help confine where things fit together. Use context to let the visitor know where they are by highlighting the current navigational element. Make the navigation interactive and give feedback (i.e. changing colors etc.) and make sure the navigation doesn't change as the visitor moves through the site, stay consistent.

## JavaScript


### The ABC of Programming

#### Scripts

Scripts are list of instructions for the computer to follow. Each instruction is carried out in order precisely as directed. Depending on the flow of decisions not all of the script will always be used. Breaking down the script into small pieces and putting them in a flowchart can be a big help when trying to plan a script.

#### Objects

JavaScript uses an object-based model. The objects are a collection of properties. The properties are structured with name and a value in a pair. Each name/value pair describes something about the object.

`car.color =  blue;` or `hotel.pool = true;`

The name/value pairs can describe simple things like a color or a number but they can also describe another series of instructions i.e. a function. A function that is the property of an object is called a method. 

`car.changeSpeed()` or `hotel.checkAvailability()`

Web browsers themselves are represented as an object. The window object represents the whole browser window (or tab), and the document object is modelled after the page loaded into the window.

`document.write('Hello there.');`

Events can trigger a script to run. There are many events, things like loading, clicking and a key-press to name a few.

The browser sees the webpage through the HTML markup, creates a object model and stores that object in memory, then a rendering engine parses the css or uses default styling to display the page to the screen. 

#### How To

JavaScript is best written to a separate file and even kept in a separate directory. As projects grow there may be many JavaScript files.

Just like CSS files JavaScript written in separate document can be linked to the HTML page or it can be written directly into the page inside of the `<script>` tag.

Linking:
```html
<link rel="stylesheet" href="../css/style.css">
```
```html
<script src="../js/script.js"></script>
```

Inline:
```html
<p style="background-color: blue">Some Text</p>
```
```html
<script>
  console.log('Howdy');
</script>
```

