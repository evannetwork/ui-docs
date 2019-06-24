==============
routes-builder
==============

.. list-table:: 
   :widths: auto
   :stub-columns: 1

   * - Source
     - `routes-builder <https://github.com/evannetwork/ui-angular-core/blob/develop/src/classes/routesBuilder.ts>`__

The routes builder is a collection of functions that handles dynamic and nested routing handling, including the default evan.network dapp routes (profile, favorites, addressbook, mailbox, queue, logging).


--------------------------------------------------------------------------------

.. _angular_core_routes_builder_getDashboardRoutes:

getDashboardRoutes
================================================================================

.. code-block:: typescript

  getDashboardRoutes(routes, enableBack);

Merges input routes with the default dashboard routes.

----------
Parameters
----------

#. ``routes`` - ``Routes``: Angular routes of the module
#. ``enableBack`` - ``boolean`` (optional): enable go back button within dapp-wrapper for dashboard routes

-------
Returns
-------

``Routes``: merged routes

-------
Example
-------

Used within buildModuleRoutes function

.. code-block:: typescript

  const enhancedRoutes = [ ].concat(getDashboardRoutes(routes, true));

--------------------------------------------------------------------------------

.. _angular_core_routes_builder_buildModuleRoutes:

buildModuleRoutes
================================================================================

.. code-block:: typescript

  buildModuleRoutes(dappEns, CoreComponent, routes);

Builds evan.network framework nested Angular DApp routes

 - including core dapps (profile, favorites, addressbook, mailbox, queue, logging)
 - multiple root route handling

   - #/dappEns/asdf
   - #/dashboard.evan/dappEns/asdf
   - #/dashboard.evan/dappEns/0x00...
   - #/dashboard.evan/0x00/...

Routes can include the following properties, that enhance the route capabilities:

.. code-block:: typescript

  data: {
    // used for routing transitions
    //   <dapp-wrapper *ngIf="!loading" #dappWrapper>
    //     <div evan-content [@routerTransition]="o?.activatedRouteData?.state">
    //       <router-outlet #o="outlet"></router-outlet>
    //     </div>
    //   </dapp-wrapper>
    state: 'task-detail',
    
    // enables navigates back for dapp-wrapper component
    navigateBack : true,
    
    // enables reload property within dapp-wrapper
    reload: [ 'contracts' ],
    
    // trigger route reset after DApp was loaded within the bootstrap-component
    evanDynamicRoutes: true
  }

----------
Parameters
----------

#. ``dappEns`` - ``string``: ens address of the dapp
#. ``CoreComponent`` - ``Component``: root routing component of the application
#. ``routes`` - ``Routes``: routing Tree

-------
Returns
-------

``Routes``: full routing tree

-------
Example
-------

.. code-block:: typescript

  function getRoutes(): Routes {
    return buildModuleRoutes(
      `dashboard.${ getDomainName() }`,
      DashboardComponent,
      [
        {
          path: '',
          redirectTo: `favorites.${getDomainName()}`,
          pathMatch: 'full'
        },
        {
          path: '**',
          component: DAppLoaderComponent,
          data: {
            state: 'unkown',
            navigateBack: true
          }
        }
      ]
    );
  }

  ...

  @NgModule({
    ...
    imports: [
      ...
      RouterModule.forRoot(getRoutes(), { enableTracing: false, })
    ],
    ...
  })
  class SampleModule {
    constructor() { }
  }
