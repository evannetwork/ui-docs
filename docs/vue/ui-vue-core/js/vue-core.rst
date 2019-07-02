========
vue-core
========

.. list-table:: 
   :widths: auto
   :stub-columns: 1

   * - Source
     - `vue-core <https://github.com/evannetwork/ui-vue/tree/master/dapps/evancore.vue.libs/src/vue-core.ts>`__

General functions for handling and starting vue instance within evan.network featured dapps.


--------------------------------------------------------------------------------

.. _vueCore_initializeVue:

initializeVue
================================================================================

.. code-block:: typescript

  vueCore.initializeVue(options);

Starts an evan vue dapp, wraps all start functionallities and adds initialized vue dependencies (vue-router, vuex-i18n, ..., have a look at the `ui-vue-core index <../index.html>`__).

----------
Parameters
----------

#. ``options`` - |source EvanVueOptionsInterface|_: vue options passed by the dapp

-------
Returns
-------

``Promise`` returns ``void``: initialized vue instance with all the configurations.

-------
Example
-------

.. code-block:: typescript

  /**
   * StartDapp function that is called by the ui-dapp-browser, including an container and the current
   * dbcp. So startup, it's evan time!
   *
   * @param      {any}     container    container element
   * @param      {string}  dbcpName     dbcp name of the dapp
   * @param      {any}     dappEnsOrContract  original ens / contract address that were loaded
   * @param      {string}  dappBaseUrl  origin of the dapp
   */
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




--------------------------------------------------------------------------------

.. _vueCore_registerComponents:

registerComponents
================================================================================

.. code-block:: typescript

  vueCore.registerComponents(Vue, components);

Registers the components within Vue. If a name is specified, register it also as component, not only for routing.

----------
Parameters
----------

#. ``Vue`` - ``any``: The options used for calling
#. ``components`` - ``<Array<any>>``: components that should be registered
  #. ``name`` - ``string``: name of the component that should be registered
  #. ``component`` - ``VueComponent``: Vue Component definition

-------
Returns
-------

``Promise`` returns ``void``: resolved when done

-------
Example
-------

.. code-block:: typescript

  @Component({ })
  class DAppLoaderComponent extends mixins(EvanComponent) {
    ...
  }

  vueCore.registerComponents(Vue, [
    { name: 'evan-dapp-loader', component: DAppLoaderComponent },
  ]);




--------------------------------------------------------------------------------

.. _vueCore_registerEvanI18N:

registerEvanI18N
================================================================================

.. code-block:: typescript

  vueCore.registerEvanI18N(Vue, translations);

Register the current translations within i18n vuex js.

----------
Parameters
----------

#. ``Vue`` - ``Vue``: The options used for calling
#. ``translations`` - ``any``: translation definition mapped to languages

-------
Example
-------

.. code-block:: typescript

  const translations = {
    de: {
      'helloWorld': 'Hallo Welt',
    },
    en: {
      'helloWorld': 'Hello World',
    }
  }

  vueCore.registerEvanI18N(Vue, translations);




--------------------------------------------------------------------------------

.. _vueCore_registerEventHandlers:

registerEventHandlers
================================================================================

.. code-block:: typescript

  vueCore.registerEventHandlers(vueInstance);

Vue does not trigger correct destroy events when a vue application is removed from the dom or when the browser is freshed. This will cause uncleared watchers and memory leaks. This function binds window unload event handlers and a vue base element MutationObserver, so we can trigger correct vue destroy events when DApps are removed from the dom.

----------
Parameters
----------

#. ``vueInstance`` - ``Vue``: initialized vue instance

-------
Example
-------

.. code-block:: typescript

  const vue = new Vue({
    el: options.container,
    router,
    store,
  });

  // register event handlers, so multiple vue instance and removed dom elements will be destroyed
  // correctly
  registerEventHandlers(vue);



.. |source EvanVueOptionsInterface| replace:: ``EvanVueOptionsInterface``
.. _source EvanVueOptionsInterface: ./vue-core.html#evanvueoptionsinterface