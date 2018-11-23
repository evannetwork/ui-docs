===================
EvanReloadComponent
===================

.. list-table:: 
   :widths: auto
   :stub-columns: 1

   * - Source
     - `reload-route <https://github.com/evannetwork/ui-angular-core/blob/develop/src/components/reload-route>`__

Is used to hardly reload an route. The user gets navigate to this route and it will navigate back after 500 milliseconds.

------
Inputs
------

#. ``param`` - ``string``: 

------
Outpus
------

#. ``param`` - ``string``: 

-------
Example
-------
Reference Implementation: `RoutesBuilder <https://github.com/evannetwork/ui-angular-core/blob/develop/src/components/routesBuilder.ts>`_

Example within routesBuilder dashboardRoutes:

- typescript

.. code-block:: typescript

  const routes: Routes = [ ...
    {
      path: `evan-reload`,
      component: EvanReloadComponent,
      data: {
        navigateBack : true
      }
    }
  ]
  
