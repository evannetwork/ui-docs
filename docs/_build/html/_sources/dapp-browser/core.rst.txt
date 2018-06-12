====
core
====
The `core <https://github.com/evannetwork/dapp-browser/blob/develop/src/app/core.ts>`_ is a function catalog to handle users accountId, login provider and users utility functions.

--------------------------------------------------------------------------------

.. _db_core_logout:

logout
================================================================================

.. code-block:: typescript

  core.logout(disabledReload);

Logout the current user. Removes the active account, provider and terms of use acceptance.

----------
Parameters
----------

#. ``disabledReload`` - ``boolean``: The options used for calling

-------
Example
-------

.. code-block:: typescript

  core.logout();




--------------------------------------------------------------------------------

.. _db_core_getCurrentProvider:

getCurrentProvider
================================================================================

.. code-block:: typescript

  core.getCurrentProvider();

Get the current, in local storage, configured provider.

-------
Returns
-------

``string``: The current provider (external, internal)

-------
Example
-------

.. code-block:: typescript

  core.getCurrentProvider()
  // 'internal'




--------------------------------------------------------------------------------

.. _db_core_isInternalProvider:

isInternalProvider
================================================================================

.. code-block:: typescript

  core.isInternalProvider();

Check if we should use internal provider.

-------
Returns
-------

``boolean``: Check if we should use internal provider.

-------
Example
-------

.. code-block:: typescript

  core.isInternalProvider()
  // true




--------------------------------------------------------------------------------

.. _db_core_getExternalProvider:

getExternalProvider
================================================================================

.. code-block:: typescript

  core.getExternalProvider();

Function description

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

.. _db_core_setCurrentProvider:

setCurrentProvider
================================================================================

.. code-block:: typescript

  core.setCurrentProvider(provider);

Sets the current provider that should be used.

----------
Parameters
----------

#. ``string``: provider to switch to

-------
Example
-------

.. code-block:: typescript

  core.setCurrentProvider('internal')




--------------------------------------------------------------------------------

.. _db_core_activeAccount:

activeAccount
================================================================================

.. code-block:: typescript

  core.activeAccount();

Get the current selected account included the check of the current provider.

-------
Returns
-------

``string``: account id of the current user (0x0...)

-------
Example
-------

.. code-block:: typescript

  const accountId = activeAccount();
  // '0x000....'




--------------------------------------------------------------------------------

.. _db_core_getAccountId:

getAccountId
================================================================================

.. code-block:: typescript

  core.getAccountId();

Returns the current (in the localStorage) saved account id

-------
Returns
-------

``string`` : account id of the user (0x0...)

-------
Example
-------

.. code-block:: typescript

  core.getAccountId()
  // '0x000...'




--------------------------------------------------------------------------------

.. _db_core_setAccountId:

setAccountId
================================================================================

.. code-block:: typescript

  core.setAccountId(accountId);

Sets an account id as active one to the local storage.

----------
Parameters
----------

#. ``accountId`` - ``string``: account id to set to the localStorage

-------
Example
-------

.. code-block:: typescript

  setAccountId('0x0...')




--------------------------------------------------------------------------------

.. _db_core_getExternalAccount:

getExternalAccount
================================================================================

.. code-block:: typescript

  core.getExternalAccount();

Checks if an external provider is activated and returns it's active account id

-------
Returns
-------

``string``: The external account.

-------
Example
-------

.. code-block:: typescript

  core.getExternalAccount()
  // '0x000...'




--------------------------------------------------------------------------------

.. _db_core_watchAccountChange:

watchAccountChange
================================================================================

.. code-block:: typescript

  core.watchAccountChange();

Watches for account changes and reload the page if nessecary

-------
Example
-------

.. code-block:: typescript

  core.watchAccountChange();




--------------------------------------------------------------------------------

.. _db_core_currentBrowser:

currentBrowser
================================================================================

.. code-block:: typescript

  core.currentBrowser();

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

  core.currentBrowser();
  // 'chrome'



--------------------------------------------------------------------------------

.. _db_core_getBalance:

getBalance
================================================================================

.. code-block:: typescript

  core.getBalance(accountId);

Gets the balance of the provided or current account id

----------
Parameters
----------

#. ``accountId`` - ``string``: account id to get the balance from (default core.activeAccount())

-------
Returns
-------

``number`` : The balance for the specific account id

-------
Example
-------

.. code-block:: typescript
  
  core.getBalance('0x000');
  // 6.0223