=====
queue
=====

The `evan queue <https://github.com/evannetwork/ui-dapp-browser/blob/develop/src/app/queue.ts>`_ is a global data handler for data synchronisation, for multiple DApp cross usage. It provides functions to save data entries and metadata globally within an browser indexDB.

**Be ware: Its not a final implementation of data saving into the blockchain. The dapp-browser handles only a initialized blockchain-core instance without any profile interaction. As a result of this, the queue synchronisation must be handle by the DApps. For a sample implementation for Angular 5, have a look at** |source queue_service|_ **(including QueueSequences, -Entries, Ids and QueueDispatchers) and** |source dapp_wrapper|_ **(for implementation reference, have a look at** |source queue_tutorial|_)




--------------------------------------------------------------------------------

.. _db_queue_entries:

entries
================================================================================

.. code-block:: typescript

  queue.entries

global available queue instances

--------------------------------------------------------------------------------

.. _db_queue_queueDB:

queueDB
================================================================================

.. code-block:: typescript

  queue.queueDB

initialized queue database

--------------------------------------------------------------------------------

.. _db_queue_lastAccountId:

lastAccountId
================================================================================

.. code-block:: typescript

  queue.lastAccountId

save the last account id to check, for which account the queue was loaded




--------------------------------------------------------------------------------

.. _db_queue_getStorageName:

getStorageName
================================================================================

.. code-block:: typescript

  queue.getStorageName();

gets the queue db storage name for the active account

-------
Returns
-------

``string``: The storage name.

-------
Example
-------

.. code-block:: typescript

  queue.getStorageName() // => 'evan-queue-${ activeAccountId }'





--------------------------------------------------------------------------------

.. _db_queue_getObjectStore:

getObjectStore
================================================================================

.. code-block:: typescript

  queue.getObjectStore(option);

Gets the "evan-queue" object store

----------
Parameters
----------

#. ``option`` - ``any``: dditional options for transaction

-------
Returns
-------

``any``: The object store.

-------
Example
-------

.. code-block:: typescript

  const objectStore = getObjectStore();
  const request = objectStore.get(accountId);




--------------------------------------------------------------------------------

.. _db_queue_updateQueue:

updateQueue
================================================================================

.. code-block:: typescript

  queue.updateQueue(arguments);

Loads the queue db for the current user and updates all global queue entries from the index db

-------
Returns
-------

``Promise`` returns ``Array<any>``: global queue entry array

-------
Example
-------

.. code-block:: typescript

  queue.updateQueue();




--------------------------------------------------------------------------------

.. _db_queue_storeQueue:

storeQueue
================================================================================

.. code-block:: typescript

  queue.storeQueue(queueEntries);

Function description

----------
Parameters
----------

#. ``queueEntries`` - ``Array<any>``: queue entries to save

-------
Returns
-------

``Promise`` returns ``any``: objectStore.put result

-------
Example
-------

.. code-block:: typescript

  await queue.storeQueue(queue.entries);

.. |source queue_service| replace:: ``angular-core queue-service``
.. _source queue_service: angular-core/services/queue

.. |source dapp_wrapper| replace:: ``angular-core dapp-wrapper component``
.. _source dapp_wrapper: angular-core/components/dapp-wrapper

.. |source queue_tutorial| replace:: ``angular queue tutorial``
.. _source queue_tutorial: https://evannetwork.github.io/dapps/angular/task-data-contract