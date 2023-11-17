# Homework 01 - HTML, CSS, and Git: Code Refactor

Deployment Link - <https://turtlenav.github.io/seo-company-refactor/>

My contributions refactoring this code base include:
# Table of Contents
1. [HTML Modifications](#html-modifications)
    1. [Added a "viewport" meta tag](#added-a-"viewport"-meta-tag)
    2. [Added a Descriptive Title](#added-a-descriptive-title)
    3. [Fixed Broken Link in Body](#fixed-broken-link-in-body)
    4. [Add Alt Attribute to Images](#add-alt-attribute-to-images)
        1. [Special Case](#special-case)
2. [CSS Modifications](#css-modifications)
    1. [Redundant CSS Code 1](#redundant-css-code-1)

## HTML Modifications
The HTML found in this codebase is good for the most part. Somesimple changes were made for SEO and acessibility, however.

### Added a "viewport" meta tag
The below code was added to our `index.html`'s head element:
```html
<meta name="viewport" content="width=device-width, initial-scale=1" />
```
This code improves the appearance of our webpage on narrow-screened devices such as mobile phones.

### Added a Descriptive Title
Changed the <title> tag to be more descriptive. For SEO purposes, a <title> should contain our website's keywords. I changed the previous value of "website" "Horiseon Social Solution Services".

### Fixed Broken Link in Body
The link with the cursor hovering over was broken upon recieving this codebase:
![Broken Link](broken-link-example.png)

Within `index.html`, a `<a>` tag was linking an internal id that didn't exist. The `<div>` that it was supposed to be targeting had its id attribute set as follows:
```html <div id="online-reputation-management">```

### Add Alt Attribute to Images
For user accessibility and SEO it is incredibly important to provide alt attributes to images. Each image was given alt text that was as short as possible to describe the image it was replacing.

#### Special Case
There is a CSS background image on our webpage and is applied to `<div class="hero"></div>`. Since div's don't have an alt attribute, if we want the image to achieve our accessibility requirements, we can instead assign alt text to the div's title attribute: `<div class="hero" title="Employees gathered around a table"></div>` 

## CSS Modifications
This website came with a `style.css` file contained within the root `assets/` directory. This file contained a multitude of redundant features and I was able to significantly trim the codebase. Minor edits include descriptive comments of complicated rules and rearranging rules to follow the folow of elements found in `index.html`

### Redundant CSS Code
The below code was not the only source of redundancy in our codebase but for the sake of brevity it is the only example provided. Upon examining our `index.html` file we will find a code block like the following:
```html
<div class="content">
    <div id="search-engine-optimization" class="search-engine-optimization">
        <img src="./assets/images/search-engine-optimization.jpg" class="float-left" />
        <h2>Search Engine Optimization</h2>
        <p>...</p>
        </div>
    <div id="online-reputation-management" class="online-reputation-management">
        <img src="./assets/images/online-reputation-management.jpg" class="float-right" />
        <h2>Online Reputation Management</h2>
        <p>...</p>
    </div>
    <div id="social-media-marketing" class="social-media-marketing">
        <img src="./assets/images/social-media-marketing.jpg" class="float-left" />
        <h2>Social Media Marketing</h2>
        <p>...</p>
    </div>
</div>
```
The above code block is targeted by a highly redundant set of CSS rules. These rules are
the same for each `<div>` yet are applied individually, resulting in 3x the code we need.
The below CSS code shows the rules applied just to the `<div id="search-engine-optimization">`
element but there is equivalent code for both `<div id="online-reputation-management">` and
`<div id="social-media-marketing">` as well.
```css
.search-engine-optimization {
    margin-bottom: 20px;
    padding: 50px;
    height: 300px;
    font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
    background-color: #0072bb;
    color: #ffffff;
}
.search-engine-optimization img {
    max-height: 200px;
}
.search-engine-optimization h2 {
    margin-bottom: 20px;
    font-size: 36px;
}
```
We can simply fix this by targeting the parent `<div class="content">` element with the
above rules instead. It is worth mentioning that the above html code block assigns a
pointless class attribute to each `<div>` and we can improve our html code by deleting
all three of them. If we did wish to target different rules to each `<div>` then our
css file should target their id attribute instead.


