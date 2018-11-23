==================
EvanRoutingService
==================

.. list-table:: 
   :widths: auto
   :stub-columns: 1

   * - Source
     - `routing <https://github.com/evannetwork/ui-angular-core/blob/develop/src/services/ui/routing.ts>`__

Angular 5 routing wrapper service.

**Be aware: We are doing fancy stuff to handle dynamic routing over cross Angular applications. We cant use the Ionic router for the app view routing, because its to restricted. Ionic router is only used for internal services like alerts, toasts and so on.**

This service overwrite some original Router functions to replace the normale angular "routing" call with an window.location.hash = "...", so each router change, in each angular instance, gets triggered.


--------------------------------------------------------------------------------

.. _document_getRoute:

getRoute
================================================================================

.. code-block:: typescript

  initializedModule.getRoute(path, parent);

Lookup the current route configuration or it's parent, to find an route where the path exists.

----------
Parameters
----------

#. ``path`` - ``string``: Route path to find
#. ``parent`` - ``any``: A route configuration where the child should be searched.

-------
Returns
-------

``any``: The loaded route

-------
Example
-------

::

.. code-block:: typescript

  // current route configuration
  // [
  //   {
  //     path: '',
  //     component: DAppListComponent,
  //     data: {
  //       state: 'dapplist'
  //     }
  //   },
  //   {
  //     path: 'dapp-add',
  //     component: DAppAddComponent,
  //     data: {
  //       state: 'dappadd',
  //       navigateBack : '..'
  //     }
  //   },
  // ]

  const route = routingService.getRoute('dapp-add')
  // will return route instance of second children 'dapp-add' instance




--------------------------------------------------------------------------------

.. _document_getRouteFromUrl:

getRouteFromUrl
================================================================================

.. code-block:: typescript

  routingService.getRouteFromUrl(routeUrl);

Takes an routeUrl, removes #, /#, #/ and returns the original hash value without query params

----------
Parameters
----------

#. ``routeUrl`` - ``string``: RouteUrl like the following : #/dapp/dapp1?param1=est

-------
Returns
-------
Will transform #/dapp/dapp1?param1=est to dapp/dapps

``Promise`` returns ``void``: resolved when done

-------
Example
-------

.. code-block:: typescript

  routingService.getRouteFromUrl('#/dapp/dapp1?param1=est')
  routingService.getRouteFromUrl(window.location.hash);




--------------------------------------------------------------------------------

.. _document_activeRouteName:

activeRouteName
================================================================================

.. code-block:: typescript

  routingService.activeRouteName();

Watches the current router url and splits out the last hash param that represents the module id.

**Don't forget to unsubscribe on component destroy**.

-------
Returns
-------

``Observable`` returns ``string``: an Observable that resolves url updates.

-------
Example
-------

.. code-block:: typescript

  // https://dashboard.evan.network/#/taskboard.evan will return => taskboard
  const subscription = routingService
    .activeRouteName()
    .subscribe(async (value) => {
      console.log(value);
    });

  ngOnDestroy() {
    subscription();
  }




--------------------------------------------------------------------------------

.. _document_activeRootRouteName:

activeRootRouteName
================================================================================

.. code-block:: typescript

  routingService.activeRootRouteName();

Watches the current router url and splits out the last hash param that represents the module id.

**Don't forget to unsubscribe on component destroy**.

-------
Returns
-------

``Observable`` returns ``string``: an Observable that resolves url updates.

-------
Example
-------

.. code-block:: typescript

  // https://dashboard.evan.network/#/dashboard.evan/favorites.evan will return => dashboard
  const subscription = this.routing
    .activeRouteName()
    .subscribe(async (value) => {
      console.log(value);
    });

  ngOnDestroy() {
    subscription();
  }




--------------------------------------------------------------------------------

.. _document_getActiveChild:

getActiveChild
================================================================================

.. code-block:: typescript

  routingService.getActiveChild(route, deep, childPath);

Returns the deepest activedRoute of the current parent activatedRoute. This one will be the active route. Used to consume route data.

----------
Parameters
----------

#. ``route`` - ``ActivatedRoute``: The activatedRoute or one of it's children
#. ``deep`` - ``number``: Recursion deep, cancel after 20 recursion to prevent dead lock
#. ``childPath`` - ``string``: Check for an additional childPath to return innerst active route

