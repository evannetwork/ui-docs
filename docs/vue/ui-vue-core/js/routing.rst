=======
routing
=======

.. list-table:: 
   :widths: auto
   :stub-columns: 1

   * - Source
     - `routing <https://github.com/evannetwork/ui-vue/tree/master/dapps/evancore.vue.libs/src/routing.ts>`__

Routing within the evan.network is not the same as in a usal web application. DApps can be loaded nested, by referencing it's ens addresses within the url hash. The root application is presented at the first one within the hash (e.g. #/dashboard.vue.evan). The ui-vue-core will automatically handle this urls and will enhance your routing configuration, that was passed to the `initializeVue function <./vue-core.html>`__, to handle the correct nested routes. As a result of this, you can define your routes simply, relative to the root of your application and it will also work nested.

Here a sample using `mailbox.vue routes <https://github.com/evannetwork/ui-core-dapps/blob/master/dapps/mailbox.vue/src/routes.ts>`__, assuming the mailbox is opened nested within the dashboard.vue:

- URL: http://localhost:3000/dev.html#/dashboard.vue.evan/mailbox.vue.evan

- routes definition

  .. code-block:: typescript
    
    // using the mailbox.vue sample routes
    const routeRegistration: Array<RouteRegistrationInterface> = [
      { path: '', redirect: { path: 'received' } },
      { name: 'add', path: 'add', component: AddComponent },
      { name: 'mail-category', path: ':category', },
    ];

- routing result

  .. code-block:: json

    // will initialize the following routing structure
    // [
    //   {
    //     "path": "/dashboard.vue.evan/mailbox.vue.evan/",
    //     "redirect": {
    //       "path": "/dashboard.vue.evan/mailbox.vue.evan/received"
    //     }
    //   },
    //   {
    //     "name": "add",
    //     "path": "/dashboard.vue.evan/mailbox.vue.evan/add"
    //   },
    //   {
    //     "name": "mail-category",
    //     "path": "/dashboard.vue.evan/mailbox.vue.evan/:category"
    //   },
    //   {
    //     "path": "/dashboard.vue.evan/mailbox.vue.evan/**",
    //     "name": "dapp-loader-1562070796215.624"
    //   }
    // ]

**Notice the last entry within the routing result. The vue-core will automatically add the wildcard route to your routing. As a result of this, unkown routes will be resolved against the ui-dapp-browser. If a correct ens / contract address is detected, the nested sub dapp will be opened under your DApp's router using the** `dapp-loader <../components/dapp-loader.html>`__.

--------------------------------------------------------------------------------

.. _routing_dappInterface:

ActiveDAppInterface
================================================================================

Base routing definitions, urls and opened dapp informations can be found within your vue instance vuex-store (this.$store.state.dapp) that includes the following parameters and create by the `getNextDApp function <./routing.html#getNextDApp>`__

----------
Parameters
----------

#. ``baseHash`` - ``string``: parent nested dapp path (e.g. url = dashboard.vue.evan/mailbox.vue.evan/test.vue.evan, baseHash will be dashboard.vue.evan/mailbox.vue.evan)
#. ``baseUrl`` - ``string``:  currents url without hash
#. ``contractAddress`` - ``string``: if a dapp was opened directly using a contractAddress or by applying a contractAddress as first routing path behind your dapps ens path, the contract address will be applied to your dapps base route and applied to the dapp definition.
#. ``domainName`` - ``string``: currents domain name (e.g.: evan, test.evan)
#. ``ens`` - ``string``:  ens address of the opened dapp (test.vue.evan),
#. ``fullUrl`` - ``string``:  full url to your dapp (https://dashboard...#dashboard.vue.evan)
#. ``rootEns`` - ``string``:  ensParts[1],

--------------------------------------------------------------------------------

.. _routing_getRouteWithDAppBase:

getRouteWithDAppBase
================================================================================

.. code-block:: typescript

  routing.getRouteWithDAppBase(path, dapp);

Uses the dapps.basehash and appends the given path.

----------
Parameters
----------

