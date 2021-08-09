---
title: Flexbox
description: Flexbox의 기본
img : /flexbox.png
alt: my first blog post
author:
  name: Byoungil Andrew Kwun
  bio: Georgia Tech
---

# flexbox
[flexbox completed guide](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)

### Terms
- main axis : primary axis along which flex items are 
laid out(not necessarily horizontal); 
depends on flex-direction
- cross axis : The axis perpendicular to the main axis is called the cross axis. 
Its direction depends on the main axis direction.

### Properties
##### properties for parent (flex container)


###### display
```
.container {
  display: flex; /* or inline-flex */
}
```
###### flex-direction : establishes the main-axis
```
.container {
  flex-direction: row | row-reverse | column | column-reverse;
}
```
###### flex-wrap : allow the items to wrap as needed
```
.container {
  flex-wrap: nowrap | wrap | wrap-reverse;
}
```
###### flex-flow : shorthand for the flex-direction and flex-wrap 
```
.container {
  flex-flow: column wrap; // default : row wrap
}
```
###### justify-content :defines the alignment along the main axis. 
```
.container {
  justify-content: flex-start | flex-end | center | space-between | space-around | space-evenly | start | end | left | right ... + safe | unsafe;
}
```
###### align-items : defines the default behavior for how flex items are laid out along the cross axis on the current line.
```
.container {
  justify-content: flex-start | flex-end | center | space-between | space-around | space-evenly | start | end | left | right ... + safe | unsafe;
}
```

###### align-content : This aligns a flex container’s lines within when there is extra space!!!! in the cross-axis, similar to how justify-content aligns individual items within the main-axis.
 -  This property only takes effect on multi-line flexible containers, where flex-flow is set to either wrap or wrap-reverse). A single-line flexible container (i.e. where flex-flow is set to its default value, no-wrap) will not reflect align-content.
```
.container {
  align-content: flex-start | flex-end | center | space-between | space-around | space-evenly | stretch | start | end | baseline | first baseline | last baseline + ... safe | unsafe;
}
```

