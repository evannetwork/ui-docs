====
ipfs
====

The `ipfs library <https://github.com/evannetwork/ui-dapp-browser/blob/develop/src/app/ipfs.ts>`_ handles the ipfs.evan.network connection settings and provides functions to handle restIpfs calls.


--------------------------------------------------------------------------------

.. _db_ipfs_ipfsConfig:

ipfsConfig
================================================================================

.. code-block:: typescript

  {
    host: 'ipfs.evan.network',
    port: '443',
    protocol: 'https',
    ipfsCache: null
  }

Ipfs connection configuration.




--------------------------------------------------------------------------------

.. _db_ipfs_restIpfs:

restIpfs
================================================================================

.. code-block:: typescript

  restIpfs.api_url(arguments);

The latest |source restIpfs|_ configuration and sets the current ipfsConfig to it.




--------------------------------------------------------------------------------

.. _db_ipfs_getRestIpfs:

getRestIpfs
================================================================================

.. code-block:: typescript

  ipfs.getRestIpfs();

Configures rest ipfs and returns the latest instance (used to get `restIpfs </dapp-browser/ipfs.html#restIpfs>`_). 

-------
Returns
-------

|source restIpfs|_: rest ipfs instance


--------------------------------------------------------------------------------

.. _db_ipfs_ipfsCatPromise:

ipfsCatPromise
================================================================================

.. code-block:: typescript

  ipfs.ipfsCatPromise(ipfsHash);

runs the restIpfs function and wraps it into a promise call

----------
Parameters
----------

#. ``ipfsHash`` - ``string``: ipfsHash to load

-------
Returns
-------

``Promise`` returns ``string``: content of the ipfs hash

-------
Example
-------

.. code-block:: typescript

  ipfs.ipfsCatPromise('Qmb...')

.. required for building markup

.. |source restIpfs| replace:: ``latest restIpfs``
.. _source restIpfs: /bcc/restipfs.html
