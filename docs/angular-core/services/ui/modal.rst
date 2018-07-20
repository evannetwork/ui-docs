================
EvanModalService
================

Service that handles components within modals.

--------------------------------------------------------------------------------

.. _document_createModal:

createModal
================================================================================

.. code-block:: typescript

  modalService.createModal(arguments);

Creates a modal using an component.

----------
Parameters
----------

#. ``component`` - ``Component``: component to show in the modal
#. ``payload`` - ``any``: payload that should be applied to the component[this]
#. ``evanModalAnimation`` - ``boolean``: a modal dialog that uses .evan-modal internally

-------
Returns
-------

``Promise`` returns ``any``: modal that is resolved on modal reject / resolve

---------
Component
---------
Each component that is used within this service needs to be added to your modals "entryComponents". The `AngularCore module <../modules/angular-core.html>`_ specifies the following components that can be used by default of your application: 

- |source MailDialogComponent|_
- |source GlobalPasswordComponent|_
- |source TrustDialogComponent|_
- |source SnapshotDialogComponent|_
- |source QRCodeScannerDialogComponent|_
- |source BigPictureDialog|_

Each component instance gets the following parameters applied, after it was created:

- ``resolveDialog`` - ``Function``: Function to close the modal and resolves the promise as successfull 
- ``rejectDialog`` - ``Function``: Function to close the modal and rejects the promise as an error

In addition, all parameters and their values are transferred from the payload object to the component instance.

-------
Example
-------
Reference Implementation:

- fullscreen modal component |source GlobalPasswordComponent|_
- fullscreen modal component |source GlobalPasswordComponent|_
- modal style component |source MailDialogComponent|_ 


.. code-block:: typescript

  showMailModal(
    modalService: EvanModalService,
    alertTitle: string,
    alertText: string,
    title: string,
    body: string
  ): Promise<any> {
    return modalService.createModal(MailDialogComponent, {
      alertTitle,
      alertText,
      title,
      body
    }, true);
  }

--------------------------------------------------------------------------------

.. _document_showBigPicture:

showBigPicture
================================================================================

.. code-block:: typescript

  modalService.showBigPicture(alertTitle, alertText, img);

Modal wrapper for the angular-core |source BigPictureDialog|_.

----------
Parameters
----------

#. ``alertTitle`` - ``string``: title of the alert
#. ``alertText`` - ``string``: text of the alert
#. ``img`` - ``string``: url / base64 of a img

-------
Returns
-------

``Promise`` returns ``any``: modal that is resolved on modal reject / resolv

-------
Example
-------
Reference Implementation: `Task DApp <https://github.com/evannetwork/ui-core-dapps/blob/master/dapps/task/src/components/detail/detail.ts>`_

.. code-block:: typescript

  try {
    return this.modalService.showBigPicture(
      'alertTitle',
      'alertText',
      dataUrl,
    );
  } catch (ex) { }

.. |source GlobalPasswordComponent| replace:: ``GlobalPasswordComponent``
.. _source GlobalPasswordComponent: /angular-core/components/global-password.html

.. |source MailDialogComponent| replace:: ``MailDialogComponent``
.. _source MailDialogComponent: /angular-core/components/mail-dialog.html

.. |source TrustDialogComponent| replace:: ``TrustDialogComponent Component``
.. _source TrustDialogComponent: /angular-core/components/trust-dialog.html

.. |source SnapshotDialogComponent| replace:: ``SnapshotDialogComponent Component``
.. _source SnapshotDialogComponent: /angular-core/components/snapshot-dialog.html

.. |source QRCodeScannerDialogComponent| replace:: ``QRCodeScannerDialogComponent Component``
.. _source QRCodeScannerDialogComponent: /angular-core/components/qr-code-scanner.html

.. |source BigPictureDialog| replace:: ``BigPictureDialog Component``
.. _source BigPictureDialog: /angular-core/components/big-picture.html

