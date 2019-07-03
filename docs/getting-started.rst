===============
Getting Started
===============

The evan.network frontend documentation describes the functionality of the core frontend libraries.

**This documentation does not explain how to setup and develop DApps. Have a look at** `writing dapps <https://evannetwork.github.io/docs/developers/ui/writing-dapps.html>`_.

ui-dapp-browser
===============
The dapp-browser is the wrapper application for the evan.network DApp framework. Using the project you will be possible to create featured DApps.

By using the evan.network framework to create featured DApps, the initialization of DBCP or the blockchain core runtime is completely replaced and existing, initialized and configured instances can be loaded. This has the advantage that accounts, encryptions and similar complex configurations are executed dynamically by the user when the application is started.

To do this, however, all DApps must be started via the evan.network dapp-browser application, since this provides the complete function stack and the various UIs. As long as the provided functions are used, the application can only be started in environments that have the corresponding structures (e.g. https://dashboard.test.evan.network, local file server).

--------------------------------------------

ui-core
=======

open source projects
--------------------
The ui-core contains several dapps, that simply wraps open source projects, that will be available within the evan.network, so it can be simply imported using dbcp.json.

evan.network projects
---------------------
The ui-core contains several dapps, that simply wraps evan.network projects like the `api-blockchain-core-browserified <https://github.com/evannetwork/ui-core/tree/master/dapps/bcc>`__ or the `smart-contracts-core-browserified <https://github.com/evannetwork/ui-core/tree/master/dapps/smartcontracts>`__.

Furthermore it includes the new ui core library, that provides base functionallities and core stylings based on bootstrap and  `core functionallities and stylings <https://github.com/evannetwork/ui-core/tree/master/dapps/ui.libs>`__

--------------------------------------------

ui-vue
=======
The `ui-vue <https://github.com/evannetwork/ui-vue>`__ is a container for the vue specific evan.network applications and libraries. It include dapp wrappers for simply building and providing vue evan.network / vue open source libraries as dapps within the evan.network framework.

The main application in this lerna container is the `@evan.network/ui-vue-core <./ui-vue-core.html>`__ project.

--------------------------------------------

Angular 5 & Ionic
=================

ui-angular-core
---------------
The `angular-core </angular-core/index.html>`_ operates as an global and central library for the evan.network Angular 5 frontend development. Using this project you will be able to to the following things:

ui-angular-libs
---------------
This `angular-libs </angular-libs/index.html>`_ contains a collection of Angular core libraries. This project is deployed to the ens (likelly to the angular-core), so you can require angular libraries (etc...) directly into the frontend without building duplicated libraries into your dapps.

ui-angular-sass
---------------
The `angular-sass </angular-sass/index.html>`_ library includes styling definitions for evan.network featured DApps.

.. |source bcc_bundlejs| replace:: ``blockchain-core frontend bundle``
.. _source bcc_bundlejs: https://github.com/evannetwork/api-blockchain-core/blob/develop/src/dist/index.js.ts

.. |source CoreInstance| replace:: ``CoreInstance``
.. _source CoreInstance: /bcc/bcc-bundle.html#coreinstance

.. |source ProfileInstance| replace:: ``ProfileInstance``
.. _source ProfileInstance: /bcc/bcc-bundle.html#profileinstance

.. |source BCInstance| replace:: ``BCInstance``
.. _source BCInstance: /bcc/bcc-bundle.html#bcinstance
