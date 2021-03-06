========================
EvanDAppWrapperComponent
========================

.. list-table:: 
   :widths: auto
   :stub-columns: 1

   * - Source
     - `dapp-wrapper <https://github.com/evannetwork/ui-angular-core/blob/develop/src/components/dapp-wrapper>`__

top-bar wrapper for DApps that enables:

- back navigation
- url routing has as title (dynamic)
- mailbox alerts
- queue status

Back navigation is configured within the routes data object. Have a look at `routesbuilder buildModule routes <http://localhost:8000/angular-core/additionals/routes-builder.html#buildmoduleroutes>`_.

------
Outpus
------

#. ``refreshing`` - ``EventEmitter<any>``: Emitted when the routing data refresh property is set and the reload button is clicked, so the parent module can reload the current component content.

-------
Example
-------
Reference Implementation: `Favorites DApp root component <https://github.com/evannetwork/ui-core-dapps/blob/develop/dapps/favorites/src/components/root/root.html>`_

Use the *evan-content* attribute to specify, which html data should be displayed within the wrapper.

::

  <evan-loading *ngIf="loading" delayLoading="500"></evan-loading>
  <dapp-wrapper *ngIf="!loading" #dappWrapper>
    <div evan-content [@routerTransition]="o?.activatedRouteData?.state">
      <router-outlet #o="outlet"></router-outlet>
    </div>
  </dapp-wrapper>

------------
View Example
------------

.. image:: ../../../images/angular-core/components/dapp-wrapper.png
   :width: 600