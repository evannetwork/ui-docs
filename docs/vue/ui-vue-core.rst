===========
ui-vue-core
===========

.. list-table:: 
   :widths: auto
   :stub-columns: 1

   * - Source
     - `ui-vue-core <https://github.com/evannetwork/ui-vue/tree/master/dapps/evancore.vue.libs>`__

The ui-vue-core for evan.network includes specific vue components, helper functions and utilities. By using the vue initialization helper functions, it's very easy to setup a vue application including everything:

- features

  - global vue components
  - i18n
  - routing
  - Form building
  - evan.network blockchain-core runtime integration
  - DApp initialization && nested DApp loading
  - Sidebar integrations
  - login / logout mechanisms

- How to use it for creating DApps: `Wiki <https://evannetwork.github.io/docs/developers/ui/vue.html>`__

- Reference Projects:

  - `addressbook.vue <https://github.com/evannetwork/ui-core-dapps/tree/master/dapps/addressbook.vue>`__
  - `digital-twin <https://github.com/evannetwork/ui-core-dapps/tree/master/dapps/digital-twin>`__
  - `digital-twin.data-container <https://github.com/evannetwork/ui-core-dapps/tree/master/dapps/digital-twin.data-container>`__
  - `digital-twin.lib <https://github.com/evannetwork/ui-core-dapps/tree/master/dapps/digital-twin.lib>`__
  - `digital-twins <https://github.com/evannetwork/ui-core-dapps/tree/master/dapps/digital-twins>`__
  - `favorites.vue <https://github.com/evannetwork/ui-core-dapps/tree/master/dapps/favorites.vue>`__
  - `mailbox.vue <https://github.com/evannetwork/ui-core-dapps/tree/master/dapps/mailbox.vue>`__
  - `onboarding.vue <https://github.com/evannetwork/ui-core-dapps/tree/master/dapps/onboarding.vue>`__

Usage
=====

- dbcp.json

  .. code-block:: json

    {
      "public": {
        "dapp": {
          "dependencies": {
            "evancore.vue.libs": "^1.2.4"
          }
        }
      }
    }

- package.json

  .. code-block:: json

    {
      "dependencies": {
        "@evan.network/ui-vue-core": "^1.2.4"
      },
    }

- typescript

  .. code-block:: ts

    import Vue from 'vue';
    import { initializeVue } from '@evan.network/ui-vue-core';

    import Main from './components/root/root.vue';
    import translations from './i18n/translations';
    import routes from './routes';
    import components from './components/registry';

    export async function startDApp(container: any, dbcpName: any, dappEnsOrContract: any, dappBaseUrl: any) {
      await initializeVue({
        components,
        container,
        dappBaseUrl,
        dappEnsOrContract,
        dbcpName,
        RootComponent: Main,
        routes,
        state: { },
        translations: translations,
        Vue: Vue,
      });
    }


JS classes, functions
=====================

.. toctree::
  :maxdepth: 3
  :glob:

  ui-vue-core/js/*


Components
==========

.. toctree::
  :maxdepth: 3
  :glob:

  ui-vue-core/components/*
