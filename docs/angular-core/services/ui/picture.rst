==================
EvanPictureService
==================

Picture taking service for HTML 5 / IOS / Android.




--------------------------------------------------------------------------------

.. _document_takeSnapshot:

takeSnapshot
================================================================================

.. code-block:: typescript

  pictureService.takeSnapshot(arguments);

Takes an img. On Desktop the webcam will be used. On mobile IOS / Android internals will be used to access native cameras.

-------
Returns
-------

``Promise`` returns ``any``: the img data

.. code-block:: typescript

  {
    name: 'capture.png',
    fileType: 'image/png',
    file: arrayBuffer,
    blobURI: this._DomSanitizer.bypassSecurityTrustUrl(dataUri)
  }

-------
Example
-------

.. code-block:: typescript

  const picture = await this.pictureService.takeSnapshot();




--------------------------------------------------------------------------------

getBlobUri
================================================================================

.. code-block:: typescript

  pictureService.getBlobUri(dataUrl);

Transform a blob uri from an dataUrl

----------
Parameters
----------

#. ``dataUrl`` - ``string``: data url that should be transformed

-------
Returns
-------

``Promise`` returns ``string``: blob uri

-------
Example
-------

.. code-block:: typescript

  pictureService.getBlobUri('blob:https://dashboard.evan.network/74334fca-0cc3-46d5-9804-2a7161005fe1')




--------------------------------------------------------------------------------

dataURItoBlob
================================================================================

.. code-block:: typescript

  pictureService.dataURItoBlob(dataURI);

Transform a data uri in to an blob.

----------
Parameters
----------

#. ``dataURI`` - ``string``: The options used for calling

-------
Returns
-------

``Promise`` returns ``any``: transformed blob

-------
Example
-------

.. code-block:: typescript

  const buffer = await pictureService.dataURItoBlob('blob:https://dashboard.evan.network/74334fca-0cc3-46d5-9804-2a7161005fe1');




--------------------------------------------------------------------------------

.. _document_blobToDataURI:

blobToDataURI
================================================================================

.. code-block:: typescript

  pictureService.blobToDataURI(blob);

Transforms an blob into an data uri.

----------
Parameters
----------

#. ``blob`` - ``Blob``: The options used for calling

-------
Returns
-------

``Promise`` returns ``void``: transformed data uri

-------
Example
-------

.. code-block:: typescript

  if (dataUri === pictureService.blobToDataURI(pictureService.dataURItoBlob('blob:https://dashboard.evan.network/74334fca-0cc3-46d5-9804-2a7161005fe1')) {
    console.log('same result')
  }




--------------------------------------------------------------------------------

.. _document_blobToArrayBuffer:

blobToArrayBuffer
================================================================================

.. code-block:: typescript

  pictureService.blobToArrayBuffer(blob);

Transforms an blob into an array buffer.

----------
Parameters
----------

#. ``blob`` - ``any``: blob to transform

-------
Returns
-------

``Promise`` returns ``any``: transformed array buffer

-------
Example
-------

.. code-block:: typescript

  pictureService.blobToArrayBuffer(blob);




--------------------------------------------------------------------------------

.. _document_resizeImage:

resizeImage
================================================================================

.. code-block:: typescript

  pictureService.resizeImage(dataUri, dimensions);

Takes an dataUri and resizes the img to an maximum px ratio of 1000px:1000px.

----------
Parameters
----------

#. ``dataUri`` - ``string``: Data Uri
#. ``dimensions`` - ``any``: dimensions to transform the picture to (default max_width: 1000, max_height: 1000)

-------
Returns
-------

``Promise`` returns ``void``: Returns the resized img as a blob.

-------
Example
-------

.. code-block:: typescript

  await pictureService.resizeImage('blob:https://dashboard.evan.network/74334fca-0cc3-46d5-9804-2a7161005fe1');