-------
Returns
-------

``ActivatedRoute``: deepest ActivatedRoute

-------
Example
-------

.. code-block:: typescript

  console.log(this.getActiveChild(this.activeRoute).params)




--------------------------------------------------------------------------------

.. _document_setNavigateBackStatus:

setNavigateBackStatus
================================================================================

.. code-block:: typescript

  routingService.setNavigateBackStatus();

Search for the current active route and set the current navigateBackStatus. This is used by "canNavigateBack" and "goBack" function to handle display of back button or to go to a specific route.

**Have a look at |source route_configuration|_**.

-------
Example
-------

.. code-block:: typescript

  routingService.setNavigateBackStatus();




--------------------------------------------------------------------------------

getActiveRoot
================================================================================

.. code-block:: typescript

  routingService.getActiveRoot();

Returns the current root component.

.. code-block:: typescript

  return this.activeRoute.firstChild;

-------
Returns
-------

``Promise`` returns ``void``: resolved when done

-------
Example
-------
Navigate relative to the current route to an other sub dapp.

.. code-block:: typescript

  routingService.getActiveRoot();






--------------------------------------------------------------------------------

.. _document_getDAppNameFromRoutePath:

getDAppNameFromRoutePath
================================================================================

.. code-block:: typescript

  routingService.getDAppNameFromRoutePath(routePath);

Get the DApp name from an route

----------
Parameters
----------

#. ``routePath`` - ``string``: route path to parse the dapp from

-------
Returns
-------

``string``: dappName

-------
Example
-------

.. code-block:: typescript

  routingService.getDAppNameFromRoutePath('#/dashboard.evan/favorites.evan') // => 'favorites'




--------------------------------------------------------------------------------

.. _document_getDAppNameFromCurrRoutePath:

getDAppNameFromCurrRoutePath
================================================================================

.. code-block:: typescript

  routingService.getDAppNameFromCurrRoutePath();

Get the DApp name from an route

-------
Returns
-------

``string``: dapp name from current route

-------
Example
-------

.. code-block:: typescript

  // current url: '#/dashboard.evan/favorites.evan'

  routingService.getDAppNameFromCurrRoutePath() // => 'favorites'




--------------------------------------------------------------------------------

.. _document_canNavigateBack:

canNavigateBack
================================================================================

.. code-block:: typescript

  routingService.canNavigateBack();

Returns an Oberservable that updates triggers when a route was changed and returns if a back navigation should be available.

**Don't forget to unsubscribe on component destroy**.
**Have a look at |source route_configuration|_**.

-------
Returns
-------

``Observable`` returns ``boolean``: True if able to navigate back, False otherwise.

-------
Example
-------

.. code-block:: typescript

  // https://dashboard.evan.network/#/dashboard.evan/favorites.evan will return => dashboard
  const subscription = routingService
    .canNavigateBack()
    .subscribe(async (value) => {
      console.log(value);
    });

  ngOnDestroy() {
    subscription();
  }




--------------------------------------------------------------------------------

.. _document_goBack:

goBack
================================================================================

.. code-block:: typescript

  initializedModule.goBack(arguments);

Goes back. If this.navigateBackStatus contains an route string, navigate to this route else trigger location.back().

**Have a look at |source route_configuration|_**.

-------
Example
-------

.. code-block:: typescript

  routingService.goBack();




--------------------------------------------------------------------------------

goToProfile
================================================================================

.. code-block:: typescript

  routingService.goToProfile();

Navigates to the dappprofile relative to the active dashboard.

  => e.g. https://dashboard.evan.network/#/dashboard.evan/profile.evan

-------
Example
-------

.. code-block:: typescript

  routingService.goToProfile();

--------------------------------------------------------------------------------

goToQueue
================================================================================

.. code-block:: typescript

  routingService.goToQueue();

Navigates to the dapp queue relative to the active dashboard

  => e.g. https://dashboard.evan.network/#/dashboard.evan/queue.evan

-------
Example
-------

.. code-block:: typescript

  routingService.goToQueue();


--------------------------------------------------------------------------------

goToMails
================================================================================

.. code-block:: typescript

  routingService.goToMails();

Navigates to the dapp mailbox relative to the active dashboard

  => e.g. https://dashboard.evan.network/#/dashboard.evan/mailbox.evan