#. ``path`` - ``string``: the route path that should be opened
#. ``somethingElse`` - ``string`` (optional): this can be set if required, defaults to ``"latest"``

-------
Example
-------

.. code-block:: typescript

  clonedRoute.path = getRouteWithDAppBase(clonedRoute.path, dappToLoad);




--------------------------------------------------------------------------------

.. _routing_initializeRouting:

initializeRouting
================================================================================

.. code-block:: typescript

  routing.initializeRouting(options);

Start the routing for a vue application. Clones the original routes and sets the base routing (= current dapp that should be opened).

----------
Parameters
----------

#. ``options`` - Partial |source EvanVueOptionsInterface|_: vue initialization options
  #. ``dappEnsOrContract`` - ``string``: ENS of the application
  #. ``routes`` - ``Array<any>``: Array of routes defined using the `Vue router structure <https://router.vuejs.org/guide/essentials/dynamic-matching.html>`__
  #. ``Vue`` - ``any``: Vue class

-------
Returns
-------

``Promise`` returns ``any``: resolved when done
  
  #. ``dappToLoad`` - |source ActiveDAppInterface|_: dapp to load definition
  #. ``router`` - ``Vue Router``: vue router instance
  
-------
Example
-------

.. code-block:: typescript

  const { dappToLoad, router } = await initializeRouting(options);

  Vue.use(Vuex);
  const store = new Vuex.Store({
    state: {
      options,
      uiLibBaseUrl,
      dapp: dappToLoad,
      ...options.state,
    },
  });

  const vue = new Vue({
    el: options.container,
    router,
    store,
  });




--------------------------------------------------------------------------------

.. _routing_getNextDApp:

getNextDApp
================================================================================

.. code-block:: typescript

  rotuing.getNextDApp(dappEnsOrContract);

Retrieves the url hash path for the next dapp, that should be loaded, by checking the
dappEnsOrContract address or by tracing every url hash part and checks, if an element with the
dom id exists.

Returns ens:

  - ens: ens address of the loaded dapp

  - contractAddess: optional detected contract address

  - baseHash: base of the dapp

E.g.: opened url #/dashboard.evan/onboarding.evan

  #. dashboard.evan element was not found, start it

  #. dashboard.evan/** will be triggered and loads the dapp-loader compoment

  #. dapp-loader tracks the url hashes and detects the dashboard.evan/onboarding.evan route and will start this dapp in the dapp-loader

  #. when navigating to /dashboard.evan/digitaltwins.evan, the dapp-loader trackts the url change and 3. will be started with the new url hash

----------
Parameters
----------

#. ``options`` - ``object``: The options used for calling
    * ``from`` - ``string`` (optional): The address the call "transaction" should be made from
#. ``callback`` - ``Function`` (optional): This callback will be fired..
#. ``somethingElse`` - ``string`` (optional): this can be set if required, defaults to ``"latest"``

-------
Returns
-------

``Promise`` returns |source ActiveDAppInterface|_: dapp that should be loaded

-------
Example
-------
Example for dynamically loading the next dapp from the url

.. code-block:: typescript

  /**
   * Searches for the next dapp in the url that should be started and run it
   */
  async startDApp() {
    // clear everything, that was loaded before
    // !IMPORTANT: clear the inner html before running getNextDApp
    //   => it will check for elements dapp names as id's, to check which dapp was already loaded
    //   => by forcing dapp loading under an other domain, will cause false domain loading
    this.$el.innerHTML = '';

    // get module id
    this.startedDApp = await getNextDApp();

    // create a new container el, vue will replace this element
    const containerEl = document.createElement('div');
    this.$el.appendChild(containerEl);

    // startup the dapp
    await dappBrowser.dapp.startDApp(this.startedDApp.ens, containerEl);
  }


.. |source ActiveDAppInterface| replace:: ``ActiveDAppInterface``
.. _source ActiveDAppInterface: ./routing.html#actvedappinterface


.. |source EvanVueOptionsInterface| replace:: ``EvanVueOptionsInterface``
.. _source EvanVueOptionsInterface: ./vue-core.html#evanvueoptionsinterface
  