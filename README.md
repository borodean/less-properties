less-properties
===============
Adds some variable property support to [LESS](https://github.com/cloudhead/less.js).

usage
-----

Include this file to your *.less stylesheet:
```scss
  @import url('less-properties.less');
```

examples
--------

You can use variable properties:
```scss
@property: border-radius;

.class {
  .property(@property, 10px);
  .property(@property, ~'10px 20px');
}
```
Which will output in:
```css
.class {
  -less-property: property;
  border-radius: 10px;
  border-radius: 10px 20px;
}
```
And mass create properties with prefixes:
```scss
@prefixes: 'moz webkit o';
@property: border-radius;

.class {
  .property(@prefixes, @property, 10px);
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