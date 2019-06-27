=====
Queue
=====

.. list-table:: 
   :widths: auto
   :stub-columns: 1

   * - Source
     - `Queue <https://github.com/evannetwork/ui-core/tree/master/dapps/ui.libs/src/Queue.ts>`__

Structure for handling dispatcher instances and managing data of them. It will start and register
dispatchers and offers the possiblity to save the dispatchers runtime data within the browsers
IndexDB.


#. ``entries`` - ``object``: global available queue instance
#. ``accountId`` - ``string``: save the last account id to check, for which account the queue was loaded
#. ``initializing`` - ``Promise<void>``: Promise to handle queueDB loading finish
#. ``storageName`` - ``string``: Storage name for the current user.

--------------------------------------------------------------------------------

.. _queue_constructor:

constructor
================================================================================


.. code-block:: typescript

  new Container(options, config);

Create new ``Queue`` instance. It will be scoped to one single accountId, so each Queue data will
saved to different IndexDB entries. So when users uses the same browser, they will not affect each
other.

----------
Parameters
----------

#. ``accountId`` - ``string``: accountId for that the Queue should be scoped.

-------
Returns
-------

``Queue`` instance

-------
Example
-------
- `Usage Example <https://github.com/evannetwork/ui-core/blob/master/dapps/ui.libs/src/Dispatcher.ts>`__

.. code-block:: typescript

  const uiCoreQueue = await new EvanQueue(runtime.activeAccount);






--------------------------------------------------------------------------------

.. _queue_openDB:

openDB
================================================================================

.. code-block:: typescript

  queue.openDB(version);

Open the correct index db for the current user. Checks also for upgrades.

----------
Parameters
----------

#. ``version`` - ``object``: current db version

-------
Returns
-------

``Promise`` returns ``void``: resolved when IndexDB was initialized

-------
Example
-------

.. code-block:: typescript

  async initialize(): Promise<any> {
    if (!queueDB) {
      if (!this.initializing) {
        try {
          queueDB = await this.openDB();
        } catch (ex) {
          console.error(ex);
        }
      }

      await this.initializing;
    }
  }




--------------------------------------------------------------------------------

.. _queue_intialize:

intialize
================================================================================

.. code-block:: typescript

  queue.intialize();

Creates a queueDB if missing and open all connections. Is called by the Queue interaction functions itself.

-------
Returns
-------

``Promise`` returns ``void``: Resolved when ``openDB`` has finished. Will use the ``initialized`` flag to only be initialized once.

-------
Example
-------

.. code-block:: typescript

  await this.initialize();




--------------------------------------------------------------------------------

.. _queue_getStorageName:

getStorageName
================================================================================

.. code-block:: typescript

  queue.getStorageName();

gets the queue db storage name for the active account

-------
Returns
-------

``string``: The storage name (e.g. 'evan-queue-' + this.accountId)

-------
Example
-------

.. code-block:: typescript

  this.storageName = this.getStorageName();




--------------------------------------------------------------------------------

.. _queue_getObjectStore:

getObjectStore
================================================================================

.. code-block:: typescript

  queue.getObjectStore(option);

Gets the "evan-queue" IndexDB object store.

----------
Parameters
----------

#. ``option`` - ``object``: additional options for queueDB.transaction

-------
Returns
-------

``Promise`` returns ``IDBObjectStore``: `IDBObjectStore <https://developer.mozilla.org/en-US/docs/Web/API/IDBObjectStore>`_

-------
Example
-------

.. code-block:: typescript

  const objectStore = this.getObjectStore('readonly');




--------------------------------------------------------------------------------

.. _queue_load:

load
================================================================================

.. code-block:: typescript

  queu.load(dispatcherId);

Loads the queue db for the current user and updates all global queue entries from the index db

----------
Parameters
----------

#. ``dispatcherId`` - ``string``: The `dispatcher identifier <./dispatcher.html#constructor>`_ (`${ dappEns }|||${ name }`)

-------
Returns
-------

``Promise`` returns ``void``: resolved when done

-------
Example
-------

.. code-block:: typescript

  const entries = await this.load(`addressbook.evan|||saveDispatcher`);




--------------------------------------------------------------------------------

.. _queue_save:

save
================================================================================

.. code-block:: typescript

  queue.save(dispatcherId, entryId, data?);

Store for the current user its current global entries to the queue db.  It loads all current saved
entries and checks for the provided entryId. If the entryId is empty, the entry will be deleted.

----------
Parameters
----------

#. ``dispatcherId`` - ``string``: The `dispatcher identifier <./dispatcher.html#constructor>`_ (`${ dappEns }|||${ name }`)
#. ``entryId`` - ``string``: random id string
#. ``data`` - ``any`` (optional): any data that should be saved

-------
Returns
-------

``Promise`` returns ``any``: objectStore.

-------
Example
-------

.. code-block:: typescript

  await this.queue.save(this.dispatcher.id, this.id, {
    data: this.data,
    error: this.error,
    status: this.status,
    stepIndex: this.stepIndex,
    customEvePrice: this.customEvePrice,
  });