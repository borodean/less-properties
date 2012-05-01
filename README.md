less-properties
===============
Set of mixins that adds some variable property support to [LESS](https://github.com/cloudhead/less.js).

usage
-----

Include this file to your *.less stylesheet:
```scss
  @import url('properties.less');
```

examples
--------

You can use variable properties:
```scss
@property: border-radius;

.class-1 {
  .property(@property, 10px);
}

.class-2 {
  .property(@property, ~'10px 20px');
}
```
Which will output in:
```css
.class-1 {
  -less-property: property;
  border-radius: 10px;
}

.class-2 {
  -less-property: property;
  border-radius: 10px 20px;
}
```
You can also mass create properties with prefixes:
```scss
.class {
  .property(border-radius, 10px, 'moz webkit o');
}
```
Which will output in:
```css
.class {
  -less-property: property;
  -moz-border-radius: 10px;
  -webkit-border-radius: 10px;
  -o-border-radius: 10px;
}
```

known issues
------------
The `-less-property: property;` junk line of code is a neccesary sacrifice due to the hack nature of this set of mixins. However, all browsers should normally skip this line so it's just a matter of purity of code.