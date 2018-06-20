=======================
GlobalPasswordComponent
=======================

The `lightwallet </dapp-browser/lightwallet.html#setpasswordfunction>`_ vault unlocking function need the users password to encrypt the locally saved vault, to interact with the blockchain. This component provides the functionality to interact with the user, check if the password is correct and returns the provided password. The Global password component is used within each Angular DApp. Will be registered in the root.ts in each evan.network featured DApp. Unlocks the current users profile. Should only be used using the modal service!

It can be used as reference implementation for custom global password dialogs.

-----
Usage
-----
Reference Implementation: `reference </angular/core/components/big-picture.rst>`_

- typescript

.. code-block:: typescript

  import {
    EvanCoreService,
    EvanBCCService,
  } from 'angular-core';

  constructor(
    private core: EvanCoreService,
    private bcc: EvanBCCService,
  ) { }

  ngOnInit() {
    await this.bcc.initialize((accountId) => this.bcc.globalPasswordDialog(this.core.activeAccount()));
  }

-----------
View Sample
-----------

.. image:: /images/angular-core/components/global-password.png
   :width: 600