-------
Example
-------

.. code-block:: typescript

  routingService.goToMails();


--------------------------------------------------------------------------------

goToLogging
================================================================================

.. code-block:: typescript

  routingService.goToLogging();

Navigates to the dapp logging relative to the active dashboard.

  => e.g. https://dashboard.evan.network/#/dashboard.evan/logging.evan

-------
Example
-------

.. code-block:: typescript

  routingService.goToLogging();


--------------------------------------------------------------------------------

goToDashboard
================================================================================

.. code-block:: typescript

  routingService.goToDashboard();

Navigates to the dapp dashboard relative to the active dashboard

  => e.g. https://dashboard.evan.network/#/dashboard.evan

-------
Example
-------

.. code-block:: typescript

  routingService.goToDashboard();




--------------------------------------------------------------------------------

.. _document_navigate:

navigate
================================================================================

.. code-block:: typescript

  initializedModule.navigate(arguments);

Use special "this.router.navigate" properties

----------
Parameters
----------

#. ``route`` - ``string``: route name to navigate to
#. ``relativeToRoot`` - ``boolean``: navigate relative to current parent route or use only the route string
#. ``queryParams`` - ``any`` (optional): query params that should be applied to the navigated routes(?param1=...&param2=...)

-------
Example
-------

.. code-block:: typescript

  this.routing.navigate(`./${ dapp.ensAddress }`, true);




--------------------------------------------------------------------------------

.. _document_openENS:

openENS
================================================================================

.. code-block:: typescript

  routingService.openENS(ensAddress, relativeTo, queryParams);

Open an ENS path

----------
Parameters
----------

#. ``ensAddress`` - ``string``: ENS Address to open
#. ``relativeTo`` - ``string``: get the route with the specific name and use the ensAddress relative to the specified route
#. ``queryParams`` - ``any``: query params that should be applied to the navigated routes(?param1=...&param2=...)

-------
Example
-------

.. code-block:: typescript

  let queryParams = this.getOnboardingQueryParams();

  this.routingService.openENS(
    this.definitions.getEvanENSAddress('onboarding'),
    '',
    queryParams
  );




--------------------------------------------------------------------------------

.. _document_getDataParam:

getDataParam
================================================================================

.. code-block:: typescript

  routingService.getDataParam(param);

Get a parameter value from the current active route.

----------
Parameters
----------

#. ``param`` - ``string``: Parameter to get from the current route state.

-------
Returns
-------

``any``: data parameter value

-------
Example
-------

.. code-block:: typescript

  // current route configuration
  // [
  //   {
  //     path: '',
  //     component: DAppListComponent,
  //     data: {
  //       state: 'dapplist'
  //     }
  //   }
  // ]

  routingService.getDataParam('state') // => dapplist




--------------------------------------------------------------------------------

.. _document_getHashParam:

getHashParam
================================================================================

.. code-block:: typescript

  getHashParam.getHashParam(param);

Returns an parameter from the current route or it's children

----------
Parameters
----------

#. ``param`` - ``any``: param key

-------
Returns
-------

``any``: hash parameter value

-------
Example
-------

.. code-block:: typescript

  // {
  //   path: ':address',
  //   component: TaskDetailComponent,
  //   data: {
  //     state: 'task-detail',
  //     navigateBack : true,
  //     reload: [ 'contracts' ]
  //   },
  // }

  // on url "https://dashboard.evan.network/#/taskboard.evan/0x280a9e533b6EF9e6B96aa35DEBA35A1A012B1e1c"

  routingService.getHashParam('address') // => '0x280a9e533b6EF9e6B96aa35DEBA35A1A012B1e1c'




--------------------------------------------------------------------------------

.. _document_getQueryparams:

getQueryparams
================================================================================

.. code-block:: typescript

  routingService.getQueryparams();

Return all query params as object.

-------
Returns
-------

``any``: deep copy of the current query params

-------
Example
-------

.. code-block:: typescript

  // on url https://dashboard.evan.network/#/dashboard.evan?param1=qwe&param2=asd

  routingService.getQueryParams() // => { param1: 'qwe', param2: 'asd' }




--------------------------------------------------------------------------------

.. _document_getRouteConfigParam:

getRouteConfigParam
================================================================================

