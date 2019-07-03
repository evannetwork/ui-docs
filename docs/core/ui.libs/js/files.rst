=====
Files
=====

.. list-table:: 
   :widths: auto
   :stub-columns: 1

   * - Source
     - `Files <https://github.com/evannetwork/ui-core/tree/master/dapps/ui.libs/src/Files.ts>`__
 
--------------------------------------------------------------------------------

.. _files_fileToContainerFile:

fileToContainerFile
================================================================================

.. code-block:: typescript

  files.fileToContainerFile(file);
 
Takes an usual File object (e.g. File from HTML 5 file input) and transforms it into an blockchain-
core understandable file.
 
----------
Parameters
----------

#. ``file`` - ``object``: html 5 input result file

-------
Returns
-------

``Promise`` returns ``UIContainerFile``: resolved when done

-------
Example
-------
- `Reference Implementation <https://github.com/evannetwork/ui-vue/blob/master/dapps/evancore.vue.libs/src/components/files/files.ts>`_

.. code-block:: typescript

  const containerFile = await FileHandler.fileToContainerFile(newFile);




--------------------------------------------------------------------------------

.. _files_readFileAsArrayBuffer:

readFileAsArrayBuffer
================================================================================

.. code-block:: typescript

  files.readFileAsArrayBuffer(file);

Upload a file that were selected with an HTML 5 <input type="file"> selector or using the evan-file-
select component and transforms them into an encryption object.

----------
Parameters
----------

#. ``file`` - ``File``: array of files

-------
Returns
-------

``Promise`` returns ``File``: uploaded files transformed into an encryption object

-------
Example
-------

.. code-block:: typescript

  const buffer = fileOrigin.buffer ? fileOrigin.buffer : await readFileAsArrayBuffer(fileOrigin);




--------------------------------------------------------------------------------

.. _files_getReadableFileSize:

getReadableFileSize
================================================================================

.. code-block:: typescript

  files.getReadableFileSize(size);

Parse the file size to a human readable format

----------
Parameters
----------

#. ``size`` - ``number``: size in B

-------
Returns
-------

``number``: XXX KB / XXX MB

-------
Example
-------

.. code-block:: typescript

  const readableSize = getReadableFileSize(file.size);

Interfaces
==========

---------------
UIContainerFile
---------------

Transformed container file, that can be saved by the blockchain core.

#. ``size`` - ``string``: The file size in bytes
#. ``readableSize`` - ``ContainerConfig``: Size parsed to kb, md, ...
#. ``blobUri`` - ``string``: downloadable url
#. ``blob`` - ``string``: blob instance
