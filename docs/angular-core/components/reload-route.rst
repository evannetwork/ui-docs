===================
EvanReloadComponent
===================

Is used to hardly reload an route. The user gets navigate to this route and it will navigate back after 500 milliseconds.

------
Inputs
------

#. ``param`` - ``string``: 

------
Outpus
------

#. ``param`` - ``string``: 

-----
Usage
-----
Reference Implementation: `reference <https://github.com/evannetwork/angular-core/blob/develop/src/classes/routesBuilder.ts>`_

Usage within routesBuilder dashboardRoutes:

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
  
