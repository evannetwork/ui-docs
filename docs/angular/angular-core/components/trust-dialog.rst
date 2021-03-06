====================
TrustDialogComponent
====================

.. list-table:: 
   :widths: auto
   :stub-columns: 1

   * - Source
     - `trust-dialog <https://github.com/evannetwork/ui-angular-core/blob/develop/src/components/trust-dialog>`__

Dialog to request user to accept permissions. (should only used within modal)

-------
Example
-------
Reference Implementation: `Contacts Account Create component <https://github.com/evannetwork/ui-core-dapps/blob/develop/dapps/addressbook/src/components/account-create/account-create.ts>`_

- typescript

::

  await this.modalService.createModal(TrustDialogComponent, {
    smartAgentName: 'Onboarding Smart Agent',
    smartAgentRights: [
      'key-exchange',
      'mailbox-send'
    ],
    smartAgentDetails: {
      description: `
        The onboarding Smart Agent gives you the ability, to invite persons via Email and send
        them EVE\'s as seed money. They receive a custom Email with an invite link.
        You get a mailbox message with the onboarded user id and the new alias of the account
      `,
      verifiedBy: 'evan.network',
      verifiedAt: '28.02.2018',
      createdBy: 'evan.network',
      createdAt: '28.02.2018',
    },
    smartAgentAccountId: '0x063fB42cCe4CA5448D69b4418cb89E663E71A139',
    smartAgentTrustFn: async() => {
      const myAccountId = this.core.activeAccount();
      let profile = this.bcc.getProfileForAccount(smartAgentAccountId);

      const targetPubKey = await profile.getPublicKey();
      const commKey = await this.bcc.keyExchange.generateCommKey();
      await this.bcc.keyExchange.sendInvite(smartAgentAccountId, targetPubKey, commKey, {});

      // add key to profile
      await this.bcc.profile.addContactKey(
        smartAgentAccountId,
        'commKey',
        commKey
      );
      await this.bcc.profile.addProfileKey(
        smartAgentAccountId, 'alias', 'Email Smart Agent'
      );

      await this.bcc.profile.storeForAccount(this.bcc.profile.treeLabels.addressBook);
    }
  }, true);

------------
View Example
------------

.. image:: ../../../images/angular-core/components/trust-dialog.png
   :width: 600