==============
getCoreOptions
==============
.. code-block:: javascript

    accountStore.getCoreOptions(CoreBundle, SmartContracts)

returns the coreOptions for creation a new bcc CoreBundle and SmartContracts object.

----------
Parameters
----------
#. ``CoreBundle`` - |source CoreBundle|_ : blockchain-core ipfs bundle import (System.import('bcc'))
#. ``SmartContracts`` - ``SmartContracts``: smart-contracts ipfs bundle import (System.import('smart-contracts'))

-------
Returns
-------

``CoreBundle`` instance

-------
Example
-------

.. code-block:: typescript
  
  const options = await getCoreOptions(CoreBundle, SmartContracts);

--------------------------------------------------------------------------------

=============
getDomainName
=============

.. code-block:: javascript

    getDomainName(domainConfig, ...subLabels);

builds full domain name based on the provided domain config a module initalization.

----------
Parameters
----------

#. ``domainConfig`` - ``string[] | string``: The domain configuration 
#. ``...subLabels`` - ``string[]``: array of domain elements to be looked up and added at the lefthand

-------
Returns
-------

``string``:  the domain name

-------
Example
-------

.. code-block:: javascript

    const domain = nameResolver.getDomainName(['factory', 'root'], 'task');
    // returns 'task.factory.evan';

--------------------------------------------------------------------------------

====================
getLatestKeyProvider
====================

.. code-block:: javascript

  getLatestKeyProvider()

Returns a new KeyProvider or a existing instance if another was created before

-------
Returns
-------

|source KeyProvider|_ :  KeyProvider instance

-------
Example
-------

.. code-block:: javascript

    const keyProvider = getLatestKeyProvider();

--------------------------------------------------------------------------------

==============================
initializeEvanNetworkStructure
==============================

.. code-block:: javascript

  initializeEvanNetworkStructure()

Starts the whole dapp-browser. Imports the bcc and smart-contracts bundle, initializes them and the routing, queue and according things

-------
Example
-------

.. code-block:: javascript

    initializeEvanNetworkStructure()

Github Sample: `initializeEvanNetworkStructure <https://github.com/evannetwork/dapp-browser/blob/3cbd07427c8aec220b3bf1657b90c368c036c5de/src/index.html#L109>`_


.. required for building markup

.. |source CoreBundle| replace:: ``CoreBundle``
.. _source CoreBundle: https://github.com/evannetwork/blockchain-core/blob/develop/src/bundles/bcc/bcc.ts

.. |source KeyProvider| replace:: ``KeyProvider``
.. _source KeyProvider: ../dapp-browser/KeyProvider.html
