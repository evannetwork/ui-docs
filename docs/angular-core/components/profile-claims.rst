==========================
EvanProfileClaimsComponent
==========================

.. list-table:: 
   :widths: auto
   :stub-columns: 1

   * - Source
     - `profile-claims <https://github.com/evannetwork/ui-angular-core/blob/develop/src/components/profile-claims>`__

Display all for the user configured active claims for a specific topic. (they can be configured using the `Claims Service <../../angular-core/services/bcc/claims.html>`_, `BCC profile API <https://github.com/evannetwork/api-blockchain-core/blob/develop/src/profile/profile.ts>`_, `Profile DApp <https://evannetwork.github.io/dapps/dapps/profile/profile>`_)

------
Inputs
------
#. ``address`` - ``string``: address that for that the claims should be checked
#. ``mode`` - ``string``: display mode that should be used (minimal, detail, full)

-------
Example
-------
Reference Implementation: `Mail Detail Component <https://github.com/evannetwork/ui-core-dapps/tree/develop/dapps/mailbox/src/components/mail-detail>`_

::

  <evan-profile-claims
    [address]="'0x1291781...'"
    [mode]="'icon'">
  </evan-profile-claims>

------------
View Example
------------

Have a look at the claims component `Claims Component <https://evannetwork.github.io/dapps/angular/hello-world>`_