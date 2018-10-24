============
angular-sass
============

The `angular-sass <https://github.com/evannetwork/ui-angular-sass>`_ project contains several scss definitions for the evan.network Ionic featured DApp stack. By using the `dapp-browser <https://dashboard.evan.network>`_ including `angular-libs </angular-libs/index.html>`_ and `angular-core </angular-core/index.html>`_ all styling definitions are loaded. The `angular-libs </angular-libs/index.html>`_ includes the core ionic-angular styles and each style for libraries that are included (e.g.: @zxing/ngx-scanner). The angular-core includes all the evan.network specific angular-sass styles.

Installation
============

.. code-block:: sh

  npm i @evan.network/ui-angular-sass

Usage
=====

For the directly usage you can include and build in scss each file into your project. We recommend to dont include the css styles as imports to your application to reduce file size loading, it will be loaded by the evan.network library dapps. 

You can use the color definition variables, to assume, that you are ongoing with the evan.network styles. By using the `angular-gulp <https://github.com/evannetwork/angular-gulp>`_ you can use the following scss import to load the evan.network core variables:

::

  @import '@evan.network/ui-angular-sass/src/variables/colors';

The evan.network supports multiple themes (currently evan basic, evan-light theme). If you are using the color variables, you should define your scss styles for all themes. To do so, it's recommended to split your structual css from your color css. It will be like the following

::

  .my-custom-style {
    postion: relative;
    width: ...
  }

  @mixin customTheme($colors, $theme) {
    .my-custom-style {
      background-color: map-get($theme, background-color);
      color: map-get($theme, text-color);
    }
  }

  // apply custom styles for all themes
  @import '@evan.network/ui-angular-sass/src/theme';
  @each $theme, $definition in $evanThemes {
    @if $theme == 'evan' {
      @include customTheme(map-get($definition, colors), map-get($definition, evanStyles));
    } @else {
      .evan-#{$theme} {
        @include customTheme(map-get($definition, colors), map-get($definition, evanStyles));
      }
    }
  }

Color Themes
============

The evan.network supports multiple themes, so you can provide a custom look and feel to each DApp. Each color theme is represented by one color map defining file. A theme can include the following variables:

::

  /**************************************** color definitions ***************************************/
  $dark-blue: #023845;
  $dark-gray: #4a4a4a;
  $dark: #222222;
  $gray-blue: #556080;
  $gray-overlay: transparentize($dark-gray, 0.6);
  $green: #53e69d;
  $ligh-red: #fdeeee;
  $light-blue: #cce1ec;
  $light-cyan: #64c6c1;
  $light-gray: #c6d1d5;
  $light: #ffffff;
  $medium-blue: #24545e;
  $medium-cyan: #61cbc8;
  $medium-gray: #808080;
  $medium-light-gray: #b4b4b4;
  $medium-red: #e48991;
  $red: #ff7676;
  $white: #ffffff;
  $yellow: #fb7d00;

  /***************************************** evan definitions ***************************************/
  // general
  $border-color: #29757b;
  $primary: $medium-cyan;
  $refresher-border-color: transparent;

  // text
  $content-header-color: $primary;
  $label-text-color: $light;
  $link-color: $medium-cyan;
  $placeholder-color: $light-gray;
  $subdued-text-color: #c6d1d5;
  $text-color: $light;

  // backgrounds
  $background-backdrop: rgba(0, 0, 0, 0.5);
  $background-color: $dark-blue;
  $background-color-2: $medium-blue;
  $background-opacity: 0.5;
  $background-color-opacity: rgba($background-color, $background-opacity);
  $background-gradient-reverse: linear-gradient(-134deg, #0c3140 0%, #3b9c97 100%);
  $background-gradient: linear-gradient($dark-blue, $primary);
  $hover-color: $primary;
  $hover: rgba(0,0,0,0.1);

  // toolbar
  $background-toolbar-small: transparent;
  $background-toolbar-wide: transparent;

  // components
  $blockie-border: $white;
  $list-icon-color: $dark-gray;

  // grid
  $grid-list-item-shadow: 0 1px 3px 0 rgba(0, 0, 0, 0.2),
  0 1px 1px 0 rgba(0, 0, 0, 0.14),
  0 2px 1px -1px rgba(0, 0, 0, 0.12);

  // list
  $list-text-color: $text-color !default;
  $list-background-color: transparent !default;
  $list-border-color: $medium-cyan !default;

  // sizing
  $content-margin: 25px !default;
  $content-padding: 25px !default;

  /********************************************* exports ********************************************/
  // color definitions
  $colors: (
    alert: $yellow,
    danger: $red,
    dark-blue: $dark-blue,
    dark-gray: $dark-gray,
    dark: $dark,
    evan-blue-dark: $dark-blue,
    green: $green,
    light-gray: $light-gray,
    light-green: $green,
    light: $light,
    medium-gray: $medium-gray,
    primary: $primary,
    secondary: $green,
    transparency: rgba(2,56,69,0.3)
  );

  // map the colors so they can be used within mixins
  $evanStyles: (
    background-backdrop: $background-backdrop,
    background-color-2: $background-color-2,
    background-color-opacity: $background-color-opacity,
    background-color: $background-color,
    background-gradient-reverse: $background-gradient-reverse,
    background-gradient: $background-gradient,
    background-opacity: $background-opacity,
    background-toolbar-small: $background-toolbar-small,
    background-toolbar-wide: $background-toolbar-wide,
    blockie-border: $blockie-border,
    border-color: $border-color,
    content-header-color: $content-header-color,
    content-margin: $content-margin,
    content-padding: $content-padding,
    grid-list-item-shadow: $grid-list-item-shadow,
    hover: $hover,
    hover-color: $hover-color,
    label-text-color: $label-text-color,
    link-color: $link-color,
    list-background-color: $list-background-color,
    list-border-color: $list-border-color,
    list-icon-color: $list-icon-color,
    list-text-color: $list-text-color,
    placeholder-color: $placeholder-color,
    refresher-border-color: $refresher-border-color,
    subdued-text-color: $subdued-text-color,
    text-color: $text-color
  );

To define your own DApp theme, you can copy this content to your own DApp and include the following code. In this case, we assumes, that the file is called "custom-color-theme.scss".

::

  .evan-custom-style {
    @import '@evan.network/ui-angular-sass/src/theme';
    @import 'custom-color-theme';
    @include evanTheme($colors, $evanStyles);

    // my custom styles
  }

After this is defined, your DApp will include a full custom evan.network design. To enable this design, apply your custom-style class to your dapp entrypoint element (e.g. within the index.ts of your DApp).

::

  ...
  // Add project class name to the ion-app / .evan-dapp element for generalized styling
  ionicAppEl.className += ' .evan-custom-style';
  ...


Style Definitions
=================
.. toctree::
  :maxdepth: 1
  :glob:

  styles/*