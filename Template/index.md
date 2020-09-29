## HTML/PUG

##### HTML

HTML is a markup language that allows developers to create pages and web applications.
It's not a programming language so it doesn't allows to have dynamic functionalities.

#### PUG
PUG is a template engine for node and the browser. Its compiled into HTML and has a simplified syntax.
It allows to write reusable code and having dynamic data. It has functionalities like loop, conditions, and so on.

#### HTML vs PUG

```html
<div>
  <h1>Example of HTML code</h1>
  <p>Hello There!</p>
</div>
```

```pug
div
	h1 Example of HTML code
	p Hello There!
```

#### HTML or PUG?
If the project is not based on a FE framework, the best solution is to use PUG due to its pletora of functionalities.

Otherwise, if you are already using some FE framework, most of PUG advantages are covered by it, the only addition will be the indentation style making the code more readable. On the other hand, it requires more configurations.

#### Best Practices
* **Avoid inline style** 

Bad
```html
    <p style="color:#abc; font-size:14px; font-family:arial,sans-serif;"></p>
```

Good
```html
    <p class='paragraph'></p>
```

* **Use the right tag** HTML has a lot of tags available, so stop using always divs and span and find the right element;
* **Comments...when needed** HTML code could be har to read and understand, so sometimes people starts inserting comments inside it. Don't overuse comments! It will make everything even more messy. Instead use comments to mark where the elements are closing.

Good
```html
<div class='wrapper'>
    <div class='row'>
    </div> <!-- End of row -->
</div> <!-- End of wrapper --> 
```
* **Dont' use BR** stop using BR tag, instead use CSS attributes;
* **Put every element on its one line** 
Bad:
```html
    <table><tr><th>Hello World!</th></tr></table>
```
Good:
```html
    <table>
        <tr>
            <th>Hello World!</th>
        </tr>
    </table>
```

* **Boolean attribute** if an attribute is a boolean, don't put a value, just use it. The HTML considers the usage as true value and, if not used, as false;