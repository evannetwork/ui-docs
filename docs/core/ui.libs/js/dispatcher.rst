==========
Dispatcher
==========

.. list-table:: 
   :widths: auto
   :stub-columns: 1

   * - Source
     - `Dispatcher <https://github.com/evannetwork/ui-core/tree/master/dapps/ui.libs/src/Dispatcher.ts>`__

The Dispatcher handles batched data processing and saves the data within the EvanQueue. Within the
dispatcher, the several steps can be defined. From this, instances can be generated, that will
process the provided steps.

#. ``dappEns`` - ``string``: Original dapp ens address.
#. ``name`` - ``string``: Technical exported class member of the dispatcher within the dapp.
#. ``id`` - ``string``: Combination of dapp ens and the name
#. ``title`` - ``string``: I18N display key.
#. ``gas`` - ``number``: estimated gas price for one full steps run.
#. ``evePrice`` - ``number``: estimated eve price for one full steps run.
#. ``startupSteps`` - ``Array<Function>``: Steps that should be runned everytime at synchrnisation beginning
#. ``steps`` - ``Array<Function>``: List of step functions.
#. ``initialized`` - ``boolean``: Were the instances loaded before?
#. ``queues`` - ``object``: Queue instances mapped to account id's and running dispatcher instances.


--------------------------------------------------------------------------------

.. _Dispatcher_watch:

watch
================================================================================

.. code-block:: typescript

  Dispatcher.watch(func, dappEns, name);

Dynamic watch for dispatcher updates within a dapp. Per default, it watches for everything.
Optional, other dapp ens addresses or dispatcher names can be listened.

----------
Parameters
----------

#. ``func`` - ``Function<$event>``: callback function that should be called
#. ``dappEns`` - ``string`` (default = '*'): ens address that should be watched
#. ``name`` - ``string`` (default = '*'): dispatcher name that should be watched

-------
Returns
-------

``Function``: Function, that removes the listener, when it's called.

-------
Example
-------

.. code-block:: typescript

  this.dispatcherWatch = Dispatcher.watch(
    ($event) => this.loadContacts($event.detail.status === 'finished'),
    `addressbook.vue.${ (<any>this).dapp.domainName }`,
    '*'
  );

--------------------------------------------------------------------------------

.. _dispatcher_constructor:

constructor
================================================================================

.. code-block:: typescript

  new Dispatcher(dappEns, name, gas, title);

Creates a new Dispatcher instance.

----------
Parameters
----------

#. ``dappEns`` - ``string``: Original dapp ens address.
#. ``name`` - ``string``: Technical exported class member of the dispatcher within the dapp.
#. ``gas`` - ``number``: estimated gas price for one full steps run.
#. ``title`` - ``string``: I18N display key.

-------
Returns
-------

``Dispatcher`` instance

-------
Example
-------

.. code-block:: typescript
  
  const dispatcher = new Dispatcher(
    `addressbook.vue.${ dappBrowser.getDomainName() }`,
    'inviteDispatcher',
    40 * 1000,
    '_addressbook.dispatcher.invite'
  );

  dispatcher
    .step(async (instance: DispatcherInstance, data: any) => {
      ...
    });




--------------------------------------------------------------------------------

.. _dispatcher_startup:

startup
================================================================================

.. code-block:: typescript

  dispatcher.startup(stepFunc);

Add a step, that should be runned every time at the begging and ignore the state.

----------
Parameters
----------

#. ``stepFunc`` - ``Function``: Function that should be called.

-------
Returns
-------

``Dispatcher``: returns the dispatcher context

-------
Example
-------

.. code-block:: typescript

  dispatcher
    .startup(async (instance: DispatcherInstance, data: any) => {
      const runtime = utils.getRuntime(instance.runtime);
    })
    .step(async (instance: DispatcherInstance, data: any) => {
      const runtime = utils.getRuntime(instance.runtime);
    })




--------------------------------------------------------------------------------

.. _dispatcher_stepFunc:

stepFunc
================================================================================

.. code-block:: typescript

  dispatcher.stepFunc(stepFunc);

Adds a step into the step array

----------
Parameters
----------

#. ``stepFunc`` - ``Function``: Function that should be called.

-------
Returns
-------

``Dispatcher``: returns the dispatcher context

-------
Example
-------

.. code-block:: typescript

  dispatcher
    .startup(async (instance: DispatcherInstance, data: any) => {
      const runtime = utils.getRuntime(instance.runtime);
    })
    .step(async (instance: DispatcherInstance, data: any) => {
      const runtime = utils.getRuntime(instance.runtime);
    })




--------------------------------------------------------------------------------

.. _dispatcher_getInstances:

getInstances
================================================================================

.. code-block:: typescript

  dispatcher.getInstances(runtime, asArray);

Get the current running instances for this dispatcher from the queue.

----------
Parameters
----------

#. ``runtime`` - ``Runtime``: bcc runtime
#. ``asArray`` - ``boolean``: should be the result an array?

-------
Returns
-------

``Promise`` returns ``Array<any>|any``: Array of DispatcherInstances or object with dispatcher id as key and the instance as value

-------
Example
-------

.. code-block:: typescript

  const dispatcherInstances = (await Promise.all([
    dispatchers.inviteDispatcher.getInstances(runtime),
    dispatchers.updateDispatcher.getInstances(runtime),
    dispatchers.removeDispatcher.getInstances(runtime),
  ]));

  // iterate through all dispatcher instances and apply loading flag, and changed data
  dispatcherInstances.forEach((instances: Array<DispatcherInstance>, index: number) =>
    instances.forEach((instance: DispatcherInstance) => {
      const data = instance.data;
      contacts[data.accountId || data.email] = Object.assign(
        contacts[data.accountId || data.email] || { },
        {
          loading: true,
          remove: index === 2,
        },
        instance.data
      );
    })
  );




--------------------------------------------------------------------------------

.. _dispatcher_start:

start
================================================================================

.. code-block:: typescript

  dispatcher.start(runtime, data, stepIndex, price);

Starts this dispatcher with an specific runtime, an data object at an specific point.

----------
Parameters
----------

#. ``runtime`` - ``Runtime``: blockchain core runtime
#. ``data`` - ``any``: Any option that should passed into the steps
#. ``stepIndex`` - ``number`` (default = 0): step index to start at
#. ``price`` - ``number`` (optional): custom calculated price

-------
Returns
-------

``Promise`` returns ``DispatcherInstance``: the newly created dispatcer instance

-------
Example
-------

.. code-block:: typescript

  dispatchers.inviteDispatcher.start((<any>this).getRuntime(), formData);




--------------------------------------------------------------------------------

.. _dispatcher_watch:

watch
================================================================================

.. code-block:: typescript

  dispatcher.watch(func);

Watch for instance updates for this dispatcher. 

----------
Parameters
----------

#. ``func`` - ``Function<$event>``: callback function that should be called

-------
Returns
-------

``Function``: Function, that removes the listener, when it's called.

-------
Example
-------

.. code-block:: typescript

  dispatchers.inviteDispatcher.watch(
    ($event) => this.loadContacts($event.detail.status === 'finished')
  );