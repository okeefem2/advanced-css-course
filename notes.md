# Notes

rem relative to the root
em relative to the parent
vh and vw % relative to the viewport height/width

computed values are inherited, not declared
so em is translated to px by the engine and that value is inherited

border box sizing will make it so padding and border size do not add to the
total height/width of the box, but instead they decrease the size of the content
inside the box model to keep the defined size of the total box
Basically makes it so only the specified height-width are used for sizing the box

## Box types

### Block level box

display: [block, flex, list-item, table]
elements formatted visually as blocks
they take 100% of parents width
displayed vertically one after another (create line breaks before and after)
box model applied as normal, with padding and border added to total size

### Inline Box

display [inline]
Content is distributed in lines
box only take space needed
no line breaks
no height/width and paddings/margins are only horizontal

### Inline Block Box

display [inline-block]
box only takes contents space
no line-breaks
box model applies as normal though, height/width and all padding/margins
are applied

## Positioning Schemes

### Normal Flow

position [relative]
is the default flow
no floating, no absolute positioning
elements laid out according to source order

### Floats

float [left, right]
takes the element completely out of the normal flow and pushs it as far
to the left/right as it can get until it hits the end of it's container
or it hits another floated element

### Absolute Positioning

position [absolute, fixed]
element has no impact on surrounding elements (fixed in place no matter what else is going on)
top,bottom,left,right are used to position the element in relation to
it's nearest relatively positioned parent container

### Stacking contexts

determines order that elements are rendered, most common is z-index
the higher in the stack, the later they are painted

### Think

Component driven design (or atomic design -- <http://bradfrost.com/)>

Everything is made of small reusable components!

### Build

BEM Block Element Modifier

.block
.block__element
.block__element--modifier
Block - standalone component that is meaningful on its own
Element - part of a block that has no meaning on its own, it is dependent on the block as a parent of some sort
Modifier - helps distinguish different elements, to make a variation on the base element

### Architecture

7-1 pattern (<https://sass-guidelin.es/)>
7 different folders for partial sass files
1 main sass file to import all others into a compiled css stylesheet

base/
components/
layouts/
pages/
themes/
abstracts/
vendors/

## Responsive design

max-width and min-width media queries
ex. 600px, is the viewport width <=600px? if true then the mediaquery is applied
if false, then it is not applied. If multiple media queries specify the same attr, the last one in the code has precedence. Media Queries do not add any specificity to the style.

max-width is used in a desktop first approach (adjust as the screen size decreases), min-width used in a mobile first approach (adjust as the screen size increases)

### Selecting breakpoints

* Bad: using device widths as breakpoints, not maintainable
* Good: use average most used device widths across the devices
* Perfect: ignore devices and design breaks to the content in the site

In a media query, the em and rems are relative to the root of the browser, not a root set by css on the site

## Responsive Images

### Resolution switching

Changing screen size

### Density switching

Changing screen resolution, number of pixels used to render a pixel of design (high res is 2x --> most smart screens)

### Art Direction

change the image served for smaller/ larger screens

## Build process

### Compilation

### Concatenation

using concat package to concat all css files into 1

### Prefixing

using postcss cli and autoprefixer packages, sets css to target last 10 versions all browsers and will add all the prefixes needed to our attributes

### Compressing

using node-sass package to compress the styles

## CSS Grid

emmet wizardry
(figure.gallery__item.gallery__item--$>img.gallery__img[src="img/gal-$.jpeg"][alt="gallery image $"])*14
