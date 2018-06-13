============
dapp-browser
============

The `dapp-browser <https://github.com/evannetwork/dapp-browser>`_ is used to start applications over it. Within this applications, several classes, functions and runtime instances can be used. General DApps will be opened like the following "https://.../index.html#/my-dapp-ens.evan". Where the index.html file is the entry point of the dapp-browser. Within the DApp the dapp-browser can be used like the following example:

- typescript file:

.. code-block:: typescript

  import {
    config,
    getDomainName
  } from 'dapp-browser';

- tsconfig.json

.. code-block:: typescript

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


usage for development
================================================================================
The src folder includes a dev.html and a index.html file. By opening the dev.html file, the code will bypass several code loading checks, to try to load dapps from the local file server. The compiled files from the "src/app" folder will be placed within the runtime folder. Chosen files will be copied to the www folder for deployment and native app building. Durin the dev mode the application will try to load dapps not from ens and ipfs, but from the local file server (runtime/external). This folder will be filled using `angular-gulp <https://github.com/evannetwork/angular-gulp>`_ and the lerna DApp projects (e.g. `core-dapps <https://github.com/evannetwork/core-dapps>`_). During production mode, each DApp or contract will be loaded using its ens or contract address and dbcp description. How to develop DApps, that can be loaded via the dapp-browser, have a look here `DApp Basics <https://evannetwork.github.io/dapps/basics>`_.

For more informations on how to start the dapp-browser locally and on how to deploy DApps have a look at `dapp-browser <https://github.com/evannetwork/dapp-browser>`_ git repository. 

classes
=======
.. toctree::
  :maxdepth: 1
  :glob:

  account-store
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
  queue
  routing
  solc
  System
  utils
  web3Helper

