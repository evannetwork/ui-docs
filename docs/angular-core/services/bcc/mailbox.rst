==================
EvanMailboxService
==================

`Blockchain core description <https://github.com/evannetwork/api-blockchain-core/blob/develop/docs/blockchain/description.rst>`_ class wrapper.

- ``mails`` - ``object[]``: all mail cache;
- ``newMailCount`` - ``number`` (default = 0): newly received mail count;
- ``readMails`` - ``Array<string>``: all mails that were already viewed (cached into local storage);
- ``receivedMails`` - ``object[]``: received mail cache;
- ``sendMailQueueId`` - |source queueId|_: queue id to handle mail sending;
- ``sentMails`` - object[]: send mail cache;
- ``totalReceivedMailCount`` - ``number``: total received mail count;
- ``totalSentMailCount`` - ``number``: total sent mail count;

.. |source queueId| replace:: ``qr-code-scanner module``
.. _source queueId: /angular-core/services/bcc/queue-utilities.html#queueid




--------------------------------------------------------------------------------

.. _document_checkNewMails:

checkNewMails
================================================================================

.. code-block:: typescript

  mailboxService.checkNewMails();

Check for new mails and set the newMails property to false / true when new mails incoming

-------
Returns
-------

``Promise`` returns ``void``: resolved when done

-------
Example
-------

.. code-block:: typescript

  setInterval(() => this.mailboxService.checkNewMails());




--------------------------------------------------------------------------------

getReadMails
================================================================================

.. code-block:: typescript

  mailboxService.getReadMails();

Check read mails within localStorage cache and return them.

-------
Returns
-------

``Array<string>``: readed mails from localStorage

-------
Example
-------

.. code-block:: typescript

  this.mailboxService.getReadMails() // [ '0x00...', '0x100...' ]

--------------------------------------------------------------------------------

getReadMailsCount
================================================================================

.. code-block:: typescript

  mailboxService.getReadMailsCount();

Get read mail count

-------
Returns
-------

``number``: count of read mails

-------
Example
-------

.. code-block:: typescript

  this.mailboxService.getReadMailsCount()




--------------------------------------------------------------------------------

.. _document_addReadMails:

addReadMails
================================================================================

.. code-block:: typescript

  mailboxService.addReadMails(mailId);

Add a mail id to the mail read array within the localStorage

----------
Parameters
----------

#. ``mailId`` - ``string``: mail id

-------
Example
-------

.. code-block:: typescript

  this.mailboxService.addReadMails(mail.address || '0x00');





--------------------------------------------------------------------------------

.. _document_syncLastReadCount:

syncLastReadCount
================================================================================

.. code-block:: typescript

  mailboxService.syncLastReadCount();

Check for new mails and update the last read mail count


-------
Example
-------

.. code-block:: typescript

  this.mailboxService.syncLastReadCount();

--------------------------------------------------------------------------------

.. _document_showMailModal:

showMailModal
================================================================================

.. code-block:: typescript

  mailboxService.showMailModal(modalService, alertTitle, alertText, title, body);

Show a mail modal, to provide the user the possility to change the email text before sending.

Have a look at `MailDialogComponent <../components/mail-dialog.html>`_

----------
Parameters
----------

#. ``modalService`` - ``string``: modal service (must to be inclued, to prevent recursive services)
#. ``alertTitle`` - ``string``: title of the modal
#. ``alertText`` - ``string``: sub text of the modal
#. ``title`` - ``string``: title text of the mail
#. ``body`` - ``string``: body text of the mail

-------
Returns
-------

``Promise`` returns ``any``: adjusted mail result

-------
Example
-------

.. code-block:: typescript

 await this.mailboxService
  .showMailModal(
    this.modalService,
    '_dappcontacts.invitation-message',
    '_dappcontacts.invitation-message-long',
    '_dappcontacts.invitation-text.title',
    '_dappcontacts.invitation-text.body',
  );




--------------------------------------------------------------------------------

.. _document_raiseMailLoadCount:

raiseMailLoadCount
================================================================================

.. code-block:: typescript

  mailboxService.raiseMailLoadCount(raise, type);

Increase the mail count for a specific type

----------
Parameters
----------

#. ``raise`` - ``number``: number to raise the mail count with
#. ``type`` - ``string``: sent / received

-------
Example
-------

.. code-block:: typescript

  raiseMailLoadCount(3, 'sent')




--------------------------------------------------------------------------------

.. _document_getMails:

getMails
================================================================================

.. code-block:: typescript

  mailboxService.getMails();

Load the mails for the current account.

----------
Parameters
----------

#. ``options`` - ``object``: The options used for calling
    * ``from`` - ``string`` (optional): The address the call "transaction" should be made from
#. ``callback`` - ``Function`` (optional): This callback will be fired..
#. ``somethingElse`` - ``string`` (optional): this can be set if required, defaults to ``"latest"``

-------
Returns
-------

``Promise`` returns ``void``: resolved when done

.. code-block:: typescript

  {
    receivedMails: [ this.getMail() ],
    sentMails: [ ... ]
  }

-------
Example
-------

.. code-block:: typescript

  await mailboxService.getMails();




--------------------------------------------------------------------------------

.. _document_getMail:

getMail
================================================================================

.. code-block:: typescript

  mailboxService.getMail(mailId);

Get a mail with a mail id.

----------
Parameters
----------

#. ``mailId`` - ``string``: TThe mail identifier

-------
Returns
-------

``Promise`` returns ``any``: return the mail

.. code-block:: typescript

  {
    "id": "0x00000000000000000000000000000000000000fa",
    "content": {
      "from": "0xe70dfbc43369DE771d357fA4a6559be2eF16772f",
      "fromAlias": "Another user",
      "title": "contact request",
      "body": "hello,\n\ni want to add you as a contact.\n\nWith kind regards,\n\nAnother user",
      "attachments": [
        {
          "type": "commKey",
          "key": "9430..."
        }
      ],
      "sent": 1526626132635,
      "to": "0xCCC..."
    },
    "cryptoInfo": {
      "originator": "0xd926...",
      "keyLength": 256,
      "algorithm": "aes-256-cbc"
    }
  }

-------
Example
-------

.. code-block:: typescript

  const mail = this.mailboxService.getMail('0x00')




--------------------------------------------------------------------------------

.. _document_sendAnswer:

sendAnswer
================================================================================

.. code-block:: typescript

  mailboxService.sendAnswer(mail, from, to);

Send an mail answer, using the queue.

----------
Parameters
----------

#. ``mail`` - ``string``: mail object
#. ``from`` - ``string``: account id from
#. ``to`` - ``string``: to account id

-------
Returns
-------

``Promise`` returns ``void``: resolved when done

-------
Example
-------

.. code-block:: typescript

  this.mailboxService.sendAnswer({
    parentId: this.mailId,
    content: {
      sent: new Date().getTime(),
      from: this.myAccountId,
      to: this.mail.content.from,
      title: this.mail.content.title,
      body: this.answer,
    }
  }, '0x000', '0x001')