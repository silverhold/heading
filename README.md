# heading-helper
Sass library to quickly manage headings on css

## Getting Started
You can download heading-helper via bower using the following command:
```shell
$ bower install trowel-heading
```


## Usage
Include to your scss stylesheet the `heading-helper.scss` file. You also need to include before `heading-helper.scss` the `responsive-helper.scss` file from the [trowel-responsive library](https://github.com/trowel/responsive).

### The `$headings` variable
The `trowel-heading` sass library has for purpose to quickly generate responsive heading class. To fit perfectly thoses classes to your needs, you will just have to override the `$headings` variable which you can find into the `partial/_parameters.scss` partial.

The `$headings` variable is a map like just below :

```scss
    $headings: (
        'all': (
            'line-height': 1.3,
        ),
        'h1': (
            'font-size': 36px,
        ),
        'h2': (
            'font-size': 30px,
        ),
        'h3': (
            'font-size': 24px,
        ),
        'h4': (
            'font-size': 18px,
        ),
        'h5': (
            'font-size': 14px,
        ),
        'h6': (
            'font-size': 12px,
        ),
    );
```

The first key of the `$heading` map is `'all'` which has for value a map with a list of property/value common to all your headings.

After the `'all'`, each heading element has a key with a map composed the same way: a list of property/value, but this time only for the heading in question.

Here an example of what the `$heading` setted before will output in css

```css
h1, .h1, h2, .h2, h3, .h3, h4, .h4, h5, .h5, h6, .h6 {
    line-height: 1.3;
}

h1,
.h1 {
    font-size: 36px;
};

h2,
.h2 {
    font-size: 30px;
};

h3,
.h3 {
    font-size: 24px;
};

h4,
.h4 {
    font-size: 18px;
};

h5,
.h5 {
    font-size: 14px;
};

h6,
.h6 {
    font-size: 12px;
};
```

### Responsiveness
In order to generate properties with specific breakpoint from [trowel-responsive library](https://github.com/trowel/responsive), you can into each sub-map of the `$headings` variable ('all', 'h1', 'h2', 'h3', 'h4', 'h5', 'h6') set as key one of the breakpoint from the [`$breakpoints` map](https://github.com/Trowel/responsive/blob/master/_parameters.scss) and as value a list of property/value.

The media query are generated with the mixin [media-query](https://github.com/Trowel/responsive#using-mixin) and the 'mobile-first' philosophy.

So the current example :

```scss
$breakpoints: (
  'xs': ('min': 0, 'max': 374px),
  'sm': ('min': 375px, 'max': 524px),
  'md': ('min': 525px, 'max': 959px),
  'lg': ('min': 960px, 'max': 1199px),
  'xl': ('min': 1200px, 'max': '∞')
);

$headings: (
    'all': (
        'line-height': 1.3,
        'md': (
            'line-height': 1.4,
        ),
    ),
    'h1': (
        'letter-spacing': .125em,
        'font-size': 30px,
        'sm': (
            'font-size': 32px,
        ),
        'md': (
            'font-size': 34px,
        ),
        'lg': (
            'font-size': 36px,
        ),
    ),
    'h2': (
        'font-size': 30px,
    ),
    'h3': (
        'font-size': 24px,
    ),
    'h4': (
        'font-size': 18px,
    ),
    'h5': (
        'font-size': 14px,
    ),
    'h6': (
        'font-size': 12px,
    ),
) !default;
```

Generates this css :
```css
h1, .h1, h2, .h2, h3, .h3, h4, .h4, h5, .h5, h6, .h6 {
    line-height: 1.3;
}

@media (min-width: 525px) {
    h1, .h1, h2, .h2, h3, .h3, h4, .h4, h5, .h5, h6, .h6 {
        line-height: 1.4;
    }
}

h1, .h1 {
    letter-spacing: 0.125em;
    font-size: 30px;
}

@media (min-width: 375px) {
    h1, .h1 {
        font-size: 32px;
    }
}

@media (min-width: 525px) {
    h1, .h1 {
        font-size: 34px;
    }
}

@media (min-width: 960px) {
    h1, .h1 {
        font-size: 36px;
    }
}

h2, .h2 {
    font-size: 30px;
}

h3, .h3 {
    font-size: 24px;
}

h5, .h5 {
    font-size: 14px;
}

h6, .h6 {
    font-size: 12px;
}
```
