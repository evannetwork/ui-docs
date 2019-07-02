=====
utils
=====

.. list-table:: 
   :widths: auto
   :stub-columns: 1

   * - Source
     - `utils <https://github.com/evannetwork/ui-core/tree/master/dapps/ui.libs/src/utils.ts>`__

Util functions for handling things like deep equal or object cloning.

--------------------------------------------------------------------------------

.. _utils_deepEqual:

deepEqual
================================================================================

.. code-block:: typescript

  utils.deepEqual(a, b);

Deep equal for objects (https://github.com/epoberezkin/fast-deep-equal/blob/master/index.js). For perfomance increasing, file types, like (Uint8Array, ArrayBuffer, ...) will be ignored.

----------
Parameters
----------

#. ``a`` - ``object``: object a to check
#. ``b`` - ``object``: object b to check

-------
Returns
-------

``boolean``: true when deep equal, false when not

-------
Example
-------

.. code-block:: typescript

  utils.deepEqual(
    { a: 1, b: 2 },
    { a: 1, b: 2 },
  );




--------------------------------------------------------------------------------

.. _utils_cloneDeep:

cloneDeep
================================================================================

.. code-block:: typescript

  utils.cloneDeep(lodash, obj, ignoreFiles);

Lodash cloneDeep wrapper including ignoreFiles flag.

----------
Parameters
----------

#. ``lodash`` - ``any``: lodash instance
#. ``obj`` - ``any``: object that should be cloned
#. ``ignoreFiles`` - ``boolean``: should file entries be ignored?

-------
Returns
-------

``object``: deep cloned object

-------
Example
-------

.. code-block:: typescript

  const copy = utils.cloneDeep({ a: 1, b: 2 })
