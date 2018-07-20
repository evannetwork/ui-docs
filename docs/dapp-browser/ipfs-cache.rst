=========
IPFSCache
=========

================================================================================
IPFSCache
================================================================================

`IPFS cache <https://github.com/evannetwork/ui-dapp-browser/blob/develop/src/app/ipfs-cache.ts>`_ that uses an index db to store ipfs results in. Will be passed to the `blockchain-core for automated caching </bcc/bcc-bundle.html>`_.

--------------------------------------------------------------------------------

.. _db_ipfs_cache_constructor:

constructor
================================================================================

.. code-block:: typescript

  new IPFSCache();

IPFS cache that uses an index db to store ipfs results in.

-------
Returns
-------

``IPFSCache`` instance

-------
Example
-------

.. code-block:: typescript
  
  const ipfsCache = new IPFSCache();





--------------------------------------------------------------------------------

.. _db_ifps_cache_get:

get
================================================================================

.. code-block:: typescript

  ipfsCache.get(hash);

gets an cached ipfs result

----------
Parameters
----------

#. ``hash`` - ``string``: ipfs hash to load the data from

-------
Returns
-------

``Promise`` returns ``string``: ipfs result


--------------------------------------------------------------------------------

.. _db_ipfs_cache_add:

add
================================================================================

.. code-block:: typescript

  ipfsCache.add(hash, data);

adds a ipfs value into the idb store cache

----------
Parameters
----------

#. ``hash`` - ``string``: ipfs hash to store the data for
#. ``data`` - ``any``: data to store for the ipfs hash

-------
Returns
-------

``Promise`` returns ``void``: resolved when done
