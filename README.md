# material-bottom-nav

[![license][license-badge]][license]
[![npm version][npm-badge]][npm]
[![npm downloads][downloads-badge]][downloads]
[![dependencies status][dependencies-badge]][dependencies]
[![devDependencies status][devDependencies-badge]][devDependencies]
[![peerDependencies status][peerDependencies-badge]][peerDependencies]

A bottom navigation bar adhering to the [Material Design specification][spec].
It is written purely using [Sass][sass] mixins which allow you to apply the
style rules to any class, as shown in the [demo page's stylesheet][demo.scss].

A running demonstration can be found [here][demo].

[![Three actions](/preview-3.png)](https://michaelbull.github.io/material-bottom-nav/) [![Five actions, hidden labels](/preview-5.png)](https://michaelbull.github.io/material-bottom-nav/labels-hide.html)

<br />
<br />

## Installation

Install the package via npm:

```
npm install --save material-bottom-nav
```

Then import the [Sass mixin][mixin]:

```sass
@import '~material-bottom-nav';
```

## Usage

Apply the the mixin to a class:

```sass
.bottom-nav {
  @include bottom-nav($background-color: #009688, $active-color: #FFFFFF, $inactive-color: #E0E0E0, $hide-inactive-labels: true);
}
```

The `$hide-inactive-labels` argument defaults to `false`. It is used to hide the
text label of any inactive actions, as suggested by the
[style specification][style-spec] if you have more than three actions visible.

Given the example above the mixin will register a set of style rules that adhere
to the [“Block Element Modifier” methodology][bem]:

- `.bottom-nav`
  - The [flexbox][flexbox] parent element.
- `.bottom-nav__action`
  - An individual navigation action.
- `.bottom-nav__action--active`
  - A modifier class to indiciate that the action is the currently active.
- `.bottom-nav__icon`
  - The [SVG][svg] icon for an action.
- `.bottom-nav__label`
  - The text label for an action.

The DOM structure for the component should follow the heirarchy as shown below:

```html
<nav class="bottom-nav">
  <a class="bottom-nav__action" href="#">
    <svg class="bottom-nav__icon" viewBox="0 0 24 24">
      <path d="M11,7V12.11L15.71,14.9L16.5,13.62L12.5,11.25V7M12.5,2C8.97,2 5.91,3.92 4.27,6.77L2,4.5V11H8.5L5.75,8.25C6.96,5.73 9.5,4 12.5,4A7.5,7.5 0 0,1 20,11.5A7.5,7.5 0 0,1 12.5,19C9.23,19 6.47,16.91 5.44,14H3.34C4.44,18.03 8.11,21 12.5,21C17.74,21 22,16.75 22,11.5A9.5,9.5 0 0,0 12.5,2Z"></path>
    </svg>
    <span class="bottom-nav__label">Recents</span>
  </a>

  <a class="bottom-nav__action bottom-nav__action--active" href="#">
    <svg class="bottom-nav__icon" viewBox="0 0 24 24">
      <path d="M12,21.35L10.55,20.03C5.4,15.36 2,12.27 2,8.5C2,5.41 4.42,3 7.5,3C9.24,3 10.91,3.81 12,5.08C13.09,3.81 14.76,3 16.5,3C19.58,3 22,5.41 22,8.5C22,12.27 18.6,15.36 13.45,20.03L12,21.35Z"></path>
    </svg>
    <span class="bottom-nav__label">Favorites</span>
  </a>

  <a class="bottom-nav__action" href="#">
    <svg class="bottom-nav__icon" viewBox="0 0 24 24">
      <path d="M12,20A8,8 0 0,1 4,12A8,8 0 0,1 12,4A8,8 0 0,1 20,12A8,8 0 0,1 12,20M12,2A10,10 0 0,0 2,12A10,10 0 0,0 12,22A10,10 0 0,0 22,12A10,10 0 0,0 12,2M12,12.5A1.5,1.5 0 0,1 10.5,11A1.5,1.5 0 0,1 12,9.5A1.5,1.5 0 0,1 13.5,11A1.5,1.5 0 0,1 12,12.5M12,7.2C9.9,7.2 8.2,8.9 8.2,11C8.2,14 12,17.5 12,17.5C12,17.5 15.8,14 15.8,11C15.8,8.9 14.1,7.2 12,7.2Z"></path>
    </svg>
    <span class="bottom-nav__label">Nearby</span>
  </a>
</nav>
```

The example above includes icons from the
[Material Design Icons][material-icons] project
([LICENSE][material-icons-license]).

## Customization

The box-model and colors of the individual styles within this component can be
configured by overriding the default variable values defined in
[`bottom-nav.scss`][mixin]. Remember to define your overrides **before**
importing the mixin file, for example:

```sass
$bottom-nav-action-horizontal-margin: 4px; // reduce the horizontal gutter between actions
$bottom-nav-icon-font-size: 28px; // increase the icon size

@import '~material-bottom-nav';

.bottom-nav {
  @include bottom-nav(#009688, #FFFFFF, #E0E0E0);
}
```

## Contributing

Bug reports and pull requests are welcome on [GitHub][github].

## License

This project is available under the terms of the ISC license. See the
[`LICENSE`][license] file for the copyright information and licensing terms.

[license-badge]: https://img.shields.io/github/license/michaelbull/material-bottom-nav.svg?style=flat-square
[license]: https://github.com/michaelbull/material-bottom-nav/blob/master/LICENSE
[npm-badge]: https://img.shields.io/npm/v/material-bottom-nav.svg?style=flat-square
[npm]: https://www.npmjs.com/package/material-bottom-nav
[downloads-badge]: https://img.shields.io/npm/dt/material-bottom-nav.svg?style=flat-square
[downloads]: https://www.npmjs.com/package/material-bottom-nav
[dependencies-badge]: https://david-dm.org/michaelbull/material-bottom-nav.svg?style=flat-square
[dependencies]: https://david-dm.org/michaelbull/material-bottom-nav
[devDependencies-badge]: https://david-dm.org/michaelbull/material-bottom-nav/dev-status.svg?style=flat-square
[devDependencies]: https://david-dm.org/michaelbull/material-bottom-nav?type=dev
[peerDependencies-badge]: https://david-dm.org/michaelbull/material-bottom-nav/peer-status.svg?style=flat-square
[peerDependencies]: https://david-dm.org/michaelbull/material-bottom-nav?type=peer
[spec]: https://material.io/guidelines/components/bottom-navigation.html
[sass]: http://sass-lang.com/guide
[demo.scss]: https://github.com/michaelbull/material-bottom-nav/blob/master/demo/index.scss#L72
[demo]: https://michaelbull.github.io/material-bottom-nav/
[mixin]: https://github.com/michaelbull/material-bottom-nav/blob/master/bottom-nav.scss#
[style-spec]: https://material.io/guidelines/components/bottom-navigation.html#bottom-navigation-style
[bem]: http://getbem.com/
[flexbox]: https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Flexible_Box_Layout/Using_CSS_flexible_boxes
[svg]: https://developer.mozilla.org/en-US/docs/Web/SVG
[material-icons]: https://materialdesignicons.com/
[material-icons-license]: https://github.com/Templarian/MaterialDesign/blob/master/license.txt
[github]: https://github.com/michaelbull/material-bottom-nav
