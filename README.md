Purpose
=======

This example demonstrates a particular way of using [SASS](http://sass-lang.com)'s
 [extends directive](http://sass-lang.com/documentation/file.SASS_REFERENCE.html#extend) and [placeholder
selectors](http://sass-lang.com/documentation/file.SASS_REFERENCE.html#placeholders) to define and modularize
 components styles.

[Here's a sassmeister illustration](http://sassmeister.com/gist/f5ed65b3116c6cfcdc33)

Typically one styles the placeholder selector and uses the extends directive in their normal styles.
  Out of the normal styles, we raise the usage of the extends directives protected as special, sanctioned interface
     definitions.

In this example we keep the styles in the placeholder selectors, and see them as styling based on an interface.


1. View the rules that extend placeholder selectors as protected, sanctioned "component" interfaces
2. View defining a placeholder selector as styling or defining the component based on its interface
3. For enhanced output control, use mixins to control the rules that extend placeholder selectors
    1.  See [[5 (extending in sass without the mess)]](http://www.smashingmagazine.com/2015/05/04/extending-in-sass-without-mess/) below
    1. Easier to opt-in/opt-out by defaulting out.
    1. Any unstyled but defined placeholder extends will throw "failed to @extend ...". hell when starting out
     with many components
    1. Reduces coupling to accessory classes, and freely enables creation of more without added complexity
    1. Aids in keeping files tidy and aware of what is happening in SCSS scope

Examples
-------

In the examples, only a few components are introduced: button and callout.

The button is any button, and in this case we define two interface definitions. One for a wide range of uses and one
for Bootstrap styled pages.

The callout just represents a custom component. Imagine a callout as a div with a border and background color. If
you are used to Foundation then "panel" might sound familiar or Bootstrap then "jumbotron" might.

 The point is that it's a container, like a dialog window. And the idea is that perhaps we want to make buttons
  inside callouts have a different margin to fit better on the page. How can we do this in a way that decouples
  the actual classnames used from the identifiers used in the SCSS files? How can we do this in a way that abstracts
  out implementation details (.btn or .ui-button or .big.button vs just button).

In the examples also demonstrated is a simple mixin file representing your own custom or favorite librarys. Bourb, sass*, whatev.

Lastly, the examples demonstrate organizing some more CSS to handle theme/skin/app specific details like mixins or
variables but also rules or more placeholder selectors and extends directives.

And it shows how to make a page that works in combination with them, or one that contains them for an all in one
 delivery.

[Enter the examples, Let's Get Started](examples/gettingstarted.md)!


FAQ
----

Q: I'm getting "failed to @extend ..."

A: When SASS is processing rules and finds an extend directive with no corresponding placeholder selector it will throw
 this error. Likely you have brought in a rule that extends a placeholder selector that you still need to define a
 placeholder selector for. This strategy inverts the typical flow so that the styler defines the placeholder selectors
  themselves, so this is normal and expected and means you need to go define it or disengage the rules that are using
  that extend directive.


References
------
- [1] http://sass-lang.com
  - [2] http://sass-lang.com/docs/yardoc/file.SASS_REFERENCE.html#extend
  - [3] http://sass-lang.com/documentation/file.SASS_REFERENCE.html#placeholders
  - [4] http://sass-lang.com/documentation/file.SASS_REFERENCE.html#placeholder_selectors_
- Learning Resources
    - [5] http://www.smashingmagazine.com/2015/05/04/extending-in-sass-without-mess/
        - Must read strategies and guidelines for using @extend and avoiding pitfalls
    - [6] http://miguelcamba.com/blog/2013/07/11/sass-placeholders-versus-mixins-and-extends/
        - Might help understanding between extends and placeholder selectors
        - Take some of the efficiency comments with a grain of salt
    - [7] http://thesassway.com/intermediate/using-object-oriented-css-with-sass
    - [8] http://thesassway.com/modular-css
    - [9] http://sassmeister.com/gist/8893261
      - Demonstrates use of @mixins with @extends and placeholder selectors (%)
      - (Not my gist)
- Prior Art
    - [10] http://www.slideshare.net/stubbornella/object-oriented-css
    - [11] https://smacss.com/
    - [12] https://en.bem.info/