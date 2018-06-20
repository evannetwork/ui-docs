================
BigPictureDialog
================

Takes an img url and shows an image on fullscreen (optimized for modal dialogs).
The dataUrl can be anything that can display an img:
  
- http / https url
- base64 img code
- data url (blob:http://localhost:...)

To take pictures during application runtime have a look at the `EvanPictureService </angular-core/services/ui/picture.html>`_.

-----
Usage
-----
Reference Implementation: `Task DApp detail <https://github.com/evannetwork/core-dapps/blob/develop/dapps/task/src/components/detail>`_

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

Havea look at the `EvanModalService </angular-core/services/ui/modal.html#showbigpicture>`_. 

-----------
View Sample
-----------

.. image:: /images/angular-core/components/big-picture.png
   :width: 600