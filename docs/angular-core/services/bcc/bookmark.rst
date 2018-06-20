===================
EvanBookmarkService
===================

Blockchain-core wrapper service to handle users favorites.

- ``joinLeaveBcQueueId`` - |source queueId|_: queue id for handling favorite saving




--------------------------------------------------------------------------------

.. _document_queueAddBookmark:

queueAddBookmark
================================================================================

.. code-block:: typescript

  bookmarkService.queueAddBookmark(ensAddress);

Queue a new bookmark add process.

----------
Parameters
----------

#. ``ensAddress`` - ``string``: ens address that should be added
#. ``dapp`` - ``any``: dapp ens description

-------
Example
-------

.. code-block:: typescript

  const dapp = await this.bookmarkService.getBookmarkDefinition(ensAddress)
  await this
    .alertService.showSubmitAlert(
      '_dappdapps.alert.validTitle',
      {
        key: '_dappdapps.alert.dappMessage',
        translateOptions: dapp
      },
      'cancel',
      'submit'
    );
  this.bookmarkService.queueAddBookmark(ensAddress, dapp))




--------------------------------------------------------------------------------

.. _document_queueRemoveBookmark:

queueRemoveBookmark
================================================================================

.. code-block:: typescript

  bookmarkService.queueRemoveBookmark(ensAddress);

Function description

----------
Parameters
----------

#. ``ensAddress`` - ``string``: ens address that should be removed

-------
Returns
-------

``Promise`` returns ``void``: resolved when done

-------
Example
-------

.. code-block:: typescript

  this.bookmarkService.queueRemoveBookmark('taskboard.evan')





--------------------------------------------------------------------------------

.. _document_addDAppBookmark:

addDAppBookmark
================================================================================

.. code-block:: typescript

  bookmarkService.addDAppBookmark(ensAddress, dapp);

Add DApp bookmark to the current profile directly without queue.

----------
Parameters
----------

#. ``ensAddress`` - ``string``: ens address that should be added
#. ``dapp`` - ``any``: dapp ens description

-------
Returns
-------

``Promise`` returns ``void``: resolved when done

-------
Example
-------

.. code-block:: typescript

  Have a look at this.queueAddBookmark






--------------------------------------------------------------------------------

.. _document_removeDappBookmark:

removeDappBookmark
================================================================================

.. code-block:: typescript

  bookmarkService.removeDappBookmark(ensAddress);

Remove bookmark from current account.

----------
Parameters
----------

#. ``ensAddress`` - ``string``: ens address that should be removed

-------
Returns
-------

``Promise`` returns ``void``: resolved when done

-------
Example
-------

.. code-block:: typescript

  this.bookmarkService.removeDappBookmark('taskboard.evan')




--------------------------------------------------------------------------------

.. _document_syncQueueBookmarks:

syncQueueBookmarks
================================================================================

.. code-block:: typescript

  bookmarkService.syncQueueBookmarks(reload);

Overwrite current bookmarks to the profile and write them to the blockchain.

-------
Returns
-------

``Promise`` returns ``void``: resolved when done

-------
Example
-------

.. code-block:: typescript

  await bookmarkService.syncQueueBookmarks();




--------------------------------------------------------------------------------

.. _document_getDAppBookmarks:

getDAppBookmarks
================================================================================

.. code-block:: typescript

  bookmarkService.getDAppBookmarks(reload);

Reload profile data and return current bookmarked dapps.

----------
Parameters
----------

#. ``reload`` - ``boolean`` (optional): Force reload of current profile and so reload the bookmarks.

-------
Returns
-------

``Promise`` returns ``Array<any>``: bookmarks for the current user

-------
Example
-------

.. code-block:: typescript

  const bookmarks = getDAppBookmarks();

  [
    {
      ...
      "taskboard.evan": {
        "name": "taskboard",
        "description": "Create todos and manage updates.",
        "i18n": {
          "description": {
            "de": "Erstelle Aufgaben und überwache Änderungen",
            "en": "Create todos and manage updates"
          },
          "name": {
            "de": "Task Board",
            "en": "Task Board"
          }
        },
        "imgSquare": "...",
        "standalone": true,
        "primaryColor": "#e87e23",
        "secondaryColor": "#fffaf5",
        "translated": {
          "description": "Create todos and manage updates",
          "name": "Task Board"
        }
      }
    }
  ]




--------------------------------------------------------------------------------

clearBookmarks
================================================================================

.. code-block:: typescript

  bookmarkService.clearBookmarks();

Clear bookmarks of current profile.

-------
Returns
-------

``Promise`` returns ``void``: resolved when done

-------
Example
-------

.. code-block:: typescript

  await bookmarkService.clearBookmarks();

--------------------------------------------------------------------------------

.. _document_setAlreadyAddedToBookmark:

setAlreadyAddedToBookmark
================================================================================

.. code-block:: typescript

  bookmarkService.setAlreadyAddedToBookmark(bookmark);

Checks if the bookmark is already added the current profile bookmarks.

----------
Parameters
----------

#. ``bookmark`` - ``any``: Bookmark ENS definition

-------
Returns
-------

``Promise`` returns ``void``: resolved when done

-------
Example
-------

.. code-block:: typescript

  const definition = await this.descriptionService.getDescription(ensAddress);

  await this.setAlreadyAddedToBookmark(definition);

  return definition;




--------------------------------------------------------------------------------

.. _document_getBookmarkFromDefinition:

getBookmarkFromDefinition
================================================================================

.. code-block:: typescript

  bookmarkService.getBookmarkFromDefinition(definition);

Transform ENS definition to bookmark definition.

----------
Parameters
----------

#. ``definition`` - ``object``: ENS definition to parse

-------
Returns
-------

``Promise`` returns ``any``: The bookmark from definition.

.. code-block:: typescript
  {
    name: definition.name,
    description: definition.description,
    i18n: definition.i18n,
    imgSquare: definition.imgSquare,
    imgWide: definition.imgWide,
    standalone: definition.standalone || definition.dapp.standalone,
    primaryColor: definition.primaryColor || definition.dapp.primaryColor,
    secondaryColor: definition.secondaryColor || definition.dapp.secondaryColor
  }

-------
Example
-------

.. code-block:: typescript

  getBookmarkFromDefinition({ name: '', ... })




--------------------------------------------------------------------------------

.. _document_getBookmarkDefinition:

getBookmarkDefinition
================================================================================

.. code-block:: typescript

  bookmarkService.getBookmarkDefinition(ensAddress);

Loads an definition and checks the "already_added" state.

----------
Parameters
----------

#. ``ensAddress`` - ``string``: ENS addres to load the definition from

-------
Returns
-------
have a look at getBookmarkFromDefinition

``Promise`` returns ``void``: The bookmark definition.

-------
Example
-------

.. code-block:: typescript

  await bookmarkService.getBookmarkDefinition('taskboard.evan')




--------------------------------------------------------------------------------

.. _document_getBookmarkDefinitions:

getBookmarkDefinitions
================================================================================

.. code-block:: typescript

  bookmarkService.getBookmarkDefinitions(ensAddresses);

Loads multiple definitions and checks the "already_added" state.

----------
Parameters
----------

#. ``ensAddresses`` - ``Array<string``: ENS addresses to load the definition from

-------
Returns
-------

``Promise`` returns ``Array<any>``: The bookmark definitions.

-------
Example
-------

.. code-block:: typescript

  await bookmarkService.getBookmarkDefinitions([
    'favorites'
    'mailbox',
    'contacts'
  ])















.. |source queueId| replace:: ``QueueId``
.. _source queueId: /angular-core/services/bcc/queue-utilities.html#queueid