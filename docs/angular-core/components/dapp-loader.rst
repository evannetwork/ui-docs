===================
DAppLoaderComponent
===================
Dynamic DApp loader component. Handles nested Angular DApps and loads the latest ens address within the url.

The following url will start the following dapps:

- http://localhost:3000/dev.html#/dashboard.evan/favorites.evan 
- dashboard.evan
  
  - favorites.evan

-------
Example
-------
Reference Implementation: `Dashboard DApp <https://github.com/evannetwork/core-dapps/blob/develop/dapps/dashboard/src/index.ts>`_

- within routes configuration, Example as wildcard route for dynamic DApp registering:

.. code-block:: typescript

  const routes: Routes = [
  ...,
  {
     path: '**',
     component: DAppLoaderComponent,
     data: {
       state: 'unkown',
       navigateBack: true
     }
   }
   ...

- within html:

::

  <evan-dapp-loader></evan-dapp-loader>

