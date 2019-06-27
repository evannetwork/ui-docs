================================
api-blockchain-core-browserified
================================

.. list-table:: 
   :widths: auto
   :stub-columns: 1

   * - Source
     - `api-blockchain-core-browserified <https://github.com/evannetwork/ui-core/tree/master/dapps/bcc>`__


evan.network framework
======================
Using the browserified blockchain-core version within the dapp-browser, you need apply the following configurations to your dapp's project. Be sure, to exclude it from your build jobs. The angular-gulp project will handle it automatically. By using vue applications, it will be configured within the `vue/webpack.config.js <https://github.com/evannetwork/ui-core-dapps/blob/master/vue/webpack.externals.js>`__ file.

- `package.json <https://github.com/evannetwork/ui-core/blob/master/package.json>`__

.. code-block:: json

  {
    "dependencies": {
      "@evan.network/api-blockchain-core": "^2.7.1"
    },
  }

- `dbcp.json <https://github.com/evannetwork/ui-vue/blob/master/dapps/evancore.vue.libs/dbcp.json>`__

.. code-block:: json

  {
    "public": {
      "dapp": {
        "dependencies": {
          "bcc": "^2.7.1"
        }
      }
    }
  }

- `in typescript <https://github.com/evannetwork/ui-vue/blob/master/dapps/evancore.vue.libs/src/components/dapp-wrapper/dapp-wrapper.ts>`__

.. code-block:: ts

  import * as bcc from '@evan.network/api-blockchain-core';


Standalone usage
================
You can also build the browserified version directly within your application. Have a look at the following  `example <https://github.com/w11k/angular7-evan-network>`__
