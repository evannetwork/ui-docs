==================
DispatcherInstance
==================

.. list-table:: 
   :widths: auto
   :stub-columns: 1

   * - Source
     - `Dispatcher <https://github.com/evannetwork/ui-core/tree/master/dapps/ui.libs/src/Dispatcher.ts>`__

A ``DispatcherInstance`` is generated, when a Dispatcher was started. This instance runs the startup
and step functions and holds the data. Also it contains several status flags, which step is
currently running and it saves it's states and data into the queue.

  #. ``queue`` - ``EvanQueue``: Queue for the current runtime and dispatcher
  #. ``dispatcher`` - ``Dispatcher``: Dispatcher that should be runned.
  #. ``runtime`` - ``Runtime``: A initialized bcc runtime.
  #. ``data`` - ``any``: Data that should be passed to the steps
  #. ``stepIndex`` - ``number``: Active step.
  #. ``id`` - ``any``: dispatcher runtime id
  #. ``_status`` - ``string``: Current running status
  #. ``error`` - ``any``: Error message.
  #. ``evePrice`` - ``number``:  If the instance must be accepted, the eve price will be estimated and saved to this instance.
  #. ``customEvePrice`` - ``number``: Custom applied eve price that will overwrite the dispatcher one
  #. ``status`` - ``string``: returns _this.status

--------------------------------------------------------------------------------

.. _DispatcherInstance_constructor:

constructor
================================================================================

.. code-block:: typescript

  new DispatcherInstance(options);

Creates a new DispatcherInstance instance.

----------
Parameters
----------

#. ``options`` - ``DispatcherInstanceOptions``: options for DispatcherInstance constructor.
    * ``queue`` - ``EvanQueue``: Queue for the current runtime and dispatcher
    * ``dispatcher`` - ``Dispatcher``: Dispatcher that should be runned.
    * ``runtime`` - ``bcc.Runtime``: A initialized bcc runtime.
    * ``data`` - ``any``: Data that should be passed to the steps
    * ``stepIndex`` - ``number``: Active step.
    * ``customPrice`` - ``number``: If the instance must be accepted, the eve price will be estimated and saved to this instance.
    * ``id`` - ``any``: dispatcher runtime id
    * ``error`` - ``any``: Error message.

-------
Returns
-------

``DispatcherInstance`` instance

-------
Example
-------

.. code-block:: typescript
  
  async start(runtime: bcc.Runtime, data: any, stepIndex = 0, price?: number) {
    const uiCoreQueue = await new EvanQueue(runtime.activeAccount);

    // map the original dispatcher instance to the current one => other dapps can create a
    // dispatcher instance pointing to the original ens and can watch and start the dispatcher
    // without implementing the original logic
    const originalDispatcher = (await System.import(`${ this.dappEns }!dapp-content`))[this.name];
    if (originalDispatcher) {
      Object.keys(originalDispatcher).forEach(key => this[key] = originalDispatcher[key]);
    }

    const instance = new DispatcherInstance({
      queue: uiCoreQueue,
      dispatcher: this,
      runtime,
      data: data,
      stepIndex: stepIndex,
    });

    // start the instance!
    await instance.start();

    return instance;
  }




--------------------------------------------------------------------------------

.. _dispatcherInstance_start:

start
================================================================================

.. code-block:: typescript

  dispatcherInstance.start(accept);

Run the startup and run functions. If the evePrice is higher than the eve-treshold (0.5), it will
send an event that this transaction must be accepted, before it can be started.

----------
Parameters
----------

#. ``accept`` - ``boolean``: should the dispatcher started directly?

-------
Returns
-------

``Promise`` returns ``void``: resolved when done

-------
Example
-------

.. code-block:: typescript

  await instance.start();




--------------------------------------------------------------------------------

.. _dispatcherInstance_startup:

startup
================================================================================

.. code-block:: typescript

  initializedModule.startup(arguments);

Run all the startup functions.

-------
Returns
-------

``Promise`` returns ``void``: resolved when done

-------
Example
-------

