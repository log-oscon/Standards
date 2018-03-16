# Accessibility

These tips are good practice to help you meet Web Content Accessibility Guidelines (WCAG) requirements.

## Table of Contents

* [Label with every form control](#label-form)
* [Include alternative text for images](#alt-text)
* [Identify page language and language changes](#page-lang)
* [Use mark-up to convey meaning and structure](#markup)
* [Help users avoid and correct mistakes](#help-users)
* [Reflect the reading order in the code order](#reading-order)
* [Write code that adapts to the user's technology](#user-technology)
* [Avoid CAPTCHA where possible](#captcha)
* [Resources](#resources)

## Label with every form control

Use a for attribute on the &lt;label&gt; element linked to the id attribute of the form element, or using WAI-ARIA attributes. In specific situations it may be acceptable to hide &lt;label&gt; elements visually, but in most cases labels are needed to help all readers understand the required input.

```html
<label for="username">Username</label>
<input id="username" type="text" name="username">
```

```html_example
<label for="username">Username</label>
<input id="username" type="text" name="username">
```

## Include alternative text for images

Ensure that alternative text for images is added to all informational and functional images. Use empty alternative text, alt="" for decorative images, or include them in the CSS instead. Text alternatives are usually provided by those responsible for written content.

```html
<img src="path_to_image" alt="Meaningful Description">
```

## Identify page language and language changes

Indicate the primary language of every page by using the lang attribute in the html tag, for example &lt;html lang="en"&gt;. Use the lang attribute on specific elements when the language of the element differs from the rest of the page.

## Use mark-up to convey meaning and structure

Use appropriate mark-up for headings, lists, tables, etc. HTML5 provides additional elements, such as &lt;nav&gt; and &lt;aside&gt;, to better structure your content. WAI-ARIA roles can provide additional meaning, for example, using role="search" to identify search functionality. Work with designers and content writers to agree on meanings and then use them consistently.

```html
<section>
  <article>
    <h2>Superbear saves the day</h2>
    <time datetime="2015-08-07">7 Aug 2015</time>
    <p>The city's favorite bear yet again proves his mettle by rescuing a young cat from a tree. Witnesses say that Superbear's efforts were not appreciated by the feline, who inflicted some minor scratch wounds on his rescuer.</p>
    <aside>
      <h3>Related Articles</h3>
      <ul>
        <li><a href="#">Bear receives key to city</a></li>
        <li><a href="#">Superbear stands for mayor</a></li>
      </ul>
    </aside>
  </article>
</section>
```

```html
<form action="#" method="post">
  <div role="search">
    <label for="search">Search for</label>
    <input type="search" id="search" aria-describedby="search-help">
    <div id="search-help">Search records by customer id or name</div>
    <button type="submit">Go</button>
  </div>
</form>
```

## Help users avoid and correct mistakes

Provide clear instructions, error messages, and notifications to help users complete forms on your site. When an error occurs:
* Help users find where the problem is
* Provide specific, understandable explanations
* Suggest corrections

Be as forgiving of format as possible when processing user input. For example, accept phone numbers that include spaces and delete the spaces as needed.

## Reflect the reading order in the code order

Ensure that the order of elements in the code matches the logical order of the information presented. One way to check this is to remove CSS styling and review that the order of the content makes sense.

```html_example
<h3>Space trainers</h3>
<img src="images/trainer.png" alt="...">
<p>Space...</p>
<a href="...">Add to cart</a>
```

```html
// Bad
<img src="images/trainer.png" alt="...">
<h3>Space trainers</h3>
<p>Space...</p>
<a href="...">Add to cart</a>

// Good
<h3>Space trainers</h3>
<img src="images/trainer.png" alt="...">
<p>Space...</p>
<a href="...">Add to cart</a>
```

## Write code that adapts to the user's technology

Use responsive design to adapt the display to different zoom states and viewport sizes, such as on mobile devices and tablets. When font size is increased by at least 200%, avoid horizontal scrolling and prevent any clipping of content. Use progressive enhancement to help ensure that core functionality and content is available regardless of technology being used.

```html
/* On narrow viewports, make the navigation full width */
@media screen and (min-width: 25em) {
  #nav {
    float: none;
    width: auto;
  }
  #main {
    margin-left: 0;
  }
}

/* On wider viewports, put the navigation on the left */
@media screen and (min-width: 43em) {
  #nav {
    float: left;
    width: 24%;
  }
  #main {
    margin-left: 27%;
  }
}
```

## Avoid CAPTCHA where possible

CAPTCHAs create problems for many people. There are other means of verifying that user input was generated by a human that are easier to use, such as automatic detection or interface interactions. If CAPTCHA really needs to be included, ensure that it is simple to understand and includes alternatives for users with disabilities, such as:

* Providing more than two ways to solve the CAPTCHAs
* Providing access to a human representative who can bypass CAPTCHA
* Not requiring CAPTCHAs for authorized users.

## Resources

* [Tips on Developing for Web Accessibility](https://www.w3.org/WAI/gettingstarted/tips/developing.html)
