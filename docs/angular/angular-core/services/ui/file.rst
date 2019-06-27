================
EvanFileService
================

.. list-table:: 
   :widths: auto
   :stub-columns: 1

   * - Source
     - `files <https://github.com/evannetwork/ui-angular-core/blob/develop/src/services/ui/files.ts>`__

Service to handle files and its encryption / decryption.


--------------------------------------------------------------------------------

.. _document_readFilesAsArrayBuffer:

readFilesAsArrayBuffer
================================================================================

.. code-block:: typescript

  inputsService.readFilesAsArrayBuffer(files, encryption);

Uploads an array of files that were selected with an HTML 5 <input type="file"> selector or using the
evan-file-select component and transforms them into an encryption object.

----------
Parameters
----------

#. ``files`` - ``Array<any>``: array of files selected using an html 5 input type="file" element or using the EvanFileSelectComponent.

-------
Returns
-------

``Promise<any>``: uploaded files transformed into an encryption object 

-------
Example
-------

.. code-block:: typescript

  const urlCreator = (<any>window).URL || (<any>window).webkitURL;
  const blobURI = urlCreator.createObjectURL(this.fileSelect[0]);
  // transform to array buffer so we can save it within the queue
  const arrayBuffer = await this.fileService.readFilesAsArrayBuffer(
    [ this.fileSelect[0] ]);

  // transform file object
  this.formData.picture = {
    blobURI: this._DomSanitizer.bypassSecurityTrustUrl(blobURI),
    file: arrayBuffer[0].file,
    fileType: arrayBuffer[0].type,
    name: arrayBuffer[0].name,
  };

--------------------------------------------------------------------------------

.. _document_equalizeFileStructure:

equalizeFileStructure
================================================================================

.. code-block:: typescript

  inputsService.equalizeFileStructure(files);

Transform an array of files to be valid for display (including file, blob and blobURI) (normally the
result of the EvanPictureComponent or EvanFileSelectComponent)

----------
Parameters
----------

#. ``files`` - ``Array<any>``: array of files that should be checked

-------
Returns
-------

``Promise<Array<any>>``: array of valid files

-------
Example
-------

.. code-block:: typescript

  const parsed = JSON.parse(formData[key]);

  if (parsed.private) {
    formData[key] = (await this.bcc.dataContract.decrypt(
      formData[key],
      contractAddress,
      activeAccount,
      '*'
    )).private;

    // transform blobURI to security trust url, so the ui can show it
    formData[key] = await this.fileService.equalizeFileStructure(formData[key]);
  } else {
    formData[key] = parsed;
  }

--------------------------------------------------------------------------------

.. _document_downloadMobile:

downloadMobile
================================================================================

.. code-block:: typescript

  inputsService.downloadMobile(name, blob);

checks for an active dom element and scrolls the users viewport to this input

----------
Parameters
----------

#. ``name`` - ``string``: name of the file
#. ``blob`` - ``Blob``: Blob of the file

-------
Returns
-------

``Promise<any>``: uploaded files transformed into an encryption object 

-------
Example
-------

  ::

    <a ion-button outline icon-only clear color="red"
      *ngIf="utils.isMobile()" target="_blank" (click)="fileService.downloadMobile(file.name, file.blob)">
      <ion-icon name="download"></ion-icon>
    </a>
