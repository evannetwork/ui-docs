===================
DAppLoaderComponent
===================

.. list-table:: 
   :widths: auto
   :stub-columns: 1

   * - Source
     - `dapp-loader <https://github.com/evannetwork/ui-vue/tree/master/dapps/evancore.vue.libs/src/components/dapp-loader>`__
   * - Selector
     - ``evan-dapp-loader``

Dynamic component that loads the next not loaded dapp within the window location hash using the `getNextDApp function <../js/routing.html#getNextDApp>`__.

#. ``startedDApp`` - ``any``: save the latest dapp path that was started, so we can check on an hash change, if the dapp for this dapp loader has been changed.
#. ``hashChangeWatcher`` - ``any``: Watch for hash updates and start a new dapp, when the corresponding hash for this dapp-loader has been changed
#. ``dappNotFound`` - ``boolean``: no valid dapp could be found for the currently opened route
#. ``wasDestroyed`` - ``boolean``: Was the component destroyed, before the hash change event was bind?


Example
=======
- `Reference Implementation <https://github.com/evannetwork/ui-core-dapps/blob/master/dapps/digital-twin/src/routes.ts>`__

.. code-block:: typescript

  import { DAppLoaderComponent, } from '@evan.network/ui-vue-core';

  const routeRegistration: Array<RouteRegistrationInterface> = [
    { name: 'dt-map',               component: MapComponent,           path: dtPath('dt-map'), },
    { name: 'dt-container',         component: DAppLoaderComponent,    path: dtPath(`datacontainer.digitaltwin.${ dappBrowser.getDomainName() }/**`), },
  ];

.. code-block:: html

  <dapp-loader></dapp-loader>

