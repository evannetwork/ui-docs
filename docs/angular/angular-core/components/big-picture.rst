================
BigPictureDialog
================

.. list-table:: 
   :widths: auto
   :stub-columns: 1

   * - Source
     - `big-picture <https://github.com/evannetwork/ui-angular-core/blob/develop/src/components/big-picture>`__

Takes an img url and shows an image on fullscreen (optimized for modal dialogs).
The dataUrl can be anything that can display an img:
  
- http / https url
- base64 img code
- data url (blob:http://localhost:...)

To take pictures during application runtime have a look at the `EvanPictureService <../services/ui/picture.html>`_ or `SnapshotDialogComponent <../components/take-snapshot.html>`_.

-------
Example
-------
Reference Implementation: `Task DApp detail <https://github.com/evannetwork/ui-core-dapps/blob/develop/dapps/task/src/components/detail>`_

- typescript

.. code-block:: typescript

  openPictureDetail(dataUrl: string) {
    try {
      return this.modalService.showBigPicture(
        'alertTitle',
        'alertText',
        dataUrl,
      );
    } catch (ex) { }
  }

- html

::

  <img class="clickable"
    [src]="picture.blobURI"
    (click)="openPictureDetail(picture.blobURI)"
  />

Havea look at the `EvanModalService <../services/ui/modal.html#showbigpicture>`_. 

------------
View Example
------------

.. image:: ../../../images/angular-core/components/big-picture.png
   :width: 600