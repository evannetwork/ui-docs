================================================================================
Solc
================================================================================

Smart `contracts solc <https://github.com/evannetwork/ui-dapp-browser/blob/develop/src/app/solc.ts>`_ representation. Is used to handle and sort the compiled |source SmartContracts|_ compiled object.

--------------------------------------------------------------------------------

.. _db_solc_constructor:

constructor
================================================================================

.. code-block:: typescript

  new Solc(SmartContracts);

Constructor of the Solc. Takes unformatted SmartContracts.

----------
Parameters
----------

#. ``SmartContracts`` - ``any``: compiled SmartContracts object.

-------
Returns
-------

``Solc``: Smart contracts export of the smart contracts project.

-------
Example
-------

.. code-block:: typescript
  
  const solc = new Solc({
    "AbstractDescribed": {
      "interface": "[...]"
    },
    "AbstractENS": {
      "interface": "[...]"
    },
    ...
  });

Usage: `Solc <https://github.com/evannetwork/ui-dapp-browser/blob/develop/src/app/bcc/bcc.ts>`_




--------------------------------------------------------------------------------

.. _db_solc_getContracts:

getContracts
================================================================================

.. code-block:: typescript

  solc.getContracts();

Takes the unformatted contracts from the constructor and format the object contract keys AbstractENS.sol => AbstractENS

-------
Returns
-------

``any``: Formatted Smart Contracts objects with shorted key names.

-------
Example
-------

.. code-block:: typescript

  solc.getContracts();
  // {
  //   "AbstractDescribed": {
  //     "interface": "[...]"
  //   },
  //   "AbstractENS": {
  //     "interface": "[...]"
  //   },
  //   ...
  // }

.. required for building markup
.. |source SmartContracts| replace:: ``SmartContracts``
.. _source SmartContracts: https://github.com/evannetwork/smart-contracts
