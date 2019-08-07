=========
component
=========

.. list-table:: 
   :widths: auto
   :stub-columns: 1

   * - Source
     - `component <https://github.com/evannetwork/ui-vue/tree/master/dapps/evancore.vue.libs/src/component.ts>`__

Evan.network component wrapper for easily accessing blockchain runtime data and active DApp information.

Extends vue components with the following parameters:

#. ``dappEns`` - ``string``: Original dapp ens address.
#. ``name`` - ``string``: Technical exported class member of the dispatcher within the dapp.

#. ``dapp`` - |source ActiveDAppInterface|_: active dapp that was detected by the `routing lib (getNextDApp) <./routing.html#getNextDApp>`__
#. ``domainName`` - ``string``: Active dapp browser domain name (e.g.: evan)
#. ``$i18n`` - `vuex i18n <https://github.com/evannetwork/ui-vue/tree/master/dapps/i18n.vuex.libs>`__: vue i18n instance 
#. ``$router`` - `$router <https://github.com/evannetwork/ui-vue/tree/master/dapps/router.vue.libs>`__: vue router instance
#. ``$store`` - `vuex <https://github.com/evannetwork/ui-vue/tree/master/dapps/vuex.libs>`__: vuex store
#. ``$t`` - `vuex i18n <https://github.com/evannetwork/ui-vue/tree/master/dapps/i18n.vuex.libs>`__: vuex i18n translate function
#. ``testMode`` - ``boolean``: is `localstorage['evan-test-mode'] set?




--------------------------------------------------------------------------------

.. _comoponents_evanNavigate:

evanNavigate
================================================================================

.. code-block:: typescript

  this.evanNavigate(path, baseHash);

Custom navigation method for evan vue projects. Always navigates using window.location.hash to force hash chaning on nested DApps.

----------
Parameters
----------

#. ``path`` - ``string``: path that should be navigated to
#. ``baseHash`` - ``string``: navigation base hash (e.g. dashboard.vue.evan, default = this.dapp.baseHash)

-------
Example
-------

.. code-block:: typescript

  this.evanNavigate(`addressbook.vue.${ this.dapp.domainName }`, `/${ this.dapp.rootEns }`)




--------------------------------------------------------------------------------

.. _components_activeDApp:

activeDApp
================================================================================

.. code-block:: typescript

  this.activeDApp();

Returns the active dapp object, including the current contract address, route base hash and ens address.

-------
Returns
-------

`dapp definition <./routing.html#getNextDApp>`__: active dapp (this.$store.state.dapp)

-------
Example
-------

.. code-block:: typescript

  console.dir(this.activeDApp());

  // {
  //   "baseHash": "/dashboard.vue.evan/addressbook.vue.evan",
  //   "baseUrl": "http://localhost:3000/dev.html#",
  //   "domainName": "evan",
  //   "ens": "addressbook.vue.evan",
  //   "fullUrl": "http://localhost:3000/dev.html#/dashboard.vue.evan/addressbook.vue.evan",
  //   "rootEns": "dashboard.vue.evan"
  // }




--------------------------------------------------------------------------------

.. _components_getRuntime:

getRuntime
================================================================================

.. code-block:: typescript

  this.getRuntime();

Returns the current runtime from the state or returns an dappBrowser core runtime. Please note to login, before using the login specific runtime functions. By using the `DApp Wrapper <../components/dapp-wrapper.html>`__ within your DApp, it will be handled automatically.

-------
Returns
-------

`blockchain core runtime <https://api-blockchain-core.readthedocs.io/en/latest/getting-started.html#adding-blockchain-core>`__: initialized blockchain core runtime


.. |source ActiveDAppInterface| replace:: ``ActiveDAppInterface``
.. _source ActiveDAppInterface: ./routing.html#actvedappinterface
