=====
utils
=====

.. list-table:: 
   :widths: auto
   :stub-columns: 1

   * - Source
     - `utils <https://github.com/evannetwork/ui-dapp-browser/blob/develop/src/app/utils.ts>`__

The `utils <https://github.com/evannetwork/ui-dapp-browser/blob/develop/src/app/utils.ts>`_ includes several support functions.

One primary function is to check for dapps that should be loaded from the local development file server. This is enabled when opening the dev.html, instead of the index.html.


--------------------------------------------------------------------------------

.. _db_utils_devMode:

devMode
================================================================================

.. code-block:: typescript

  devMode

global available array that includes dev mode available dapps, when devMode is enabled, else undefined

--------------------------------------------------------------------------------

.. _db_utils_browserName:

browserName
================================================================================

.. code-block:: typescript

  browserName

Active browsers name. (Only set, after getBrowserName was runned before)

--------------------------------------------------------------------------------

.. _db_utils_isPrivateMode:

isPrivateMode
================================================================================

.. code-block:: typescript

  isPrivateMode

Is the current browser is running in private mode? (Only set, after getIsPrivateMode was runned before)

--------------------------------------------------------------------------------
 
.. _db_utils_setUpDevMode:
 
setUpDevMode
================================================================================

.. code-block:: typescript

 utils.setUpDevMode();

Checks if we are running in devMode, if true, load dev-dapps from local file server, if false do nothing
 



--------------------------------------------------------------------------------

.. _db_utils_isDevAvailable:

isDevAvailable
================================================================================

.. code-block:: typescript

  utils.isDevAvailable(name);

Check if a dev application is available

----------
Parameters
----------

#. ``name`` - ``string``: string of the dapp to check

-------
Returns
-------

``boolean``: True if DApp is available for development, False otherwise.

-------
Example
-------

.. code-block:: typescript

  utils.isDevAvailable(ensDefinition.name)




--------------------------------------------------------------------------------

.. _db_utils_sendEvent:

sendEvent
================================================================================

.. code-block:: typescript

  utils.sendEvent(name, data);

Sends an event using window.dispatchEvent

----------
Parameters
----------

#. ``name`` - ``string``: event name
#. ``data`` - ``any`` (optional): data that should be send

-------
Example
-------

.. code-block:: typescript

  utils.sendEvent('my-cool-event', { anyData: 1234 });




--------------------------------------------------------------------------------

.. _db_utils_events:

events
================================================================================

Predefined events for frontend usage

--------------
loadingSubDApp
--------------

.. code-block:: typescript

  events.loadingSubDApp

sends the event, that a sub DApp starts loading


--------------------
finishLoadingSubDApp
--------------------

.. code-block:: typescript

  events.loadingSubDApp

Sends the event, that a sub DApp finished loading




--------------------------------------------------------------------------------

.. _db_utils_showError:

showError
================================================================================

.. code-block:: typescript

  utils.showError();

Show Error during the initial loading, when no UI framework is loaded




--------------------------------------------------------------------------------

.. _db_utils_setProgress:

setProgress
================================================================================

.. code-block:: typescript

  utils.setProgress(percentage);

Sets the current loading progress (animates evan.network logo)

----------
Parameters
----------

#. ``percentage`` - ``number``: current loading percentage


-------
Example
-------

.. code-block:: typescript

  utils.setProgress(70)




--------------------------------------------------------------------------------

.. _db_utils_raiseProgress:

raiseProgress
================================================================================

.. code-block:: typescript

  utils.raiseProgress(percentage, returnObj);

Takes the latest progress percentage and raise it with the incoming value.

----------
Parameters
----------

#. ``percentage`` - ``number``: percentage to add
#. ``returnObj`` - ``any`` (optional): additional return object for raising loading progress and returning object instantly

-------
Returns
-------

``Promise`` returns ``any``: additional returnObject

-------
Example
-------

.. code-block:: typescript

  Promise
    .all<any, any>([
      System
        .import('bcc')
        .then(CoreBundle => utils.raiseProgress(10, CoreBundle)),
      System
        .import('smart-contracts')
        .then(SmartContracts => utils.raiseProgress(10, SmartContracts))
    ])




--------------------------------------------------------------------------------

.. _db_utils_devLog:

devLog
================================================================================

.. code-block:: typescript

  utils.devLog(message, level);

Log a message according to localStorage settings to the log

----------
Parameters
----------

#. ``message`` - ``string``: message to log
#. ``level`` - ``string`` (optional): level to log (log / verbose)


-------
Example
-------

.. code-block:: typescript

  utils.devLog(`Loading dapp: ${ dappEns }`, 'trace');


--------------------------------------------------------------------------------

.. _db_utils_onDeviceReady:

onDeviceReady
================================================================================

.. code-block:: typescript

  utils.devLogonDeviceReady();

Adds an deviceready event handler and wait for the result to resolve the promise. If we are on a
desktop device, dont wait for deviceready, it will be never called.

-------
Returns
-------

``Promise`` returns ``void``: resolved when decive is ready

-------
Example
-------

.. code-block:: typescript

  await utils.onDeviceReady();
  console.log('device is ready :)');

--------------------------------------------------------------------------------

.. _db_utils_getDAppName:

getDAppName
================================================================================

.. code-block:: typescript

  utils.getDAppName();

Removes the text after the last dot.

----------
Parameters
----------

#. ``ensAddress`` - ``string``: ens address to get the name for

-------
Returns
-------

``string``: dappname including sub ens paths

-------
Example
-------

.. code-block:: typescript

  const dappName = utils.getDAppName('mydapp.mycompany.evan');
  console.log(dappName) // => mydapp.mycompany

--------------------------------------------------------------------------------

.. _db_utils_getBrowserName:

getBrowserName
================================================================================

.. code-block:: typescript

  utils.getBrowserName();

Return the name of the current browser 

-------
Returns
-------

``string``: (Opera, Firefox, Safari, Chrome, IE, Edge, Blink, Cordova)

--------------------------------------------------------------------------------

.. _db_utils_getIsPrivateMode:

getIsPrivateMode
================================================================================

.. code-block:: typescript

  utils.getIsPrivateMode();

Lightweight script to detect whether the browser is running in Private mode.

-------
Returns
-------

``boolean``: true if running in private mode, else false