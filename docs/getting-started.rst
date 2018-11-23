===============
Getting Started
===============

The evan.network frontend documentation describes the functionality of the core frontend libraries.

**This documentation does not explain how to setup and develop DApps. Have a look at** `dapps introduction <https://evannetwork.github.io/dapps/introduction>`_.

dapp-browser
============
The dapp-browser is the wrapper application for the evan.network DApp framework. Using the project you will be possible to create featured DApps.

By using the evan.network framework to create featured DApps, the initialization of DBCP or the blockchain core is completely replaced and existing, initialized and configured instances can be loaded. This has the advantage that accounts, encryptions and similar complex configurations are executed dynamically by the user when the application is started.

To do this, however, all DApps must be started via the evan.network dapp-browser application, since this provides the complete function stack and the various UIs. As long as the provided functions are used, the application can only be started in environments that have the corresponding structures.

The DApp browser provides several functionallities to access:

- DApp routing
- global utillity functions like log
- informations of the current logged in user
- blockchain connections configuration
- blockchain-core AccountStore and KeyProvider
- DApp time tracing options
- initialized blockchain-core structures
- IPFS cache
- ipfs handlers
- load and start sub DApps
- loading mechanisms
- SystemJS plugins for ENS loading, ENS and file loading, IPFS loading, JSON loading, CSS loading
- web3 handlers

blockchain-core frontend bundle
===============================
The |source bcc_bundlejs|_ is similar to the blockchain-core runtime and its build to handle several UI steps including blockchain-core instance without account interactions, blockchain-core instance including account id for profile interactions and blockchain-core instance to interact with business centers. It exposes the following Runtime parameters and several functions to create, handle and overwrite them:

- CoreRuntime: |source CoreInstance|_
- ProfileRuntime: |source ProfileInstance|_
- BCRuntime: |source BCInstance|_

angular-core
============
The `angular-core </angular-core/index.html>`_ operates as an global and central library for the evan.network Angular 5 frontend development. Using this project you will be able to to the following things:

- easy import AngularCoreModule for including all services and components
- featured Angular DApp starting mechanisms
- dynamic routes builder for nested Angular DApps
- comfortable UI services
- comfortable BCC wrapper services
- queue handling
- generalized Angular components
- Angular animation helpers
- Angular 5 Onetime binding directive
- I18N handling using ngx-translate

angular-libs
============
This `angular-libs </angular-libs/index.html>`_ contains a collection of Angular core libraries. This project is deployed to the ens (likelly to the angular-core), so you can require angular libraries (etc...) directly into the frontend without building duplicated libraries into your dapps.

- @angular
- @ionic-native
- @ngx-translate
- @zxing
- ionic-angular
- ionic-tags-input
- ng-circle-progress
- rxjs

angular-sass
============
The `angular-sass </angular-sass/index.html>`_ library includes styling definitions for evan.network featured DApps.

- font-style: Open Sans
- `Ionic Styles <https://github.com/ionic-team/ionic>`_
- positioning & color sass variables
- evan.network start page & loading symbol
- alert style adjustments
- button styles
- content containers with dynamic sizes
- dashboard side panel style
- form specific stylings
- grid styles
- modal styles
- popover styles
- table styles
- tab styles
- Ionic adjustments
- evan theming

.. |source bcc_bundlejs| replace:: ``blockchain-core frontend bundle``
.. _source bcc_bundlejs: https://github.com/evannetwork/api-blockchain-core/blob/develop/src/bundles/bcc/bcc.ts

.. |source CoreInstance| replace:: ``CoreInstance``
.. _source CoreInstance: /bcc/bcc-bundle.html#coreinstance

.. |source ProfileInstance| replace:: ``ProfileInstance``
.. _source ProfileInstance: /bcc/bcc-bundle.html#profileinstance

.. |source BCInstance| replace:: ``BCInstance``
.. _source BCInstance: /bcc/bcc-bundle.html#bcinstance
