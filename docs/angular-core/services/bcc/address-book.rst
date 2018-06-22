======================
EvanAddressBookService
======================

BCC addressbook wrapper

- ``queueId`` - |source queueId|_: Address book sync queue id
- ``current`` - any: latest loaded address book data (object result from `loadAccounts <../services/bcc/address-book.html#loadaccounts>`_)

.. |source queueId| replace:: ``qr-code-scanner module``
.. _source queueId: /angular-core/services/bcc/queue-utilities.html#queueid




--------------------------------------------------------------------------------

loadAccounts
================================================================================

.. code-block:: typescript

  addressBookService.loadAccounts(arguments);

Load the accounts from the address book from the blockchain and from the queue.

-------
Returns
-------

``Promise`` returns ``any``: addressbok data

.. code-block:: typescript

  {
    // sharing keys
    "keys": {
      "0xd1fa932fa69a55fde0d943b1bff79a31e6dc943263697068711570adb652c409": {
        "dataKey": "f5510ce31283edef95aeeccae3589cf60b35882e71c741636d5d64c4953b7e89"
      },
      "0x1d84ab8f4f7b90d837bd2dea56ac559706d1e918f9fe0e85e7b2042a6a7e8ece": {
        "commKey": "de6aa299ecabb7508cc6a64f295a1c493200f5cd22bbac10efed409188a616ec"
      }
    },
    "profile": {
      "0x1813587e095cDdfd174DdB595372Cb738AA2753A": {
        "alias": "My Account Alias"
      },
      "0x1637Fa43D44a1Fb415D858a3cf4F7F8596A4048F": {
        "alias": "My buddy"
      }
    },
    "0x1813587e095cDdfd174DdB595372Cb738AA2753A": {
      "alias": "My account Alias"
    },
    "0x1637Fa43D44a1Fb415D858a3cf4F7F8596A4048F": {
      "alias": "My buddy"
    }
  }

-------
Example
-------

.. code-block:: typescript

  this.contacts = await this.addressBook.loadAccounts();




--------------------------------------------------------------------------------

loadAccount
================================================================================

.. code-block:: typescript

  addressBookService.loadAccount(accountId);

Loads an account ids address book entry

----------
Parameters
----------

#. ``accountId`` - ``string``: account id to get the entry for

-------
Returns
-------

``Promise`` returns ``string``: addressbook data

-------
Example
-------

.. code-block:: typescript

  this.singleContact = await this.addressBook.loadAccount('0x000');




--------------------------------------------------------------------------------

addContactToQueue
================================================================================

.. code-block:: typescript

  initializedModule.addContactToQueue(arguments);

Save an contact to the address book queue and sets a locally saved contact type 'add' property, so the ui can display it as "adding"

----------
Parameters
----------

#. ``accountId`` - ``string``: account id to add
#. ``contact`` - ``any``: Contact object (accountId, alias, email address)

-------
Example
-------

.. code-block:: typescript

  this.addressBookService.addContactToQueue('0x00...', {
    "isCreate": true,
    "profile": {
       "alias": "Test account",
       "accountId": "0xf2009Fc431B326469005bB13370F1df67Ad852e9"
     },
     "mail": {
       "fromAlias": "My Account Alias",
       "title": "Contact request",
       "body": "Hi,\n\nI'd like to add you as a contact. Do you accept my invitation?\n\nWith kind regards,\n\nMy Account Alias"
    },
  });




--------------------------------------------------------------------------------

addRemoveContactToQueue
================================================================================

.. code-block:: typescript

  addressBookService.addRemoveContactToQueue(accountId, contact);

Remove an contact from the address book queue and sets a locally saved contact type 'remove' property, so the ui can display it as "removing"

----------
Parameters
----------

#. ``accountId`` - ``string``: account id to remove
#. ``contact`` - ``any``: Contact object (accountId, alias, email address)

-------
Example
-------

.. code-block:: typescript

  this.addressBookService.addRemoveContactToQueue(this.accountId, {
    email: "..."
  });




--------------------------------------------------------------------------------

saveContactToQueue
================================================================================

.. code-block:: typescript

  addressBookService.saveContactToQueue(contact);

Add an contact including type property to the queue. 

----------
Parameters
----------

#. ``contact`` - ``any``: Contact object (accountId, alias, email address) including type property

-------
Example
-------

For usage have a look at "addContactToQueue".



--------------------------------------------------------------------------------

activeUserName
================================================================================

.. code-block:: typescript

  addressBookService.activeUserName(disableNoAlias);

Get the current configured user name.

----------
Parameters
----------

#. ``disableNoAlias`` - ``boolean`` (optional): disable empty alis filling

-------
Returns
-------

``Promise`` returns ``string``: users alias

