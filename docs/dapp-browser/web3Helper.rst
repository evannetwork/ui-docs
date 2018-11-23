==========
web3Helper
==========

.. list-table:: 
   :widths: auto
   :stub-columns: 1

   * - Source
     - `web3 helper <https://github.com/evannetwork/ui-dapp-browser/blob/develop/src/app/web3.ts>`__

The `web3 helper <https://github.com/evannetwork/ui-dapp-browser/blob/develop/src/app/web3.ts>`_ is a wrapper library to get a new Web3 Constructor with overwritten functions. By default, web3 cannot handle websocket disconnects and the UI will break after 5 minutes, when its not used. To handle this, the web3 helper overwrites the "WebsocketProvider.prototype.send" function.


--------------------------------------------------------------------------------

.. _ds_web3helper_getWeb3Constructor:

getWeb3Constructor
================================================================================

.. code-block:: typescript

  web3Helper.getWeb3Constructor();

Returns the Web3 Constructor from blockchain-core and overwrites the send function

-------
Returns
-------

``Promise`` returns ``void``: resolved when done

-------
Example
-------

.. code-block:: typescript

  The web 3 constructor.




--------------------------------------------------------------------------------

.. _db_web3helper_getWeb3Instance:

getWeb3Instance
================================================================================

.. code-block:: typescript

  web3Helper.getWeb3Instance(url);

Returns a new web3 instances. If a web3 currentProvider is provided, it will be used.

----------
Parameters
----------

#. ``url`` - ``string``: url for the web socket connection

-------
Returns
-------

``any``: web3 instance

-------
Example
-------

.. code-block:: typescript

  import { config } from '../config';
  web3 = getWeb3Instance(config.web3Provider);

