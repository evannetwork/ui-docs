==========================
EvanProfileVerificationsComponent
==========================

.. list-table:: 
   :widths: auto
   :stub-columns: 1

   * - Source
     - `profile-verifications <https://github.com/evannetwork/ui-angular-core/blob/develop/src/components/profile-verifications>`__

Display all for the user configured active verifications for a specific topic. (they can be configured using the `Verifications Service <../../angular-core/services/bcc/verifications.html>`_, `BCC profile API <https://github.com/evannetwork/api-blockchain-core/blob/develop/src/profile/profile.ts>`_, `Profile DApp <https://evannetwork.github.io/dapps/dapps/profile/profile>`_)

------
Inputs
------
#. ``address`` - ``string``: address that for that the verifications should be checked
#. ``mode`` - ``string``: display mode that should be used (minimal, detail, full)

-------
Example
-------
Reference Implementation: `Mail Detail Component <https://github.com/evannetwork/ui-core-dapps/tree/develop/dapps/mailbox/src/components/mail-detail>`_

::

  <evan-profile-verifications
    [address]="'0x1291781...'"
    [mode]="'icon'">
  </evan-profile-verifications>

------------
View Example
------------

Have a look at the verifications component `Verifications Component <https://evannetwork.github.io/dapps/angular/hello-world>`_