.. code-block:: typescript

  await instance.startup();




--------------------------------------------------------------------------------

.. _queueInstance_accept:

accept
================================================================================

.. code-block:: typescript

  queueInstance.accept(arguments);

Accept the dispatcher instance and start the synchronisation. Used to accept the eve-treshold

-------
Returns
-------

``Promise`` returns ``void``: used to accept the eve-treshold




--------------------------------------------------------------------------------

.. _queueInstance_run:

run
================================================================================

.. code-block:: typescript

  queueInstance.run();

Run the next step in the queue and persist the data.


-------
Returns
-------

``Promise`` returns ``void``: resolved when done

-------
Example
-------

.. code-block:: typescript

  queueInstance.run();




--------------------------------------------------------------------------------

.. _queueInstance_stop:

stop
================================================================================

.. code-block:: typescript

  queueInstance.stop();

Set the current status to 'stopping' and the dispatcher will stop, after it finished the current running step step.

-------
Example
-------

.. code-block:: typescript

  queueInstance.stop();




--------------------------------------------------------------------------------

.. _queueInstance_delete:

delete
================================================================================

.. code-block:: typescript

  queueInstance.delete();

Stops the current synchronisation and deletes the instance from the queue. If the dispatcherInstance
is running, deleting flag is set, so the queue will stop after finishing current step.

-------
Returns
-------

``Promise`` returns ``void``: resolved when deleted

-------
Example
-------

.. code-block:: typescript

  queueInstance.delete();




--------------------------------------------------------------------------------

.. _queueInstance_triggerWatchers:

triggerWatchers
================================================================================

.. code-block:: typescript

  queueInstance.triggerWatchers(status);

Sends all events, specific for this disaptcher, using the given status. Events that will be sent:

  - evan-queue-*-*
  - evan-queue-this.dispatcher.dappEns }-*
  - evan-queue-${ this.dispatcher.dappEns }-${ this.dispatcher.name }
  - evan-queue-${ this.id }

-------
Example
-------

.. code-block:: typescript

  queueInstance.triggerWatchers('running');




--------------------------------------------------------------------------------

.. _queueInstance_sendEvent:

sendEvent
================================================================================

.. code-block:: typescript

  queueInstance.sendEvent(eventName, status);

Send an event with an status for this instance. Will send the following parameters

#. ``detail`` - ``object``: payload that should be sent
  #. ``dispatcher`` - ``Dispatcher``: Dispatcher definition
  #. ``instance`` - ``DispatcherInstance``: running dispatcher instance
  #. ``status`` - ``status``: status

----------
Parameters
----------

#. ``eventName`` - ``string``: event name to trigger
#. ``status`` - ``string``: status that should be sent

-------
Example
-------

.. code-block:: typescript

  this.sendEvent(`evan-queue-*-*`, 'running');




--------------------------------------------------------------------------------

.. _queueInstance_save:

save
================================================================================

.. code-block:: typescript

  queueInstance.save();

Take the current data and saves it into the queue db.

-------
Returns
-------

``Promise`` returns ``void``: resolved when saved

-------
Example
-------

.. code-block:: typescript

  dispatcherInstance.save();




--------------------------------------------------------------------------------

.. _queueInstance_finish:

finish
================================================================================

.. code-block:: typescript

  queueInstance.finish();

Set the status to finished and remove the queue entry data.

-------
Returns
-------

``Promise`` returns ``void``: resolved when done

-------
Example
-------

.. code-block:: typescript

  queueInstance.finish();




--------------------------------------------------------------------------------

.. _queueInstance_watch:

watch
================================================================================

.. code-block:: typescript

  queueInstance.watch(func);

Watch for instance updates

----------
Parameters
----------

#. ``options`` - ``object``: The options used for calling

-------
Returns
-------

``Promise`` returns ``void``: resolved when done

-------
Example
-------

.. code-block:: typescript

  dispatchers.inviteDispatcher.watch(
    ($event) => this.loadContacts($event.detail.status === 'finished')
  );