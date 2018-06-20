===============
EvanCoreService
===============

Core service for angular-core that handles dapp-browser connections, active accounts, current provider and more.

--------------------------------------------------------------------------------

getCurrentProvider
================================================================================

.. code-block:: typescript

  coreService.getCurrentProvider();

Get the current configured current provider

----------
Parameters
----------

#. ``options`` - ``object``: The options used for calling
    * ``from`` - ``string`` (optional): The address the call "transaction" should be made from
#. ``callback`` - ``Function`` (optional): This callback will be fired..
#. ``somethingElse`` - ``string`` (optional): this can be set if required, defaults to ``"latest"``

-------
Returns
-------

``string``: The current provider. (internal / external)

-------
Example
-------

.. code-block:: typescript

  coreService.getCurrentProvider();

--------------------------------------------------------------------------------

.. _document_finishDAppLoading:

finishDAppLoading
================================================================================

.. code-block:: typescript

  coreService.finishDAppLoading();

Hides the `initial loading </dapp-browser/loading.html#finishdapploading>`_ that is embedded to the root dapp html page. => It will disappear smooth and will be removed when animation is over

-------
Example
-------

.. code-block:: typescript

  coreService.finishDAppLoading();


--------------------------------------------------------------------------------

isInternalProvider
================================================================================

.. code-block:: typescript

  coreService.isInternalProvider();

Check if we should use internal provider.

-------
Returns
-------

``boolean``: True if internal provider, False otherwise.




--------------------------------------------------------------------------------

getExternalProvider
================================================================================

.. code-block:: typescript

  core.getExternalProvider();

Checks if a injected web3 provider exists an returns it's name

-------
Returns
-------

``boolean``: check if the current provider is external

-------
Example
-------

.. code-block:: typescript

  getExternalProvider()
  // false




--------------------------------------------------------------------------------

.. _document_setCurrentProvider:

setCurrentProvider
================================================================================

.. code-block:: typescript

  coreService.setCurrentProvider(provider);

Sets the current provider that should be used.

----------
Parameters
----------

#. ``provider`` - ``string``: provider to switch to

-------
Example
-------

.. code-block:: typescript

  coreService.setCurrentProvider('internal')




--------------------------------------------------------------------------------

.. _document_activeAccount:

activeAccount
================================================================================

.. code-block:: typescript

  coreService.activeAccount();

Get the current selected account included the check of the current provider.

-------
Returns
-------

``string``: active account

-------
Example
-------

.. code-block:: typescript

  coreService.activeAccount();




--------------------------------------------------------------------------------

.. _document_getAccountId:

getAccountId
================================================================================

.. code-block:: typescript

  coreService.getAccountId();

Returns the current saved account id from localStorage

-------
Returns
-------

``string``: get account id from local storage

-------
Example
-------

.. code-block:: typescript

  coreService.getAccountId();





--------------------------------------------------------------------------------

.. _document_setAccountId:

setAccountId
================================================================================

.. code-block:: typescript

  coreService.setAccountId(accountId);

Sets an account id as active one to the local storage.

----------
Parameters
----------

#. ``accountId`` - ``string``: account id to set


Example
-------

.. code-block:: typescript

  coreService.setAccountId('0x00');


--------------------------------------------------------------------------------

getExternalAccount
================================================================================

.. code-block:: typescript

  coreService.getExternalAccount();

Checks if an external provider is activated and returns it's active account id

-------
Returns
-------

``string``: The external account.

-------
Example
-------

.. code-block:: typescript

  coreService.getExternalAccount()
  // '0x000...'

--------------------------------------------------------------------------------

currentBrowser
================================================================================

.. code-block:: typescript

  coreService.currentBrowser();

Return the name of the current used browser =>
https://stackoverflow.com/questions/9847580/how-to-detect-safari-chrome-ie-firefox-and-opera-browser

-------
Returns
-------

``string`` : opera / firefox / safari / ie / edge / chrome

-------
Example
-------

.. code-block:: typescript

  coreService.currentBrowser();
  // 'chrome'

--------------------------------------------------------------------------------

getBalance
================================================================================

.. code-block:: typescript

  coreService.getBalance(accountId);

Gets the balance of the provided or current account id

----------
Parameters
----------

#. ``accountId`` - ``string``: account id to get the balance from (default coreService.activeAccount())

-------
Returns
-------

``number`` : The balance for the specific account id

-------
Example
-------

.. code-block:: typescript
  
  coreService.getBalance('0x000');
  // 6.0223

--------------------------------------------------------------------------------

logout
================================================================================

.. code-block:: typescript

  coreService.logout(disabledReload);

Logout the current user. Removes the active account, provider and terms of use acceptance.

----------
Parameters
----------

#. ``disabledReload`` - ``boolean``: The options used for calling

-------
Example
-------

.. code-block:: typescript

  coreService.logout();




--------------------------------------------------------------------------------

copyString
================================================================================

.. code-block:: typescript

  coreService.copyString(arguments);

Copes a string into the users clipboard and shows an toast, including the copied text

----------
Parameters
----------

#. ``stringToCopy`` - ``string``: text that should be copied

-------
Example
-------

.. code-block:: typescript

  coreService.copyString('Copy me :)');