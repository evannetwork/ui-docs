=========
EvanQueue
=========

The evan queue synchronisation implementation. You can add entries using QueueIDs and data properties. The configured dispatchers and its Angular modules are loaded during runtime, so each dispatcher can handle angular services, also, when the DApp is not openend.

- ``queue`` - |source dapp_browser_queue|_: dapp-wrapper queue reference object to handle alsome global queue;
- ``loading`` - ``boolean``: is the queue loading?;
- ``exception`` - ``boolean``: has the queue some exceptions?;
- ``allSyncing`` - ``boolean``: are all queue entries syncing?;

.. |source dapp_browser_queue| replace:: ``QueueId``
.. _source dapp_browser_queue: /dapp-browser/queue.html




--------------------------------------------------------------------------------

queueCount
================================================================================

.. code-block:: typescript

  queueService.queueCount();

Returns the count of entries within the queue.

-------
Returns
-------

``number``: dappBrowser.queue.entries.length

-------
Example
-------

.. code-block:: typescript

  queueService.queueCount();




--------------------------------------------------------------------------------

isInstantSave
================================================================================

.. code-block:: typescript

  queueService.isInstantSave();

Check if the queue entries should enqueued instant or only over the queue component. (currently always enabled)

-------
Returns
-------

``boolean``: True if instant save, False otherwise.

-------
Example
-------

.. code-block:: typescript

  queueService.isInstantSave();





--------------------------------------------------------------------------------

.. _document_loadModule:

loadModule
================================================================================

.. code-block:: typescript

  queueService.loadModule(ensAddress);

Load an module from ens.

----------
Parameters
----------

#. ``ensAddress`` - ``string``: Ens address to load the module from

-------
Returns
-------

``any``: module instance

-------
Example
-------

.. code-block:: typescript

  queueService.loadModule('taskboard.evan')




--------------------------------------------------------------------------------

.. _document_loadDispatcherForQueue:

loadDispatcherForQueue
================================================================================

.. code-block:: typescript

  queueService.loadDispatcherForQueue(queueEntry);

Load dispatchers for the current queue

----------
Parameters
----------

#. ``queueEntry`` - ``object``: queue entry to load the dispatcher for

-------
Returns
-------

``Promise`` returns ``void``: applies the dispatcher instance to the queue entry

-------
Example
-------

.. code-block:: typescript

  this.loadDispatcherForQueue({
    queueId: {},
    data: [],
    status: 0
  })




--------------------------------------------------------------------------------

saveQueue
================================================================================

.. code-block:: typescript

  queueService.saveQueue(arguments);

Save the current queue to the queue db storage.

-------
Example
-------

.. code-block:: typescript

  queueService.saveQueue();





--------------------------------------------------------------------------------

.. _document_getQueueEntry:

getQueueEntry
================================================================================

.. code-block:: typescript

  queueService.getQueueEntry(id, fillEmpty);

Get an specifc queue entry for the given queue id.

----------
Parameters
----------

#. ``id`` - |source QueueId|_: QueueId to get
#. ``fillEmpty`` - ``boolean``: creates an empty queue entry

-------
Returns
-------

|source QueueEntry|_: The queue entry.

.. code-block:: typescript

  {
    queueId: {},
    data: [],
    status: 0
  }

-------
Example
-------

.. code-block:: typescript

  queueService.getQueueEntry(taskboard.evan);




--------------------------------------------------------------------------------

.. _document_addQueueData:

addQueueData
================================================================================

.. code-block:: typescript

  queueService.addQueueData(id, data, idProperties);

Add new Queue entry to the queue.

----------
Parameters
----------

#. ``id`` - |source QueueId|_: Queue id where the data should be added.
#. ``data`` - ``any``: Data that should be added.
#. ``idProperties`` - ``Array<string>``: identity properties that should match, to remove / add queue updates

-------
Example
-------

.. code-block:: typescript

  this.queue.addQueueData(queueId, {
    id: '0x000',
    name: '0x000',
  });




--------------------------------------------------------------------------------

removeQueueData
================================================================================

.. code-block:: typescript

  queueService.removeQueueData(id, data);

Remove data entry from queue id.

----------
Parameters
----------

#. ``id`` - ``QueueId``: Queue id where the data should be added.
#. ``data`` - ``any``: Data that should be removed. (data is checked using data instance reference from addQueueData)

-------
Example
-------

.. code-block:: typescript
  
  this.queue.removeQueueData(queueId, {
    id: '0x000',
    name: '0x000',
  });




--------------------------------------------------------------------------------

removeQueueEntry
================================================================================

.. code-block:: typescript

  queueService.removeQueueEntry(id);

Remove queue entry with queue id

----------
Parameters
----------

#. ``id`` - |source QueueId|_: Queue id where the data should be added.

-------
Example
-------

