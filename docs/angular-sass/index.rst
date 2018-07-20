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

You can use the color definition variables, to assume, that you are ongoing with the evan.network styles. By using the `angular-gulp <https://github.com/evannetwork/angular-gulp>`_ you can use the following scss import to load the evan.network variables:

::

  @import 'ui-angular-sass/src/variables/colors';


- background colors

  - ``$dark-blue``: ``#023845``;
  - ``$medium-blue``: ``#24545e``;

- top bar color
  
  - ``$light-cyan``: ``#64c6c1``;
  - ``$medium-cyan``: ``#61cbc8``;

- font color

  - ``$light-gray``: ``#c6d1d5``;

- complementary

  - ``$green``: ``#53e69d``;
  - ``$red``: ``#ff7676``;

- additional colors

  - ``$dark-gray``: ``#4a4a4a``;
  - ``$gray-blue``: ``#556080``;
  - ``$gray-overlay``: ``transparentize($dark-gray, 0.6)``;
  - ``$ligh-red``: ``#fdeeee``;
  - ``$light-blue``: ``cce1ec``;
  - ``$medium-gray``: ``#808080``;
  - ``$medium-light-gray``: ``#b4b4b4``;
  - ``$medium-red``: ``#e48991``;
  - ``$white``: ``#ffffff``;
  - ``$yellow``: ``#fb7d00``;

--------------------------------------------------------------------------------

- ionic styles

  - ``$light``: ``#ffffff``;
  - ``$dark``: ``#222222``;
  - ``$primary``: ``$medium-cyan``;
  - ``$colors``
  
    - ``primary``: ``$primary``;
    - ``secondary``: ``$green``;
    - ``danger``: ``$red``;
    - ``light``: ``$light``;
    - ``dark``: ``$dark``;
    - ``light-gray``: ``$light-gray``;
    - ``medium-gray``: ``$medium-gray``;
    - ``dark-gray``: ``$dark-gray``;
    - ``evan-blue-dark``: ``$dark-blue``;
    - ``green``: ``$green``;
    - ``light-green``: ``$green``;
    - ``dark-blue``: ``$dark-blue``;
    - ``alert``: ``$yellow``;

--------------------------------------------------------------------------------

- general

  - ``$border-color``: ``#24545e``;
  - ``$refresher-border-color``: ``transparent``;

- text

  - ``$text-color``: ``$light !default``;
  - ``$link-color``: ``$medium-cyan !default``;
  - ``$subdued-text-color``: ``#c6d1d5 !default``;
  - ``$label-text-color``: ``$light``;

- backgrounds

  - ``$background-color``: ``$dark-blue``;
  - ``$background-color-2``: ``$medium-blue``;
  - ``$background-gradient``: ``linear-gradient(-134deg, #3b9c97 0%, #0c3140 100%)``;
  - ``$background-gradient-reverse``: ``linear-gradient(-134deg, #0c3140 0%, #3b9c97 100%)``;
  - ``$background-backdrop``: ``rgba(0, 0, 0, 0.5)``;
  - ``$hover``:  ``$medium-blue``;

- toolbar
  
  - ``$background-toolbar-wide``: ``$light-cyan``;
  - ``$background-toolbar-small``: ``$light-cyan``;
  - ``$toolbar-height``: ``56px``;

- components
  
  - ``$blockie-border``: ``$white``;
  - ``$list-icon-color``: ``$dark-gray``;

- grid

  - ``$grid-list-item-shadow``: ``0 1px 3px 0 rgba(0, 0, 0, 0.2), 0 1px 1px 0 rgba(0, 0, 0, 0.14), 0 2px 1px -1px rgba(0, 0, 0, 0.12)``;

- list

  - ``$list-text-color``: ``$text-color !default``;
  - ``$list-background-color``: ``$background-color !default``;
  - ``$list-border-color``: ``$medium-cyan !default``;

- sizing

  - ``$content-margin``: ``25px !default``;
  - ``$content-padding``: ``25px !default``;

Style Definitions
=================
.. toctree::
  :maxdepth: 1
  :glob:

  styles/*