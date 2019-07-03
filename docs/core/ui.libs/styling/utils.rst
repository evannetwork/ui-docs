===========
utils
===========

.. list-table:: 
   :widths: auto
   :stub-columns: 1

   * - Source
     - `utils <https://github.com/evannetwork/ui-core/tree/master/dapps/ui.libs/src/style/utils.scss>`__

This file includes evan specific scss mixins and functions.




--------------------------------------------------------------------------------

.. _utils_evanVariables:

evanVariables
================================================================================

.. code-block:: typescript

  evanVariables(arguments);

Maps a scss param enum to css variables `--evan-variables`.

----------
Parameters
----------

#. ``variables`` - ``object``: definitions

-------
Example
-------

.. code-block:: scss

  $theme-colors: (
    danger: cssVar('red'),
    dark: #023845,
    info: cssVar('blue'),
    light: cssVar('gray-200'),
    primary: cssVar('pink'),
    secondary: cssVar('cyan'),
    success: cssVar('green'),
    warning: cssVar('yellow'),
  );

  .theme-evan {
    @include evanVariables($themeEvan);
  }




--------------------------------------------------------------------------------

.. _utils_cssVar:

cssVar
================================================================================

.. code-block:: typescript

  cssVar(name);

Returns a variable mapped to the evan css variable scope

----------
Parameters
----------

#. ``name`` - ``string``: name that should be mapped

-------
Returns
-------

``string``: --evan-$name

-------
Example
-------

.. code-block:: scss

  color: cssVar('gray-500');




--------------------------------------------------------------------------------

.. _utils_keyframes:

keyframes
================================================================================

.. code-block:: typescript

  keyframes($animationName);

Shorthand multibrowser keyframes wrapper

----------
Parameters
----------

#. ``animationName`` - ``string``: The options used for calling

-------
Returns
-------

``Promise`` returns ``void``: resolved when done

-------
Example
-------

.. code-block:: typescript

  @keyframes jump {
    0% {
      transform: translateY(0);
    }
    20% {
      transform: translateY(0);
    }
  }