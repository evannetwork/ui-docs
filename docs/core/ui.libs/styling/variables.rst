=========
variables
=========

.. list-table:: 
   :widths: auto
   :stub-columns: 1

   * - Source
     - `definitions <https://github.com/evannetwork/ui-core/tree/master/dapps/ui.libs/src/style/definitions/evan.theme.scss>`__

----------
$themeEvan
----------

SCSS map, including all for the evan style available parameters. Using this set of parameters, a custom evan.network theme can be created easily. The bootstrap version that is used within featured dapps, is adjusted to handle css variables. As a result of this, the theme can be changed at runtime.

.. code-block:: scss

  .theme-evan {
    @include evanVariables($themeEvan);
  } 

For which parameters are available, please have a look at the `evan.theme <https://github.com/evannetwork/ui-core/tree/master/dapps/ui.libs/src/style/definitions/evan.theme.scss>`__.
