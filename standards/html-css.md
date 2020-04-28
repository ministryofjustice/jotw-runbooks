---
category: Style guide
expires: 2019-03-31
---

# HTML and CSS

## HTML5

Our team uses HTML5 language features as default, when possible, building the websites html markup.

Example using semantic elements:
<p align="left"><img src="https://www.w3schools.com/html/img_sem_elements.gif "></p>

Useful resources
* [Mozilla Offical HTML5 Docs](https://developer.mozilla.org/en-US/docs/Web/Guide/HTML/HTML5)

## CSS

When possible, use flexbox and CSS grid to achieve frontend page layouts.

### Flexbox

* [Basic concepts of Flexbox](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Flexible_Box_Layout/Basic_Concepts_of_Flexbox)

### CSS GRID

Useful resources
* [CSS GRID with Wes Boss](https://cssgrid.io/) (free)
* [Grid by Example](https://gridbyexample.com/)

If not covered yet in this documentation, as a default refer to [Google's documentation](https://google.github.io/styleguide/jsguide.html).

### SASS

Preference in the team to use SASS, unless there is a legitimate reason to use something else. SASS however, is mature, well documented, feature rich and used by Gov UK.

* [SASS offical site](https://sass-lang.com/)

### BEM

CSS methodology is the core approach we current strive for in the team. 

Further information available at [BEM intro](http://getbem.com/introduction/)

## Image use

* Use SVGs for logos
* Keep images out of Git if possible

## Webpack

We current use webpack across all our sites and plugins where possible. In an order to keep things consistent, it is encouraged to use Webpack unless there is a good reason to use another compiler.
* [Webpack site](https://webpack.js.org/)

### Laravel Mix

Ontop of WebPack we use Laravel Mix, which basically simplifies Webpack usage. Laravel Mix can be added via NPM.
* [Laravel Mix](https://laravel-mix.com/docs/5.0/installation)