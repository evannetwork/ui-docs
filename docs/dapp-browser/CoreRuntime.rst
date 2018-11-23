===========
CoreRuntime
===========

.. list-table:: 
   :widths: auto
   :stub-columns: 1

   * - Source
     - `CoreRuntime <https://github.com/evannetwork/api-blockchain-core/blob/develop/src/bundles/bcc/bcc.ts>`__

The CoreRuntime is exported from the `bcc bundle </bcc/bcc-bundle.html>`_ instance. Is available after `initializeEvanNetworkStructure </dapp-browser/functions.html#initializeevannetworkstructure>`_ is executed.

--------------------------------------------------------------------------------


-------
Returns
-------

|source CoreInstance|_ : new CoreInstance

-------
Example
-------

.. code-block:: typescript

  core.CoreInstance.description.getDescription(...)

.. required for building markup

.. |source CoreInstance| replace:: ``CoreInstance``
.. _source CoreInstance: /bcc/bcc-bundle.html

