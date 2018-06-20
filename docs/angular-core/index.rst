============
angular-core
============

General
=======
The `angular-core </angular-core/index.html>`_ operates as an global and central library for the evan.network Angular 5 frontend development. Using this project you will be able to to the following things:

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

Usage
=====
Include the AngularCore module into your module and all of the services, components, directives (...) are defined within your project.

- tsconfig.json

.. code-block:: json

  {
    "compilerOptions": {
      "declaration": true,
      "module": "es2015",
      "target": "es5",
      "baseUrl": "./src",
      "stripInternal": true,
      "emitDecoratorMetadata": true,
      "experimentalDecorators": true,
      "moduleResolution": "node",
      "outDir": "../build",
      "rootDir": "./src",
      "lib": [
        "es2015",
        "dom"
      ],
      "skipLibCheck": true,
      "types": [],
      "paths": {
        "angular-core": [
          "../node_modules/@evan.network/angular-core/dist/angularcore.js"
        ]
      }
    },
    "angularCompilerOptions": {
      "annotateForClosureCompiler": true,
      "strictMetadataEmit": true,
      "skipTemplateCodegen": true,
      "flatModuleOutFile": "dashboard.js",
      "flatModuleId": "dashboard"
    },
    "files": [
      "./index.ts"
    ]
  }

- module.ts

.. code-block:: typescript

  import {
    AngularCore,
  } from 'angular-core';

  @NgModule({
    ...
    imports: [
      CommonModule,
      AngularCore,
    ],
    ...
  })
  class SampleModule {
    constructor() { }
  }

Next to the ususal angular stuff, additional functionallities are provided to handle nested ionic angular apps and a dynamic routing. For this have a look at additionals.

Additionals
===========
.. toctree::
  :maxdepth: 1
  :glob:

  additionals/*

Animations
==========
.. toctree::
  :maxdepth: 1
  :glob:

  animations/*

Components
==========
.. toctree::
  :maxdepth: 1
  :glob:

  components/*

Directives
==========
.. toctree::
  :maxdepth: 1
  :glob:

  directives/*

Modules
=======
.. toctree::
  :maxdepth: 1
  :glob:

  modules/*

Pipes
=====
.. toctree::
  :maxdepth: 1
  :glob:

  pipes/*

General Services
================
.. toctree::
  :maxdepth: 1
  :glob:

  services/utils
  services/singleton-service

UI Services
===========
.. toctree::
  :maxdepth: 1
  :glob:

  services/ui/*

BCC Services
============
.. toctree::
  :maxdepth: 1
  :glob:

  services/bcc/*
