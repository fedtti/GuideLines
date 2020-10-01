# CSS/SCSS

We’ll start with a short intro about CSS and SCSS.

**CSS** is a language used to add styles to web pages. It’s one of the core “values” of web development, along with JavaScript and HTML.

**SCSS** is [a pre-processed language](https://sass-lang.com/) that will be compiled into a CSS file. It allows to add special functionalities to a simple CSS file, such as variables and class nesting.



## Advantages of SCSS

* the code is more readable, also thanks to its nesting capabilities (the lines of code will be reduced);
* inline comments help developers understanding the code;
* usage of variables and functions.



## Folder structure

Here’s some examples and suggestions on how to make a good folder structure when it comes to styles.

The main fodler will be called *__styles__* and contains all subfolders and files.
One of the core concepts is to avoid having styles inside a single file, but to split it into multiple files, one for each component created.

The folder structure is based on the *__7-1__* rule: 7 folders, 1 file.
The only file contained in the *__styles__* folder is *__main.scss__* and its only purpose is to import all the styles files created.

The 7 subfodlers are the follwing:
* **utilities** contains all the SCSS files used to help the developers—like variables, functions, mixins;
* **base** contains the SCSS code that will be used in the whole application—like rest files, common and generic CSS classes (e.g. margin classes, font-size classes and so on);
* **components** contains all the component related styles. When it comes to large scale application, this folder could be splitted into subfodlers containing, for example, base components, or domain related components;
* **layout** contains all the styles related to layout components. With the increasingly usage of frontend frameworks, this folder could be omitted;
* **pages** styles related to the applications pages;
* **themes** not very used, this folder contains all the styles that modify the application with some specific theme;
* **vendors** all codes belonging to third part libraries should be store inside this folder. If, for some reason, we need to overwrite the style of some components, create a subfolder with the name *__vendors-extensions__* and save the styles inside it;

All the styles file names that are not `main.scss` should start with an `_` symbol.

Here’s an example of a folder structure:

styles/
|
|– utilities/
|   |– _variables.scss
|   |– _functions.scss
|   |– _mixins.scss 
|
|– base/
|   |– _reset.scss
|   |– _typography.scss
|
|– components/
|   |– _button.scss 
|   |– _carousel.scss
|   |– _slider.scss 
|
|– layout/
|   |– _grid.scss
|   |– _header.scss
|   |– _footer.scss
|   |– _sidebar.scss
|   |– _form.scss
|
|– pages/
|   |– _home.scss
|   |– _about.scss
|   |– _contact.scss
|
|– themes/
|   |– _theme.scss
|
|– vendors/
|   |– _bootstrap.scss
|   |– _jquery-ui.scss
|
|– main.scss


N.B.: The 7-1 rule can be applied as needed, for example don’t create a themes folder if not necessary.

We can make a little change on this structure by adding, for every folder, an entry point file which will import all the files of that folder.
For example, the layout folder, could contain **a `__layout.scss` which will import all the other SCSS files contained in the `layout/` folder**.
This newly created file will be then, the one imported in `main.scss`.



### Best practices

* **Put every attribute on a single line** 
Bad:
```css
.class { display: none; position: relative; }
```

Good:
```css
.class {
	display: none;
	position: relative;
}
```
* **Use reset files** when starting a project from scratch, its a good practice to have reset files to remove all the browser useless styles:
* **Merge common style** if some classes uses the same styles, merge them;

Bad
```css
.class_1 {
	color: black;
}

.class_2 {
	color: black;
}
```

Good:
```css
.class_1, .class_2 {
	color: black;
}
```
* **First HTML, then CSS** start by writing down the HTML and then add style to it;
* **Utility classes** create and use utility classes if some style are widely used in the application, make the code as much reusable as possible;
**Warning** don't overuse utility classes. Use them with wisdom.
For example, if an element has a left float and we are using '.float-left' class maybe later we'll need to float it to the right. To do so we need to change the HTML of the element and update its css classes to be 'float-right'. That's wrong because we are changing HTML to update the style.
Remember:
*__HTML is for markup, CSS for style__*

* **Use shorthand** 
Bad:
```css
.class {
	margin-top: 2px;
	margin-right: 10px;
	margin-bottom: 15px;
	margin-left: 20px
}
```

Good:
```css
.class {
	margin: 2px 10px 15px 20px;
}
```
* **Keep alphabetical order** 
Bad
```css
.class {
	margin: 10px;
	display: flex;
	border: 1px solid red;
}
```

Good:
```css
.class {
	border: 1px solid red;
	display: flex;
	margin: 10px;
}
```

* **Use rem, em instead of px**
* **Use the most specific attribute**
Bad
```css
.class {
    background: red;
}
```

Good
```css
.class {
    background-color: red;
}
```

### BEM
It's a metodology to give css classes descriptive names. Forces the developer to make component as little and reusable as possible.

BEM (Block - Element - Modifiers) is based on the concept of split the elements of the page into blocks.

Here an example of a card component:
The main element will have a *__.card__** css class.
The card contains an image, a description and two actions buttons.
The inner elements will then, have the following css classes:
* *__.card\_\_image__*;
* *__.card\_\_description__*;
* *__.card\_\_button__*

The buttons, moreover, will be divided into confirm and cancel button, so their css classe are: *__.card\_\_button--is-success__*, *__.card\_\_button--is-cancel__*

As you can see, the card components has been split into, BLOCK (card), elements (image, description, button) and modifiers (--is-success, --is-cancel).

**WARNING**
Watch out when creating css names, sometimes you will end up having very long names. Remember, BEM is not strictly related to the DOM so try keeping the names with at most a single '__' pattern in it.

The following example shows, how to use BEM without relating it to the DOM structure:
Bad
```html
<div class="card">
    <div class="card__header">
        
        <h2 class="card__header__title">Title text here</h2>
    
    </div>
    <div class="card__body">
        
        <img class="card__body__img" src="some-img.png">
        
        <p class="card__body__text">Lorem ipsum dolor sit amet, consectetur</p>
        <p class="card__body__text">Adipiscing elit.
            <a href="/somelink.html" class="card__body__text__link">Pellentesque amet</a>
        </p>

    </div>
</div>
```

Good
```html
<div class="card">
    <div class="card__header">
        
        <h2 class="card__title">Title text here</h2>
    
    </div>
    <div class="card__body">
        
        <img class="card__img" src="some-img.png">
        
        <p class="card__text">Lorem ipsum dolor sit amet, consectetur</p>
        <p class="card__text">Adipiscing elit.
            <a href="/somelink.html" class="card__link">Pellentesque amet</a>
        </p>

    </div>
</div>
```
