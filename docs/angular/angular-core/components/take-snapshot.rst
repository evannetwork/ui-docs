=======================
SnapshotDialogComponent
=======================

.. list-table:: 
   :widths: auto
   :stub-columns: 1

   * - Source
     - `take-snapshot <https://github.com/evannetwork/ui-angular-core/blob/develop/src/components/take-snapshot>`__

Component to take pictures using HTML 5. Should only be used within a modal.

-------
Example
-------
Reference Implementation: `EvanPictureService <https://github.com/evannetwork/ui-angular-core/blob/develop/src/services/ui/picture.ts>`_

- typescript

.. code-block:: typescript

  import {
    EvanModalService,
  } from 'angular-libs';

  constructor(
    private modalService: EvanModalService,
  ) { }

  ngOnInit() {
    this.picture = await this.modalService.createModal(SnapshotDialogComponent, {});
  }

  openPictureDetail(dataUrl) {
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

------------
View Example
------------

.. image:: ../../../images/angular-core/components/take-snapshot-dialog.png
   :width: 600