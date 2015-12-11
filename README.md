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

### Set rules to single headings
In order to set specific rule to specific heading, just redefine the `$heading--definitions` as shown below (presenting the default value):
```scss
$heading--defintions: (
    1: (
        font-size: 36px,
    ),
    2: (
        font-size: 30px,
    ),
    3: (
        font-size: 24px,
    ),
    4: (
        font-size: 18px,
    ),
    5: (
        font-size: 14px,
    ),
    6: (
        font-size: 12px,
    ),
) !default;
```

this will generate for example :
```css
h1,
.h1 {
    font-size: 36px;
}

h2,
.h2 {
    font-size: 30px;
}

h3,
.h3 {
    font-size: 24px;
}

h4,
.h4 {
    font-size: 18px;
}

h5,
.h5 {
    font-size: 14px;
}

h6,
.h6 {
    font-size: 12px;
}
```


### Generate responsive classes
If you want to generate for example a class `.h1--sm` with as media querie `@media (min-width: 768px)` you can set the variable `$heading--responsive-breakpoint` which is a list with as key the prefix ('--sm') and as value the min-width media querie wanted (768px). Here is the default value :
```sass
$heading--responsive-breakpoint: (
    '--xs': 0,
    '--sm': 768px,
    '--md': 992px,
    '--lg': 1200px,
);
```
If you want to avoid responsive classes generations, just turn `$heading--responsive-breakpoint` as `false`.
