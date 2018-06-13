======
System
======

The dapp-browser uses |source SystemJS|_ load js bundles (UMD), json and css files from IPFS. You can use SystemJS directly. It is exposed as "System" property by the dapp-browser.

Using the `DApp loader </dapp-browser/dapp.html#loaddappdependencies>`_, each within the DBCP defined dependency of an DApp gets registered within SystemJS. So you can use the normal import statements within your DApp. Each library will be loaded before your app is running and inserted into your module.

.. code-block:: json

  {
    "public": {
      "dapp": {
        "dependencies": {
          "angular-core": "1.0.0"
        }
      }
    }
  }

.. code-block:: typescript

  import {
    AngularCoreModule
  } from 'angular-core';

This is handled by the dapp-browser SystemJS plugin "dapp-content". When importing the angular-core, the following will mechanism will be started:

- SystemJS plugin dapp-content will be triggered
- angular-core module name will be changed to match a valid ens address and enchanced with the current configured ens domain
  => `angularcore.${ getDomainName()` (e.g. angularcore.evan)
- DBCP configuration will be loaded from this
- each dependency will be loaded with the same mechanism as the current sample
- each css file will be injected into the dom
- the index file will be loaded and exposed to be able to import module exports


.. _db_system_dapp_content:

SystemJS Plugin: dapp-content 
================================================================================

.. code-block:: typescript

  System.import('angular-core!dapp-content')

The dapp-content plugin is used to load evan.network DApps within SystemJS. It loads the DBCP description, requires the dependencies, injects the CSS into the page and returns the main entry point as object.


--------------------------------------------------------------------------------

.. _db_system_ens:

SystemJS Plugin: ens
================================================================================

.. code-block:: typescript

  System.import('angular-core!ens')

The ens plugin loads a DBCP json description from an ens address and returns the json, where the public an the private part are merged and returned.

--------------------------------------------------------------------------------

.. _db_system_ipfs:

SystemJS Plugin: ipfs
================================================================================

.. code-block:: typescript

  System.import('Qmb...!ipfs')

The ipfs plugin uses restipfs to load data from ipfs over SystemJS.

--------------------------------------------------------------------------------

.. _db_system_json:

SystemJS Plugin: json
================================================================================

.. code-block:: typescript

  System.import('http://...!json')

The json plugin loads data from anywhere and tries to serializes the result as an object.

--------------------------------------------------------------------------------

.. _db_system_text:

SystemJS Plugin: text
================================================================================

.. code-block:: typescript

  System.import('http://...!text')

The text plugin loads data from anywhere and returns simply the result. (e.g. used to load css from a file)

--------------------------------------------------------------------------------


.. |source SystemJS| replace:: ``SystemJS``
.. _source SystemJS: https://github.com/systemjs/systemjs

.. |source loadDApp| replace:: ``dapp.loadDApp``
.. _source loadDApp: /dapp-browser/dapp.html#loaddappdependencies

.. |source restipfs| replace:: ``restipfs``
.. _source restipfs: /dapp-browser/ipfs.html#ipfscatpromise