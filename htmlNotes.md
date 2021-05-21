# HTML notes

[ref for html](https://developer.mozilla.org/en-US/docs/Web/HTML)
[finish this](https://www.tutorialrepublic.com/html-tutorial/)

## what is it?

--HTML, meaning Hyper Text Marker Language is used to structure/present elements in a webpage.

---

\*typical structure of an html file:
html tags are not case sensitive but should be written in lowercase as thats the standard

```html
        <!DOCTYPE html>
        <html>
            <head>
                <meta ....
                <title>Title of the document</title>
            </head>
            <body>
            The content of the document......
            </body>

        </html>
```

`<!DOCTYPE html>` is NOT A TAG, its used by browsers to properly introduce a html doc. It helps your browser process the information in the document into an actual page

`<html>` is a container for the rest of the elements within the page

`<head>` is a container which stores meta information about the page, metadata is information about your information.

`<title>` name of the page which is displayed on the top of a browser

`<body>` a container for the content of your page

html 5 introduced a bunch of new elements to help designers organize the contents of their page better

---

## NOTES FROM CODECAMP

---

### IMAGES

To add images:

```html
<img src="https://www.your-image-source.com/your-image.jpg" />
```

Note that img elements are self-closing. All img elements must have an alt attribute. The text inside an alt attribute is used for screen readers to improve accessibility and is displayed if the image fails to load. Note: If the image is purely decorative, using an empty alt attribute is a best practice. Ideally the alt attribute should not contain special characters unless needed. Let's add an alt attribute to our img example above:

```html
<img
  src="https://www.your-image-source.com/your-image.jpg"
  alt="Author standing on a beach with two thumbs up."
/>
```

---

### ANCHOR FOR EXTERNAL LINKS

You can use anchor elements to link to content outside of your web page. anchor elements need a destination web address called an href attribute. They also need anchor text. Here's an example:

```html
<a href="https://freecodecamp.org">this links to freecodecamp.org</a>
```

Then your browser will display the text "this links to freecodecamp.org" as a link you can click. And that link will take you to the web address [codecamp](https://www.freecodecamp.org).

#### USING ANCHOR FOR INPAGE OPERATIONS

Anchor elements can also be used to create internal links to jump to different sections within a webpage.
To create an internal link, you assign a link's href attribute to a hash symbol # plus the value of the id attribute for the element that you want to internally link to, usually further down the page.
You then need to add the same id attribute to the element you are linking to.
An id is an attribute that uniquely describes an element.
Below is an example of an internal anchor link and its target element:

```html
<a href="#contacts-header">Contacts</a>
...
<h2 id="contacts-header">Contacts</h2>
```

When users click the Contacts link, they'll be taken to the section of the webpage with the Contacts header element.

### NESTED LINK WITHIN A `<P>`

You can nest links within other text elements.

```html
<p>
  Here's a
  <a target="_blank" href="http://freecodecamp.org">
    link to freecodecamp.org</a
  >
  for you to follow.
</p>
```

Let's break down the example:

Normal text is wrapped in the p element:
`<p> Here's a ... for you to follow. </p>`

Next is the anchor element `<a>` (which requires a closing tag `</a>`):
`<a> ... </a>`

target is an anchor tag attribute that specifies where to open the link and the value "\_blank" specifies to open the link in a new tab

href is an anchor tag attribute that contains the URL address of the link:
`<a href="http://freecodecamp.org"> ... </a>`

The text, "link to freecodecamp.org", within the anchor element called anchor text, will display a link to click:
`<a href=" ... ">link to freecodecamp.org</a>`

The final output of the example will look like this:
Here's a link to freecodecamp.org for you to follow.

### BLANK LINK FOR FUTURE USE

Sometimes you want to add a elements to your website before you know where they will link.
This is also handy when you're changing the behavior of a link using JavaScript, which we'll learn about later.
The current value of the href attribute is a link that points to "http://freecatphotoapp.com".
Replace the href attribute value with a #, also known as a hash symbol, to create a dead link.
For example:

```html
href="#"
```

### IMAGE AS LINK

You can make elements into links by nesting them within an a element.
Nest your image within an a element. Here's an example:

```html
<a href="#"
  ><img
    src="https://bit.ly/fcc-running-cats"
    alt="Three kittens running towards the camera."
/></a>
```

Remember to use `#` as your a element's href property in order to turn it into a dead link.

---

## UNORDERED BULLET POINT STYLE LIST

HTML has a special element for creating unordered lists, or bullet point style lists.

Unordered lists start with an opening `<ul>` element, followed by any number of `<li>` elements. Finally, unordered lists close with a `</ul>`

For example:

```html
<ul>
  <li>milk</li>
  <li>cheese</li>
</ul>
```

would create a bullet point style list of "milk" and "cheese".

## ORDERED LISTS

HTML has another special element for creating ordered lists, or numbered lists.

Ordered lists start with an opening `<ol>` element, followed by any number of `<li>` elements. Finally, ordered lists close with a `</ol>`

For example:

```html
<ol>
  <li>Garfield</li>
  <li>Sylvester</li>
</ol>
```

would create a numbered list of "Garfield" and "Sylvester".

---

### INPUT TEXT

To add an input text box do:

```html
<input type="text" />
```

Placeholder text is what is displayed in your input element before your user has inputted anything.
You can create placeholder text like so:

```html
<input type="text" placeholder="this is placeholder text" />
```

---

### PLACEHOLDER TEXT TO TEXTFIELD

Add Placeholder Text to a Text Field
Placeholder text is what is displayed in your input element before your user has inputted anything.

You can create placeholder text like so:

```html
<input type="text" placeholder="this is placeholder text" />
```

Note: Remember that input elements are self-closing.

---

### CREATING FORM ELEMENT

You can build web forms that actually submit data to a server using nothing more than pure HTML. You can do this by specifying an action on your form element.

For example:

```html
<form action="/url-where-you-want-to-submit-form-data"></form>
```

---

### BUTTON

Let's add a submit button to your form. Clicking this button will send the data from your form to the URL you specified with your form's action attribute.

Here's an example submit button:

```html
<button type="submit">this button submits the form</button>
```

---

### USE HTML5 TO REQUIRE A FIELD

You can require specific form fields so that your user will not be able to submit your form until he or she has filled them out.

For example, if you wanted to make a text input field required, you can just add the attribute required within your input element,
like this:

```html
<input type="text" required />
```

---

### CREATE A SET OF RADIO BUTTONS

You can use radio buttons for questions where you want the user to only give you one answer out of multiple options.

Radio buttons are a type of input.

Each of your radio buttons can be nested within its own label element. By wrapping an input element inside of a label element it will automatically associate the radio button input with the label element surrounding it.

All related radio buttons should have the same name attribute to create a radio button group. By creating a radio group, selecting any single radio button will automatically deselect the other buttons within the same group ensuring only one answer is provided by the user.

Here's an example of a radio button:

```html
<label> <input type="radio" name="indoor-outdoor" />Indoor </label>
It is considered best practice to set a for attribute on the label element, with
a value that matches the value of the id attribute of the input element. This
allows assistive technologies to create a linked relationship between the label
and the child input element. For example:

<label for="indoor">
  <input id="indoor" type="radio" name="indoor-outdoor" />Indoor
</label>
```

---

### CHECKBOX

Forms commonly use checkboxes for questions that may have more than one answer.

Checkboxes are a type of input.

Each of your checkboxes can be nested within its own label element. By wrapping an input element inside of a label element it will automatically associate the checkbox input with the label element surrounding it.

All related checkbox inputs should have the same name attribute.

It is considered best practice to explicitly define the relationship between a checkbox input and its corresponding label by setting the for attribute on the label element to match the id attribute of the associated input element.

Here's an example of a checkbox:

```html
<label for="loving"
  ><input id="loving" type="checkbox" name="personality" /> Loving</label
>
```

---

### Use the value attribute with Radio Buttons and Checkboxes

When a form gets submitted, the data is sent to the server and includes entries for the options selected. Inputs of type radio and checkbox report their values from the value attribute.

For example:

```html
<label for="indoor">
  <input id="indoor" value="indoor" type="radio" name="indoor-outdoor" />Indoor
</label>
<label for="outdoor">
  <input
    id="outdoor"
    value="outdoor"
    type="radio"
    name="indoor-outdoor"
  />Outdoor
</label>
```

Here, you have two radio inputs. When the user submits the form with the indoor option selected, the form data will include the line: indoor-outdoor=indoor. This is from the name and value attributes of the "indoor" input.

If you omit the value attribute, the submitted form data uses the default value, which is on. In this scenario, if the user clicked the "indoor" option and submitted the form, the resulting form data would be indoor-outdoor=on, which is not useful. So the value attribute needs to be set to something to identify the option.

---

### Check Radio Buttons and Checkboxes by Default

You can set a checkbox or radio button to be checked by default using the checked attribute.

To do this, just add the word "checked" to the inside of an input element. For example:

```html
<input type="radio" name="test-name" checked />
```

---

### Nest Many Elements within a Single div Element

The div element, also known as a division element, is a general purpose container for other elements.

The div element is probably the most commonly used HTML element of all.

Just like any other non-self-closing element, you can open a div element with `<div>` and close it on another line with `</div>`.

---

### Declare the Doctype of an HTML Document

The challenges so far have covered specific HTML elements and their uses. However, there are a few elements that give overall structure to your page, and should be included in every HTML document.

At the top of your document, you need to tell the browser which version of HTML your page is using. HTML is an evolving language, and is updated regularly. Most major browsers support the latest specification, which is HTML5. However, older web pages may use previous versions of the language.

You tell the browser this information by adding the `<!DOCTYPE ...>` tag on the first line, where the ... part is the version of HTML. For HTML5, you use `<!DOCTYPE html>`.

The ! and uppercase DOCTYPE is important, especially for older browsers. The html is not case sensitive.

Next, the rest of your HTML code needs to be wrapped in html tags. The opening `<html>` goes directly below the `<!DOCTYPE html>` line, and the closing `</html>` goes at the end of the page.

Here's an example of the page structure:

```html
<!DOCTYPE html>
<html>
  <!-- Your HTML code goes here -->
</html>
```

---

### Define the Head and Body of an HTML Document

You can add another level of organization in your HTML document within the html tags with the head and body elements. Any markup with information about your page would go into the head tag. Then any markup with the content of the page (what displays for a user) would go into the body tag.

Metadata elements, such as link, meta, title, and style, typically go inside the head element.

Here's an example of a page's layout:

```html
<!DOCTYPE html>
<html>
  <head>
    <!-- metadata elements -->
  </head>
  <body>
    <!-- page contents -->
  </body>
</html>
```

---
