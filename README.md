#Vintage Software HTML CSS & Sass Style Guide

Code in any code-base should look like a single person typed it, no matter how many people contributed.

> “Programs are meant to be read by humans and only incidentally for computers to execute.”
> — H. Abelson and G. Sussman (in “Structure and Interpretation of Computer Programs”)

A big thanks to the following projects:
- [codeguide.co](http://codeguide.co/)
- [styleguides.io](http://styleguides.io/)
- [Github Code Guide](https://github.com/styleguide)

##Categories
1. [HTML](#html)
1. [CSS/Sass](#csssass)

## HTML
Strive to maintain HTML standards and semantics, but not at the expense of practicality. Use the least amount of markup with the fewest intricacies whenever possible.

###Formatting

- Use tabs (4 spaces)
- DOM nodes should have no spaces
- Leverage HTML5 elements to have more semantic code elements `<header>, <footer>, <main>, <nav>, <aside>, <section>`

###Doctype

- Ensure proper rendering on all browsers follow the HTML5 doctype spec
- Make sure the language is specified for the document at all times

  ``` html
  <!DOCTYPE html lang="en-us">
  ```

###Encoding

- Have proper encoding type set

  ``` html
  <head>
    <meta charset="UTF-8">
  </head>
  ```

###Attribute order

HTML attributes should come in this particular order for easier reading of code.

- `class`
- `id`, `name`
- `data-*` or Angular attributes
- `src`, `for`, `type`, `href`
- `title`, `alt`
- `aria-*`, `role`

``` html
<a class="..." id="..." data-modal="toggle" href="#">
  Example link
</a>
```

Regular custom data attributes should follow the html5 spec and be prefixed with `data-`. Example:`data-stuff="Hello"`

###Reducing markup

Whenever possible, avoid superfluous parent elements when writing HTML. Many times this requires iteration and refactoring, but produces less HTML. Take the following example:

  ``` html
  <!-- Not so great -->
  <span class="avatar">
    <img src="...">
  </span>
  
  <!-- Better -->
  <img class="avatar" src="...">
  ```
  
### URLs 
- URLs should all be lowercase and permanent redirect any uppercase version to the lowercase route. Otherwise search engines will treat case differences as duplicate content. 
- URLs words should be separated by dashes. Search engines determine words by this convention.


## CSS/Sass

- Use [Sass](http://sass-lang.com/) for the preprocessing of css.
- Use the CSS naming convention `.words-with-dashes`.
- Never reference js- prefixed class names from CSS files. js- are used exclusively from JS files.
- Do not put IE specific hacks in the CSS. Use a separate IE specific stylesheet.
- Page specific CSS should be minimal and code should follow OOCSS patterns.
- Do not use inline styles
  
  ``` html
  <!-- Bad -->
  <div style="background: #000; color: #fff;"></div>

  <!-- Good -->
  <div class="my-module"></div>
  ```
  
###Conventions

- Files should follow block formatting as it is the Sass convention.
- Do not use `ID`'s in selectors as they add specificity issues.
- Keep classes as short and succinct as possible.
- Use meaningful names; use structural or purposeful names over presentational.
- Use shorthand hex values where available, e.g., `#fff` instead of `#ffffff`.
- Avoid specifying units for zero values, e.g., `margin: 0;` instead of `margin: 0px;`.
- Quote attribute values in selectors, e.g., `input[type="text"]`. 
  [They're only optional in some cases](http://mathiasbynens.be/notes/unquoted-attribute-values#css), and it's a good practice for consistency.

###Box-sizing
We reset `box-sizing` to `border-box` for every element. This allows us to more easily assign widths to elements that also have `padding` and `borders`.


###BEM Syntax
Follow the [Custom BEM](http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/) Syntax where appropriate to keep html/css module reusable.

[http://blog.8thlight.com/nelsol-batalla/2014/08/01/bem-basics.html](http://blog.8thlight.com/nelsol-batalla/2014/08/01/bem-basics.html)

[http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/](http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/)

- `.block` highest level of abstraction or component.
- `.block__element` descendant of `.block` element that helps <code>.block</code>.
- `.block--modifier` different state or version of `.block`.

  ``` css
  /* Generated CSS BEM */
  .block {
  }
  
  .block__element {
  }
  
  .block--modifier {
  }
  
  /* Sass BEM */
  .block {
    &__element {
    
    }
    
    &--modifier {
    
    }
  }
```

###Nesting Sass

- Nest no more than three elements deep.
- Avoid unnecessary nesting. Just because you can nest, doesn't mean you always should. Consider nesting only if you must scope styles to a parent and if there are multiple elements to be nested.

  ``` css
  /* Bad Nesting */
  .message {
    display: block;
    
    li {
      margin: 4px;
      
      p {
        margin: 0; 
        
        span {
          color: red;    
        } 
      }     
    }    
  }
  
  /* Better nesting less than 3 */
  .message {
    display: block;
    
    li {
        margin: 4px;     
    }
    
    p {
        margin: 0;
    }
  }
  ```
