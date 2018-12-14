==================
EvanClaimComponent
==================

.. list-table:: 
   :widths: auto
   :stub-columns: 1

   * - Source
     - `claim <https://github.com/evannetwork/ui-angular-core/blob/develop/src/components/claim>`__

Display a all claims for a specific topic using the api-blockchain-core claims service.

------
Inputs
------
#. ``address`` - ``string``: address that for that the claims should be checked
#. ``topic`` - ``string``: the topic to load the claims for (/test/test2)
#. ``mode`` - ``string``: display mode that should be used (minimal, detail, full)
#. ``compute`` - ``boolean``: use computed view and only one claim instead of all possible ones (will display a small claim count at the right of the card)
#. ``enableIssue`` - ``boolean``: Are issue buttons are available? Not avaialble for icon mode
#. ``enableDelete`` - ``boolean``: should the delete button be shown?
#. ``enableReject`` - ``boolean``: should the delete button be shown?

-------
Example
-------
Reference Implementation: `Profile Claims Component <https://github.com/evannetwork/ui-angular-core/tree/develop/src/components/profile-claims>`_

::

  <evan-claim
    [topic]="'/test/1234'"
    [address]="'0x1291781...'"
    [mode]="'icon'"
    [compute]="true">
  </evan-claim>

------------
View Example
------------

.. image:: ../../images/angular-core/components/claims/icon.png
   :width: 600

.. image:: ../../images/angular-core/components/claims/normal.png
   :width: 600

.. image:: ../../images/angular-core/components/claims/detail.png
   :width: 600

