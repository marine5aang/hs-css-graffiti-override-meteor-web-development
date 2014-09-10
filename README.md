---
languages: html, css
tags: dev tools, developer tools, style, selectors, authority, cascade, overrides, graffiti, kids
type: lab
level: 2
---

# CSS Graffiti Override

In this challenge you are asked to clean the graffiti tags off the wall by making use of in browser developer tools and writing selectors that are more specific (have greater authority) in order to override the existing styles.

You will write your code in `cleanup.css`. You are absolutely not allowed to touch the contents of `paint.css`. 

Take a look at the example below for a hint. You'll want to work your way through each image to hide them. 

##Inheritence
If you take a look at `index.html`, you'll notice that `paint.css` is linked after `cleanup.css`, which means that `paint.css` loads last. In order to erase the graffiti from the wall, you cannot use the same CSS selectors in `cleanup.css` that were used in `paint.css`. In order to override the CSS in `paint.css`, you have to be more specific. 


##Example:
For example for tag-1 the developer tools reveal that the style applying the graffiti here from `paint.css` is:

```
.tag-1 {
  background: url(../images/tag-1.png) no-repeat;
  z-index: 7;
  display: block;
}
```

The CSS selector used is `.tag-1`. To make that image invisible, we want to use the property `display` and set the value to `none`. But what would happen if we used the same CSS selector to set `display: none;`? Unfortunately, because of the order in which the stylesheets are being loaded, the image would still be shown. This is why the specificity matters. In order to actually hide that image, we have to get more specific with our selectors. 

If we look, the div with the class `tag-1` is inside a div with the id `wall`...so to get more specific we could write something like this:

```
#wall .tag-1 {
  display: none;
}
```

## Resources

 * [Smashing Magazine - CSS Specificity](http://www.smashingmagazine.com/2007/07/27/css-specificity-things-you-should-know/)
 * [CSS Tricks - CSS Specificity](http://css-tricks.com/specifics-on-css-specificity/)
 * [Code School - DiscoverDevTools](http://discover-devtools.codeschool.com/)
