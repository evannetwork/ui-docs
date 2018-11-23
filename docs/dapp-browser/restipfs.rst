========
restipfs
========

.. list-table:: 
   :widths: auto
   :stub-columns: 1

   * - Source
     - `restipfs <https://github.com/evannetwork/ui-dapp-browser/blob/develop/src/libs/browser-ipfs.js>`__

The `restipfs <https://github.com/evannetwork/ui-dapp-browser/blob/develop/src/libs/browser-ipfs.js>`_ is a local copy of `browser ipfs <https://github.com/pelle/browser-ipfs>`_ including some small adjustments, to handle a lightweight rest based ipfs connection. It is used to initial files (before bcc and browserified ipfs-js loaded) and small DBCP descriptions. 




--------------------------------------------------------------------------------

.. _db_restipfs_setProvider:

setProvider
================================================================================

.. code-block:: typescript

  ipfs.setProvider(opts);

set localProvider configuration

----------
Parameters
----------

#. ``opts`` - ``object``: e.g. {host: 'localhost', port: '5001'}





--------------------------------------------------------------------------------

.. _db_restipfs_api_url:

api_url
================================================================================

.. code-block:: typescript

  ipfs.api_url(path);

build the api connection url

----------
Parameters
----------

#. ``path`` - ``string``: path to build the api url for

-------
Returns
-------

```string``: full api enchanced path

-------
Example
-------

.. code-block:: typescript

  restIpfs.api_url(`/ipfs/Qmb...`) => http://localhost:5001/api/v0/ipfs/Qmb




--------------------------------------------------------------------------------

.. _db_restipfs_add:

add
================================================================================

.. code-block:: typescript

  ipfs.add(input, callback);

Adds a file to the ipfs

----------
Parameters
----------

#. ``input`` - ``string``: string input of the file
#. ``callback`` - ``Function``: callback called when finished adding

-------
Example
-------

.. code-block:: typescript

  ipfs.add('hello world, wohooo', () => console.log('Finished'))




--------------------------------------------------------------------------------

.. _db_restipfs_catText:

catText
================================================================================

.. code-block:: typescript

  ipfs.catText(ipfsHash, callback);

Returns a string that is loaded from a ipfs hash

----------
Parameters
----------

#. ``ipfsHash`` - ``string``: ipfs hash to load
#. ``callback`` - ``Function``: callback called when finished loading

-------
Returns
-------

``string``: result of the ipfs hash

-------
Example
-------

.. code-block:: typescript

  ipfs.catText('Qmb...', (result) => console.log(result))  //==> hello world, wohooo




--------------------------------------------------------------------------------

.. _db_restipfs_addJson:

addJson
================================================================================

.. code-block:: typescript

  ipfs.addJson(jsonObject, callback);

Serializes a json object and saves it using ipfs.add

----------
Parameters
----------

#. ``jsonObject`` - ``object``: json object to save
#. ``callback`` - ``Function``: callback that is called when finished request

-------
Example
-------

.. code-block:: typescript

  ipfs.add({ text: "hello world, wohooo" }, () => console.log('Finished'))




--------------------------------------------------------------------------------

.. _db_restipfs_catJson:

catJson
================================================================================

.. code-block:: typescript

  ipfs.catJson(ipfsHash, callback);

Load data from an ipfs hash and tries an JSON.parse on the result

----------
Parameters
----------

#. ``ipfsHash`` - ``string``: ipfs hash to load
#. ``callback`` - ``Function``: callback called when finished loading

-------
Returns
-------

``object``: resolved when done

-------
Example
-------

.. code-block:: typescript

  ipfs.catJson('Qmb...', (result) => console.log(result)) // ==> { text: "hello world, wohooo" }

