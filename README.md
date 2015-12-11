# heading-helper
Sass libray to quickly manage headings on css


## Usage

### Set Common property to all headings
You can easily add couple property/values to the following selector :

```scss
h1, h2, h3, h4, h5, h6 {}
```

You just need to redefine `$heading__all--block` list variable like this (showing in the same time !default value)

```scss
$heading__all--block: (
    line-height: 1.3,
) !default;
```

### Extends from 'all headings'
If you want inside the statement with all headings selected, to extend a specific selector, just redefine the variable `$heading__all--extend` (set to false as !default).

#### Example
this
```scss
$heading__all--extend: '.selector';

.selector {
    margin-bottom: 10px;
}
```
will compile into
```css
.selector, h1, h2, h3, h4, h5, h6 {
    margin-bottom: 10px;
}
```

### Extends to 'all headings'
In the other hand if you want the `.selector` to be extended into the the `h1, h2, h3, h4, h5, h6` use the extend placeholder `%headings` as in the example

#### Example
this
```scss
$heading__all--block: (
    line-height: 1.3,
);

.selector {
    @extend %headings;
}
```
will compile into
```css
h1, h2, h3, h4, h5, h6, .selector {
  line-height: 1.3; }
```
