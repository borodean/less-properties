**Deprecated. LESS supports [property interpolation](http://lesscss.org/features/#variables-feature-properties) since version 1.6.0.**

---

less-properties
===============
Mixin that adds some variable property support to [LESS](https://github.com/cloudhead/less.js).

usage
-----

Include this stylesheet to your project:
```scss
@import url('properties.less');
```

examples
--------

Now you can use variable properties:
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
  border-radius: 10px;
}
```

If you want to generate *only* prefixed properties, pass `false` as a fourth
argument:
```scss
.class {
  .property(border-radius, 10px, 'moz webkit o', false);
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
The `-less-property: property` junk line of code is a necessary sacrifice due to
the hack nature of this mixin. However, all browsers should normally skip this
line so it's just a matter of purity of code.

The mixin properly works with values that have spaces in them (e. g.
`1px solid red`) only when those are passed as an escaped string (e. g.
`~'1px solid red'`).

license
-------
Licensed under WTFPL.
See http://sam.zoy.org/wtfpl/COPYING for more details.
