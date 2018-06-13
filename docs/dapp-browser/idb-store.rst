================================================================================
IDBStore
================================================================================

`IndexDB store wrapper <https://github.com/evannetwork/dapp-browser/blob/develop/src/app/idb-store.ts>`_.


--------------------------------------------------------------------------------

.. _module_name_constructor:

constructor
================================================================================

.. code-block:: typescript

  new IDBStore(dbName, storeName);

Creates a new IDBStore instance.

----------
Parameters
----------

#. ``dbName`` - ``string`` (default = 'keyval-store'): database name;
#. ``storeName`` - ``string`` (readonly, default = 'keyval'): store name within the database;

-------
Returns
-------

``IDBStore`` instance

-------
Example
-------

.. code-block:: typescript
  
  this.ipfsCacheStore = new IDBStore('ipfs-cache', 'ipfs-hashes');

--------------------------------------------------------------------------------

.. _db_idb_store_getDefaultStore:

getDefaultStore
================================================================================

.. code-block:: typescript

  ipfsCacheStore.getDefaultStore();

private: creates a new store or returns the latest one

-------
Returns
-------

``Promise`` returns ``void``: resolved when done

-------
Example
-------

.. code-block:: typescript

  // ...

--------------------------------------------------------------------------------

.. _db_idb_store_get:

get
================================================================================

.. code-block:: typescript

  ipfsCacheStore.get<Type>(key, store);

Gets a key from the IDB store.

----------
Parameters
----------

#. ``key`` - ``IDBValidKey``: key to load
#. ``store`` - ``IDBStore`` (default = getDefaultStore()): idb store to load the data from

-------
Returns
-------

``Promise`` returns ``Type``: returns a key value from idb store

-------
Example
-------

.. code-block:: typescript

  const result = await ipfsCacheStore.get('sample-key')

--------------------------------------------------------------------------------

.. _db_idb_store_set:

set
================================================================================

.. code-block:: typescript

  ipfsCacheStore.set(key, value, store);

sets a key value in a idb store

----------
Parameters
----------

#. ``key`` - ``IDBValidKey``: key to set the value for
#. ``value`` - ``any``: value to set
#. ``store`` - ``IDBStore`` (default = getDefaultStore()): idb store to set the value in

-------
Returns
-------

``Promise`` returns ``void``: resolved when done

-------
Example
-------

.. code-block:: typescript

  await ipfsCacheStore.set('sample-key', 'cool value')


--------------------------------------------------------------------------------

.. _db_store_del:

del
================================================================================

.. code-block:: typescript

  ipfsCacheStore.del(del, store);

delete a key from an idb store

----------
Parameters
----------

#. ``key`` - ``IDBValidKey``: key to delete
#. ``store`` - ``Function`` (default = getDefaultStore()): idb store to delete the data from

-------
Returns
-------

``Promise`` returns ``void``: resolved when done

-------
Example
-------

.. code-block:: typescript

  await ipfsCacheStore.del('sample-key')




--------------------------------------------------------------------------------

.. _db_idb_store_clear:

clear
================================================================================

.. code-block:: typescript

  ipfsCacheStore.clear(store);

Clears an idb store

----------
Parameters
----------

#. ``store`` - ``IDBStore`` (default = getDefaultStore()): The store;

-------
Returns
-------

``Promise`` returns ``void``: resolved when done

-------
Example
-------

.. code-block:: typescript

  await ipfsCacheStore.clear();




--------------------------------------------------------------------------------

.. _db_idb_store_keys:

keys
================================================================================

.. code-block:: typescript

  ipfsCacheStore.keys(store);

Gets the keys from an idb store

----------
Parameters
----------

#. ``store`` - ``IDBStore`` (default = getDefaultStore()): The store;

-------
Returns
-------

``Promise`` returns ``IDBValidKey[]``: keys of the idb store

-------
Example
-------

.. code-block:: typescript

  const keys = ipfsCacheStore.keys();