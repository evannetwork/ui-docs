=======
routing
=======

The `routing library <https://github.com/evannetwork/ui-dapp-browser/blob/develop/src/app/routing.ts>`_ is a small routing library that handles top level DApp navigation. To be small as possible, it uses the `navigo routing <https://github.com/krasimir/navigo>`_ as helper library.

- On first loading, it checks a logged in user and in case of an unregistered user, it redirectes the browser to the onboarding DApp.
- It watches dynamically on route changes to trigger a new `dapp.startDApp </dapp-browser/dapp.html#startdapp>`_ call when the root dapp hash changed.
- Sub DApp routing must be handled by DApps it self.

  - |source angular_core_routes_builder|_
  - |source sample_route_dynamic_config|_

.. |source angular_core_routes_builder| replace:: ``angular core routes builder``
.. _source angular_core_routes_builder: /angular-core/custom/routes-builder.html

.. |source sample_route_dynamic_config| replace:: ``angular sample dynamic & nested routes configuration``
.. _source sample_route_dynamic_config: https://github.com/evannetwork/ui-core-dapps/blob/master/dapps/dashboard/src/index.ts





--------------------------------------------------------------------------------

.. _db_routing_goToOnboarding:

goToOnboarding
================================================================================

.. code-block:: typescript

  routing.goToOnboarding();

Go to onboarding. (#/onboarding.evan)

--------------------------------------------------------------------------------

.. _db_routing_goToDashboard:

goToDashboard
================================================================================

.. code-block:: typescript

  routing.goToDashboard(arguments);

Go to dashboard.  (#/dashboard.evan)

--------------------------------------------------------------------------------

.. _db_routing_isOnboarding:

isOnboarding
================================================================================

.. code-block:: typescript

  routing.isOnboarding(arguments);

Determines if the user is on the onboarding page.

-------
Returns
-------

``boolean`` : True if onboarding, False otherwise. (when url includes /onboarding.domainName)




--------------------------------------------------------------------------------

.. _db_routing_getActiveRootENS:

getActiveRootENS
================================================================================

.. code-block:: typescript

  routing.getActiveRootENS();

Gets the active root ens.


-------
Returns
-------

``string``: The active root ens.

-------
Example
-------

.. code-block:: typescript

  // http://localhost:3000/index.html#/dashboard.evan/favorites.evan
  routing.getActiveRootENS()
  // result: dashboard.evan




--------------------------------------------------------------------------------

.. _db_routing_getDefaultDAppENS:

getDefaultDAppENS
================================================================================

.. code-block:: typescript

  routing.getDefaultDAppENS();

Gets the default root DApp ens (mapped to the \*.evan.network prefix). Default is dasboard.evan.

-------
Returns
-------

``Promise`` returns ``string``: default DApp ens path

-------
Example
-------

.. code-block:: typescript

  routing.getDefaultDAppENS()

http://localhost:3000/index.html => dashboard.evan
http://taskboard.evan.network/index.html => taskboard.evan
http://customer.evan.network/index.html => customer.evan




--------------------------------------------------------------------------------

.. _db_routing_beforeRoute:

beforeRoute
================================================================================

.. code-block:: typescript

  routing.beforeRoute();

Prerouting checks to handle if the user was logged in and onboared. Navigates to onboarding / default dapp ens when necessary.

-------
Returns
-------

``Promise`` returns ``void``: resolved when done




--------------------------------------------------------------------------------

.. _db_routing_onRouteChange:

onRouteChange
================================================================================

.. code-block:: typescript

  routing.onRouteChange();

Function to check if the route DApp hash changed => run beforeRoute and set the route active. Start DApp when root DApp changed

-------
Returns
-------

``Promise`` returns ``void``: resolved when done




--------------------------------------------------------------------------------

.. _db_routing_initialize:

initialize
================================================================================

.. code-block:: typescript

  routing.initialize();

Initialize the whole routing mechanism. Starts navigo, and runs initial route change for default route detection and dapp loading.

-------
Returns
-------

``Promise`` returns ``void``: resolved when done




--------------------------------------------------------------------------------

.. _db_routing_getRouteFromUrl:

getRouteFromUrl
================================================================================

.. code-block:: typescript

  routing.getRouteFromUrl();

Takes the current url, removes #, /#, #/ and returns the original hash value without query params.

-------
Returns
-------

``string``: transforms #/dapp/dapp1?param1=est to dapp/dapps

--------------------------------------------------------------------------------

.. _db_routing_history:

history
================================================================================

.. code-block:: typescript

  routing.history.push('dashboard.evan/favorites.evan');

The current navigation stack and includes every route that is opened from apps to handle a specific
and logical go back function. Each application should implement an navigate function that pushes into this history array.

**Important: Need to be filled by the application it self!!!**

--------------------------------------------------------------------------------

.. _db_routing_updateHistory:

updateHistory
================================================================================

.. code-block:: typescript

  routing.updateHistory();

Takes the current navigation history and writes it to the sessionStorage if the user navigates to another page and navigates back
