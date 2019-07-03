===============
IframeComponent
===============

.. list-table:: 
   :widths: auto
   :stub-columns: 1

   * - Source
     - `iframe <https://github.com/evannetwork/ui-vue/tree/master/dapps/evancore.vue.libs/src/components/iframe>`__
   * - Selector
     - ``evan-iframe``

replaceme

#. ``loading`` - ``boolean``: iframe is loading

Props
=====

#. ``src`` - ``string``: The iframes src that should be rendered


Example
=======
- `Reference Implementation <https://github.com/evannetwork/ui-core-dapps/blob/develop/dapps/dashboard.vue/src/routes.ts>`__

- typescript

  .. code-block:: typescript

    import { EvanIframeComponent } from '@evan.network/ui-vue-core';

    const routeRegistration: Array<RouteRegistrationInterface> = [
      {
        path: '',
        redirect: { path: 'github' }
      },
      {
        path: 'github',
        component: EvanIframeComponent,
        props: { src: 'https://evannetwork.github.io' }
      },
      {
        path: `bccdocs`,
        component: EvanIframeComponent,
        props: { src: '//api-blockchain-core.readthedocs.io/en/latest/' }
      },
      {
        path: `uidocs`,
        component: EvanIframeComponent,
        props: { src: '//ui-docs.readthedocs.io/en/latest/' }
      },
    ];


- typescript

  .. code-block:: html

    <evan-iframe
      :src="https://dashboard.test.evan.network">
    </evan-iframe>


