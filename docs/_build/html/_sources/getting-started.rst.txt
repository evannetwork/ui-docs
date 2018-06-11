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

  - account id
  - lightwallet vault
  - provider (internal, external)
  - global synchronisation data queue

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

angular-core
============
The angular-core operates as an global and central library for the evan.network Angular 5 frontend development. Using this project you will be able to to the following things:

- easy import AngularCoreModule for including all services and components
- featured Angular DApp starting mechanisms

  - **IMPORTANT: use this functions for starting and stopping your nested Angular DApps to prevent memory leaks.**

- dynamic routes builder for nested Angular DApps
- comfortable UI services

  - Ionic alert service wrapper (smaller function calls + i18n)
  - file handling and upload  (HTML 5 + Ionic IOS + Ionic Android)
  - modal ui handler
  - picture capturing (HTML 5 + Ionic IOS + Ionic Android)
  - qr-code scanning (HTML 5 + Ionic IOS + Ionic Android)
  - Angular routing wrapper
  - Ionic slides wrapper and helpers 
  - Ionic toast service wrapper (smaller function calls + i18n)
  - translate (ngx-translate wrapper)

- comfortable BCC wrapper services
  - address-book
  - bcc
  - bc
  - bookmark
  - core
  - description
  - mailbox
  - onboarding

- queue handling
  - value pushing & dispatcher loading
  - queue-utilities (QueueId, ...)

- generalized Angular components

  - blockie

    - display blockie for an account id

  - bootstrap-component

    - global available Ionic bootstrap component

  - contract-members

    - generalized contract member managment

  - dapp-loader

    - load DApps within DApps using Angular components

  - dapp-wrapper top-bar for DApps that enables

    - back navigation
    - url routing has as title (dynamic)
    - mailbox alerts
    - queue status

  - dashboard-top-buttons

    - dynamic buttons that will be embedded to the dapp-wrapper on large screens or to the bottom right on small screen

  - dynamic-component

    - creates an dynamic component with a specific template during runtime

  - empty-dapp-display

    - shows an generalized "Theirs no data." screen using DApp DBCP descriptions

  - evan-loading

    - evan-network loading icon

  - *file-select (under construction)*

    - file selector for HTML 5 &IOS & Anroid

  - global-password

    - global password component that is used within each Angular DApp
    - will be registered in the root.ts in each evan.network featured DApp
    - unlocks the current users profile

  - big-picture

    - shows an picture within a modal

  - mail-dialog

    - dialog that will be openend, before a mail is sent

  - not-implemented

    - not implemented notice

  - qr-code-scanner

    - scan qr-codes on HTML 5 & IOS & Anroid

  - reload-route

    - reloads the current route (only available using dapp-wrapper)

  - split-pane

    - create easy Dashboards
    - generates an left panel using Ionic
    - powerfull in combination with DApps that using dapp-wrapper

  - take-snapshot

    - takes an img using camera on HTML 5 & IOS & Android

  - trust-dialog

    - asks for permissions (used before inviting an agent)

- Angular animation helpers

  - ngIf height growing
  - ngIf opacity showing
  - router transition management (easy to use) (eg.: route1 => route2 : swipe to the left / right / top / bottom)
  - tab swiping animation
  
- Angular 5 Onetime binding directive
- I18N handling using ngx-translate

angular-sass
============
The angular-sass library includes styling definitions for evan.network featured DApps.

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