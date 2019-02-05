======
Verifications
======

.. list-table:: 
   :widths: auto
   :stub-columns: 1

   * - Source
     - `claims <https://github.com/evannetwork/ui-core-dapps/tree/develop/dapps/claims>`__

General
=======
The claims library contains functionalities to handle and explore claims in an easy and expert way. Using the Verifications 

How to include
==============
To include this library, you need to add the following package into your project: "@evan.network/claims".

1. Add @evan.network/claims to your root project package.json.

2. Enhance tsconfig of your DApp so it can load the correct reference later from DBCP.json

::

  {
    ...

    "compilerOptions": {
      "paths": {
        ...
        "claims": [
          "../../../node_modules/@evan.network/claims/dist/claims.js"
        ],
        ...
      }
    }
  }

3. Add the claims dependency to your DApp's DBCP.json

::

  {
    "public": {
      "author": "evan GmbH",
      "dapp": {
        "dependencies": {
          "angular-core": "^1.4.0",
          "angular-libs": "^1.2.1",
          "claims": "^1.0.0"
        },
        ...
      }
    }
  }

4. Load the claims service in your module and include it in your DApp module

::

  import {
    VerificationLibraryModule,
    VerificationsTranslations,
  } from 'claims';

  ...

  let config: any = {
    imports: [
      AngularCore,
      VerificationLibraryModule,
      CommonModule,
    ],
    ...
  };

  ...

  @NgModule(getConfig(false))
  class ExplorerModule {
    constructor(
      private translations: Translations,
      private claimsTranslations: VerificationsTranslations
    ) { }
  }

5. Use the components within your DApp's components!

Verifications
===========
.. toctree::
  :maxdepth: 1
  :glob:

  ../claims/*
