=========================
EmptyDAppDisplayComponent
=========================
Shows an generalized "Theirs no data." screen using DApp DBCP descriptions 

------
Inputs
------

#. ``ensAddress`` - ``string``: ens address to load the empty preview img from
#. ``text`` - ``string``: text to display under neath the window
#. ``img`` - ``string``: apply dynamic applied img, overwrites ensAddress img

------
Outpus
------

#. ``param`` - ``string``: 

-----
Usage
-----
Reference Implementation: `Favorites DApp <https://github.com/evannetwork/core-dapps/blob/develop/dapps/favorites/src/components/dapp-list/dapp-list.html>`_

- html

::

  <evan-empty-dapp
    *ngIf="dappKeys.length === 0"
    [text]="filterString ? ('_dappdapps.nothing-found' | translate:{ filter: filterString }) : '_dappdapps.empty-bookmarks'"
    ensAddress="favorites">
  </evan-empty-dapp>

-----------
View Sample
-----------

.. image:: /images/angular-core/components/empty-dapp-display.png
   :width: 600