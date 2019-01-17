============================
EvanIdentityMissingComponent
============================

.. list-table:: 
   :widths: auto
   :stub-columns: 1

   * - Source
     - `EvanIdentityMissingComponent <https://github.com/evannetwork/ui-core-dapps/tree/develop/dapps/claims/src/components/identity-missing>`__
     
Used to check if the identity for the current logged in user exists, if not, it will enable a functionality, to create a new identity.

-------
Example
-------
Reference Implementation: `EvanVerificationsOverviewComponent <https://github.com/evannetwork/ui-core-dapps/tree/develop/dapps/claims/src/components/claims>`__

- html

::

  this.identityExists = await this.bcc.claims.identityAvailable(this.core.activeAccount());

- typescript

::

  <evan-identity-missing *ngIf="!identityExists"></evan-identity-missing>

