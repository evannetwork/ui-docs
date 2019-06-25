============================
QRCodeScannerDialogComponent
============================

.. list-table:: 
   :widths: auto
   :stub-columns: 1

   * - Source
     - `qr-code-scanner <https://github.com/evannetwork/ui-angular-core/blob/develop/src/components/qr-code-scanner>`__

Shows an QR-Code Scanner Dialog for HTML 5. Should only be used within a modal.

-------
Example
-------
Reference Implementation: `EvanQrCodeService <https://github.com/evannetwork/ui-angular-core/blob/develop/src/services/ui/qr-code.ts>`_

- typescript

.. code-block:: typescript

  const qrCodeValue = await this.modalService.createModal(QRCodeScannerDialogComponent, {});

------------
View Example
------------

.. image:: ../../../images/angular-core/components/qr-code-scanner.png
   :width: 600