.. code-block:: typescript

  queueService.removeQueueEntry(queueId)




--------------------------------------------------------------------------------

getDispatcherService
================================================================================

.. code-block:: typescript

  queueService.getDispatcherService(queueEntry);

Gets the dispatcher service for an queueEntry, that is specified within the |source QueueId|_.

----------
Parameters
----------

#. ``queueEntry`` - |source QueueEntry|_: queue entry to load the dispatcher service fore

-------
Returns
-------

``Promise`` returns ``any``: service instance

-------
Example
-------

.. code-block:: typescript

  queueService.getDispatcherService(queueEntry);




--------------------------------------------------------------------------------

.. _document_startSync:

startSync
================================================================================

.. code-block:: typescript

  queueService.startSync(queueEntry);

Starts syncing an queue entry. It's running the dispatchers run function.

----------
Parameters
----------

#. ``queueEntry`` - |source QueueEntry|_: The queue entry to start the synchronisation for.

-------
Returns
-------

``Promise`` returns ``void``: resolved when done

-------
Example
-------

.. code-block:: typescript

  queueService.startSync(queueEntry);




--------------------------------------------------------------------------------

startSyncAll
================================================================================

.. code-block:: typescript

  queueService.startSyncAll(disableErrors);

Start synchronisation of the whole queue.

----------
Parameters
----------

#. ``disableErrors`` - ``boolean`` (optional): dont run dispatchers with exceptions

-------
Example
-------

.. code-block:: typescript

  queueService.startSyncAll();




--------------------------------------------------------------------------------

enableSyncAll
================================================================================

.. code-block:: typescript

  initializedModule.enableSyncAll(arguments);

Check if sync all can be triggered (when not all queue entries are running)

-------
Returns
-------

``boolean``: true if all can be started (when no queueEntry is working)

-------
Example
-------

.. code-block:: typescript

  queueService.enableSyncAll();




--------------------------------------------------------------------------------

calculatePercentage
================================================================================

.. code-block:: typescript

  queueService.calculatePercentage(queueEntry);

Returns the current working percentage.

----------
Parameters
----------

#. ``queueEntry`` - |source QueueEntry|_: The queue entry to start the synchronisation for.

-------
Returns
-------

``number``: The percentage of the queue dispatcher (if 2 of 5 sequences was solved, it returns 20)

-------
Example
-------

.. code-block:: typescript

  queueService.calculatePercentage(queueEntry);




--------------------------------------------------------------------------------

setQueueStatus
================================================================================

.. code-block:: typescript

  initializedModule.setQueueStatus(disableEvent);

Check all queue stati (loading, exception, allSyncing) and send, that the queue stati have changed

----------
Parameters
----------

#. ``disableEvent`` - ``boolean``: dont trigger evan-queue-update


-------
Example
-------

.. code-block:: typescript

  queueService.setQueueStatus();


  
  
--------------------------------------------------------------------------------

isLoading
================================================================================

.. code-block:: typescript

  queueService.isLoading();

Check if one queue entry is loading.

-------
Returns
-------

``boolean``: True if loading, False otherwise.

-------
Example
-------

.. code-block:: typescript

  queueService.isLoading();

--------------------------------------------------------------------------------

isException
================================================================================

.. code-block:: typescript

  queueService.isException();

Check if an exception is represented within the queue.

-------
Returns
-------

``boolean``: True if exception, False otherwise.

-------
Example
-------

.. code-block:: typescript

  queueService.isException();




--------------------------------------------------------------------------------

.. _document_onQueueFinish:

onQueueFinish
================================================================================

.. code-block:: typescript

  queueService.onQueueFinish(queueId, run);

Adds an "event handle" to refresh data on queue entry finish.

----------
Parameters
----------

#. ``queueId`` - ``QueueId``: Queue ID to check for updates
#. ``run`` - ``Function``: Function to call on first binding and when queue entry with the queue id has finished

-------
Example
-------
Reference Implementation: `Task DApp <https://github.com/evannetwork/core-dapps/blob/master/dapps/task/src/components/detail/detail.ts>`_

.. code-block:: typescript

  this.clearStateQueue = await this.queueService.onQueueFinish(
    this.taskService.getStateQueueId(this.taskId),
    async (queueFinish) => {
      if (queueFinish) {
        this.task.contractState = await this.taskService.getContractState(this.task.address);

        this.task.states = await this.taskService.loadTaskStates(this.task);
      }

      await this.onTodoQueueFinish(queueFinish);
    }
  );

.. |source QueueId| replace:: ``QueueId``
.. _source QueueId: /angular-core/services/bcc/queue-utilities.html#queueid

.. |source QueueEntry| replace:: ``QueueEntry``
.. _source QueueEntry: /angular-core/services/bcc/queue.html#getqueueentry
