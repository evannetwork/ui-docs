====================
EvanLoadingComponent
====================

Evan network loading img wrapper. Use it for full application loading, its build as a big loading animation

------
Inputs
------

#. ``delayLoading`` - ``string``: milliseconds to delay the loading symbol display (normally the DApp will load within 500ms and their we need no loading icon)
#. ``loadingText`` - ``string``: text that should be displayed during loading

-------
Example
-------
Reference Implementation: `Favorites DApp <https://github.com/evannetwork/core-dapps/blob/develop/dapps/favorites/src/components/dapp-list/dapp-list.html>`_

- html

::

  <evan-loading *ngIf="loading" delayLoading="500"></evan-loading>

  <div *ngIf="!loading"> </div>

------------
View Example
------------

.. image:: /images/angular-core/components/evan-loading.png
   :width: 600