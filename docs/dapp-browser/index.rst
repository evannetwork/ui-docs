============
dapp-browser
============

The dapp-browser is used to start applications over it. Within this applications, several classes, functions and runtime instances can be used. General DApps will be opened like the following "https://.../index.html#/my-dapp-ens.evan". Where the index.html file is the entry point of the dapp-browser. Within the DApp the dapp-browser can be used like the following example:

- typescript file:

::

  import {
    config,
    getDomainName
  } from 'dapp-browser';

- tsconfig.json

::

  {
    "compilerOptions": {
      ...,
      "paths": {
        "dapp-browser": [
          "../node_modules/@evan.network/dapp-browser/runtime/build/main.js"
        ]
      }
      ...
    }
  }

**Be aware: The instances will only be exposed when the dapp-browser is started using the** `initializeEvanNetworkStructure </dapp-browser/functions.html#initializeevannetworkstructure>`_ **function (normally executed by the index.html of the dapp-browser).**

classes
=======
.. toctree::
  :maxdepth: 1
  :glob:

  AccountStore
  KeyProvider
  ipfs-cache
  idb-store

functions
=========
.. toctree::
  :maxdepth: 1
  :glob:

  functions

instances
=========
.. toctree::
  :maxdepth: 1
  :glob:

  config
  core
  CoreRuntime
  dapp
  evanGlobals
  ipfs
  restipfs
  lightwallet
  loading
  nameResolver
  queue
  routing
  solc
  System
  utils
  web3
  web3Helper

