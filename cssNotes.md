# CSS notes

## what is it?

--CSS, or Cascading Style Sheets is a language used to style web pages. With CSS devs can control how the various html elements on their page are dispslayed.

__________________________________________________________________________________________________________________________________________________________________

### HOW TO APPLY CSS

CSS can be applied to a page inline, internally and externally. Inline CSS is what it sounds like, say you create a new `<p>` with som etext in it well inline CSS would style the element on the same line it was created ex:

```html
<p style="color:blue">Some random text</p>
```

next is internal CSS, this is set inside the `<head>` of a page, inside a `<style></style>` like so

```html
        <head>
            <meta charset="UTF-8">
            <meta http-equiv="X-UA-Compatible" content="IE=edge">
            <meta name="viewport" content="width=device-width, initial-scale=1.0">
                <title></title>

            <!-- example of internal css -->
            <style>
                h2{ color: cyan;}
                h3{color : green;}
            </style>
        </head>
```

Finally we can apply CSS via a stylesheet using the link tag. The link tag is used to establish a relationship between the current html page and an external source. The rel attribute is REQUIERED to use the link tag because rel (realtionship) specifies qhat kind of relationship is actually being established. There are many values rel can have but for css stylesheets simply use "stylesheet". After that the href tag is needed to indicate where the file is. The stylesheet.css doesnt have to be called stylesheet, could be anything

```html
        <link rel="stylesheet" href="stylesheet.css">
```

__________________________________________________________________________________________________________________________________________________________________

### USING ID'S AND CLASSES

Say you wanna group a bunch of elements together so they can have share the same color, in the html assign these elements classes and later call them with css. To call them simply do:
        .classname{}
For ID's its very similar, instead of using a ., instead us a # like so:
        #idOfElement{}
__________________________________________________________________________________________________________________________________________________________________

### USING ATTRIBUTE SELECTORS

using the syntax:

```html
    [attr=value]
```

you can style specific pieces of your page take for example this code:

```html
        [type='checkbox'] {
            margin-top:100px;
            margin-bottom:15px;
        }
        </style>
            <p>Things cats love:</p>
            <ul>
            <li>cat nip</li>
            <li>laser pointers</li>
            <li>lasagna</li>
            </ul>
            <p>Top 3 things cats hate:</p>
            <ol>
            <li>flea treatment</li>
            <li>thunder</li>
            <li>other cats</li>
            </ol>
        </div>
        <form action="https://freecatphotoapp.com/submit-cat-photo" id="cat-photo-form">
            <label><input type="radio" name="indoor-outdoor" checked> Indoor</label>
            <label><input type="radio" name="indoor-outdoor"> Outdoor</label><br>
            <label><input type="checkbox" name="personality" checked> Loving</label>
            <label><input type="checkbox" name="personality"> Lazy</label>
            <label><input type="checkbox" name="personality"> Energetic</label><br>
            <input type="text" placeholder="cat photo URL" required>
            <button type="submit">Submit</button>
        </form>
        </main>
```

on the first few lines we are basically saying,'for every input element with a type attribute of checkbox value, make the checkboxes have these properties'
__________________________________________________________________________________________________________________________________________________________________

### SPECIFICITY/HIERARCHY IN CSS

CSS follows a hierarchy:
    basically specificity will always have more weight, the more specific you are the higher the priority
    id>class
    inline>internal>external

Every selector has its place in the specificity hierarchy. There are four categories which define the specificity level of a selector:

>Inline styles: An inline style is attached directly to the element to be styled. Example: `<h1 style="color: #ffffff;">`
>>IDs: An ID is a unique identifier for the page elements, such as #navbar.
>>>Classes, attributes and pseudo-classes: This category includes .classes, [attributes] and pseudo-classes such as :hover, :focus etc.
>>>>Elements and pseudo-elements: This category includes element names and pseudo-elements, such as h1, div, :before and :after.

Specificity starts at 0, inline styles are worth 1000, id's are worth 100, classes and attributes are worth 10 and element names are worth 1

```html
A: h1
B: #content h1
C: <div id="content"><h1 style="color: #ffffff">Heading</h1></div>
```

so above it would go like C>B>A

if something has equal specificity the last one will be visible
__________________________________________________________________________________________________________________________________________________________________

### ABSOLUTE AND RELATIVE UNITS

__________________________________________________________________________________________________________________________________________________________________

### ON FONTS, TAKEN FROM FREECODECAMP

the font family property is used to change the font of elements

```css
        h2 {
            font-family: sans-serif;
        }
```

you can also import a font from a free google library and from possibly some other sources. Google website will auto generate the html code to link it with your page. below is the google library page, below that is an example snippet that would get generated:
[https://fonts.google.com/]

```html
        <link href="https://fonts.googleapis.com/css?family=Lobster" rel="stylesheet" type="text/css">
```

After putting this in the head, you can call the font in your css. Font names are case sensitve and cant interpret spaces, so if the font family name has spaces in it you need to use " ". you can assign multiple font families incase one fails to load:

```css
        font-family:"font name", Generic font;
```

the generic fonts dont need "" and is not case sensitve cause its a css keyword. Again it will only be displayed if the first font fails.
__________________________________________________________________________________________________________________________________________________________________

### ON SIZING ELEMENTS TAKEN FROM FREECODECAMP

Using css's width property you can change the size of things
__________________________________________________________________________________________________________________________________________________________________

### ADDING BORDERS AROUND YOUR ELEMENTS

properties to use:
   border-color: color1 color2 color3 color4
            -1 color  = entire border will be 1 color
            -2 colors = top,bottom sides will be color1 and right,left will be color2
            -3 colors = top color 1, sides color 2, bottom color 3
            -4 colors = top color1, right color2, bottom color3, left color4
this is called clockwise notation

   border-style
            -anything you do will not be displayed unless this property is set
   border-width
   border-radius
            -rounds out your image edges. You can make an img be a circle. Values can be px. To make perfect circle use 50%

__________________________________________________________________________________________________________________________________________________________________

### COLORS

color:
    changes only the color of the text
background-color
    -changes literally the background color of something
__________________________________________________________________________________________________________________________________________________________________

### PADDING AND MARGINS

all html elements are displayed as rectangles of varying sizes. There are 3 properties the control the space around each element:
    **border**
    **padding**
        controls the amount of space between element's content and border
        There are also other padding options which control the amount of padding on a specific side:
        - padding-top
        - padding-bottom
        - padding-left
        - padding-right
    **margin**
        controls the amount of space between an element's border and other elements. Increasing this causes your elements to move farther apart while setting a negative value causes them to scoot together. Same goes for margins, you can hae diff margin values for diff sides:
        - margin-top
        - margin-bottom
        - margin-left
        - margin-right

instead of going one by one for each property you can use something called clockwise notation, which acts like when we played with border-color prop.This works for margin too, So doing

```css
padding: 10px 20px 30px 70px;
```

is same as

```css
padding-top:10px;
padding-bottom:20px;
padding-left:30px;
padding-right:70px;
```
