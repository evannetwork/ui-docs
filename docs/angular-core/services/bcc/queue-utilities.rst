===============
Queue Utilities
===============

--------------------------------------------------------------------------------

QueueId
================================================================================

.. code-block:: typescript

  new QueueId(ensAddress, dispatcher, id, forceReload);

Generates an queue ID by concadinating an ensAddress and a dispatcher name

----------
Parameters
----------

#. ``ensAddress`` - ``string``: ens address were the dispatcher lives;
#. ``dispatcher`` - ``string``: name of the exported function on the ens expose object;
#. ``id`` - ``string``: specification to start the same queue in seperated instances;
#. ``forceReload`` - ``boolean``: use force reload to disable alert when current opened ens address is the same as the currently finished dispatcher;

-------
Example
-------
Reference Implementation: `EvanBookmarkService <https://github.com/evannetwork/angular-core/blob/develop/src/services/bcc/bookmark.ts>`_

.. code-block:: typescript

  this.queueId = new QueueId(
    this.description.getEvanENSAddress('addressbook'),
    'ContactsDispatcher',
    'contacts'
  );





--------------------------------------------------------------------------------

QueueSequence
================================================================================

.. code-block:: typescript

  new QueueSequence(name, description, run);

Used to handle one step of an dispatcher

----------
Parameters
----------

#. ``name`` - ``string``: Display name for queue (used for |source QueueDApp|_)
#. ``description`` - ``string``: Description for the queue (used for |source QueueDApp|_)
#. ``run`` - ``Function``: the function that is called to run the queue (gets the within the QueueDispatcher configured service and the data that should be handled (Array<any>: one entry for each new added QueueEntry))

-------
Returns
-------

``Promise`` returns ``void``: resolved when done

-------
Example
-------

.. code-block:: typescript

  new QueueSequence(
    '_dappdapps.dispatcher.save-bookmarks',
    '_dappdapps.dispatcher.save-bookmarks-description',
    async (service: BookmarkDispatcherService, data: any) => {
      await service.bookmarkService.syncQueueBookmarks();
    }
  )

.. |source QueueDApp| replace:: ``QueueDApp``
.. _source QueueDApp: https://dashboard.evan.network/#/dashboard.evan/queue.evan




--------------------------------------------------------------------------------

QueueDispatcher
================================================================================

.. code-block:: typescript

  new QueueDispatcher(sequence, i18n, serviceName);

Represents one dispatcher using several queueSequences, that will processed one after another, using step caches

----------
Parameters
----------

#. ``sequence`` - ``Array<QueueSequence>``: All sequences that should be runned after another
#. ``i18n`` - ``any``: i18n definitions for the queue
#. ``serviceName`` - ``string``: name of the servide that should be applied to the sequence entry

-------
Example
-------

.. code-block:: typescript

  export const BookmarkDispatcher = new QueueDispatcher(
    [
      sequences...
    ],
    translations
  );