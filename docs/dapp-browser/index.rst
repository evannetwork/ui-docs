============
dapp-browser
============

The `dapp-browser <https://github.com/evannetwork/ui-dapp-browser>`_ is used to start applications over it. Within this applications, several classes, functions and runtime instances can be used. General DApps will be opened like the following "https://.../index.html#/my-dapp-ens.evan". Where the index.html file is the entry point of the dapp-browser.

It is the wrapper application for the evan.network DApp framework. Using the project you will be possible to create featured DApps.

By using the evan.network framework to create featured DApps, the initialization of DBCP or the blockchain core is completely replaced and existing, initialized and configured instances can be loaded. This has the advantage that accounts, encryptions and similar complex configurations are executed dynamically by the user when the application is started.

To do this, however, all DApps must be started via the evan.network dapp-browser application, since this provides the complete function stack and the various UIs. As long as the provided functions are used, the application can only be started in environments that have the corresponding structures.

**Be aware: The instances will only be exposed when the dapp-browser is started using the** `initializeEvanNetworkStructure </dapp-browser/functions.html#initializeevannetworkstructure>`_ **function (normally executed by the index.html of the dapp-browser).**

Installation
============
.. code-block:: sh

  npm i dapp-browser

Usage as Dependency
===================
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
          "../node_modules/@evan.network/ui-dapp-browser/runtime/build/main.js"
        ]
      }
      ...
    }
  }


Usage for local Development
===========================
The src folder includes a dev.html and a index.html file. By opening the dev.html file, the code will bypass several code loading checks, to try to load dapps from the local file server. The compiled files from the "src/app" folder will be placed within the runtime folder. Chosen files will be copied to the www folder for deployment and native app building. Durin the dev mode the application will try to load dapps not from ens and ipfs, but from the local file server (runtime/external). This folder will be filled using `angular-gulp <https://github.com/evannetwork/angular-gulp>`_ and the lerna DApp projects (e.g. `core-dapps <https://github.com/evannetwork/ui-core-dapps>`_). During production mode, each DApp or contract will be loaded using its ens or contract address and dbcp description. How to develop DApps, that can be loaded via the dapp-browser, have a look here `DApp Basics <https://evannetwork.github.io/dapps/basics>`_.

For more informations on how to start the dapp-browser locally and on how to deploy DApps have a look at `dapp-browser <https://github.com/evannetwork/ui-dapp-browser>`_ git repository. 

Classes
=======
.. toctree::
  :maxdepth: 1
  :glob:

  account-store
  KeyProvider
  ipfs-cache
  idb-store

Functions
=========
.. toctree::
  :maxdepth: 1
  :glob:

  functions

Instances
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
  lightwallet
  loading
  notifications
  queue
  restipfs
  routing
  solc
  System
  utils
  web3Helper