.. code-block:: typescript

  routingSErvice.getRouteConfigParam(param);

Get a data parameter value from the current active route. (similar to getDataParam, but only for getActiveRoot())

----------
Parameters
----------

#. ``string`` - ``param``: Parameter to get from the current route state.

-------
Returns
-------

``any``: The root route configuration parameter.

-------
Example
-------

Have a look at `getDataParam <../services/ui/routing.html#getdataparam>`_.




--------------------------------------------------------------------------------

.. _document_reloadCurrentContent:

reloadCurrentContent
================================================================================

.. code-block:: typescript

  routingService.reloadCurrentContent();

Triggers an loading of the current split pane content. (navigates to `evan-reload route <../additional/routes-builder.html>`_)

-------
Example
-------

.. code-block:: typescript

  routingService.reloadCurrentContent();




--------------------------------------------------------------------------------

.. _document_windowLocationReload:

windowLocationReload
================================================================================

.. code-block:: typescript

  routingService.windowLocationReload();

window.location.reload(); wrapper

-------
Example
-------

.. code-block:: typescript

  routingService.windowLocationReload();




--------------------------------------------------------------------------------

.. _document_subscribeRouteChange:

subscribeRouteChange
================================================================================

.. code-block:: typescript

  routingService.subscribeRouteChange(callback);

Register for an route change event.

**Don't forget to unsubscribe on component destroy**.

----------
Parameters
----------

#. ``callback`` - ``Function``: Function to call if an route change ends

-------
Returns
-------

``Function``: function to unsubscribe

-------
Example
-------

.. code-block:: typescript

  const subscription = routingService.subscribeRouteChange(() => console.log('navigated!'))

  ngOnDestroy() {
    subscription();
  }




--------------------------------------------------------------------------------

.. _document_onceNavigated:

onceNavigated
================================================================================

.. code-block:: typescript

  routingService.onceNavigated(arguments);

Watching one time for a route change.

-------
Returns
-------

``Observable`` returns ``void``: called on after the first route change

-------
Example
-------

.. code-block:: typescript

  routingService
    .onceNavigated()
    subscribe(() => console.log('navigated'));




--------------------------------------------------------------------------------

.. _document_getActiveRootEns:

getActiveRootEns
================================================================================

.. code-block:: typescript

  routingService.getActiveRootEns();

Return the current active route ENS (if no one is opened, it returns `routing.defaultDAppENS <../../../dapp-browser/routing.html#getdefaultdappns>`_)

-------
Returns
-------
https://.../dashboard.evan/dapp1.evan/dapp2.evan => dashboard.evan

``string``: The active root ens.

-------
Example
-------

.. code-block:: typescript

  routing.getActiveRootEns();




--------------------------------------------------------------------------------

.. _document_getContractAddress:

getContractAddress
================================================================================

.. code-block:: typescript

  .getContractAddress(arguments);

return this.getHashParam('address') or Split the current url hash and return the latest path.


-------
Returns
-------

``string``: The stand alone contract identifier.

-------
Example
-------

.. code-block:: typescript

  // https://dashboard.evan.network/#/taskboard.evan/0x280a9e533b6EF9e6B96aa35DEBA35A1A012B1e1c
  // https://dashboard.evan.network/#/taskboard.evan/0x280a9e533b6EF9e6B96aa35DEBA35A1A012B1e1c/edit-contract
  getContractAddress() // will return 0x280a9e533b6EF9e6B96aa35DEBA35A1A012B1e1c, even when the ":address" parameter within the path is not defined


--------------------------------------------------------------------------------

.. _document_forceUrlNavigation:

forceUrlNavigation
================================================================================

.. code-block:: typescript

  routingService.forceUrlNavigation(hash);

Uses an hash value and replaces the current hash with the new one. But it will use href = to force
parent dapp router handling, if we only set the hash, the navigation will stuck within the current
child DApp.

e.g. dashboard/favorites goes back to dashboard with empty history stack but nothing will happen
because the favorites capured the navigation event and stops bubbling

----------
Parameters
----------

#. ``hash`` - ``string``: new window.location.hash value


-------
Example
-------

.. code-block:: typescript

  this.forceUrlNavigation('dashboard.evan');


.. |source route_configuration| replace:: ``RouteConfiguration``
.. _source route_configuration: /angular-core/additionals/routes-builder.html


