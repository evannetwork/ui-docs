================
EvanToastService
================

Ionic toast wrapper service that handles translated toasts.

This service hold the reference to the latest available toast service to handle cross dapp toast messages. It could be possible, that the queue is running and tries to submit an toast, even when the queue origin dapp was closed and the toastService is destroyed.




--------------------------------------------------------------------------------

.. _document_showToast:

showToast
================================================================================

.. code-block:: typescript

  toastService.showToast(toastObj);

Shows a Ionic toast message using the latest available toastService.

----------
Parameters
----------

#. ``toastObj`` - ``any``: toast configuration object

-------
Returns
-------

``Promise`` returns ``any``: Resolved when disappeard

-------
Example
-------

.. code-block:: typescript

  await this.toastService.showToast({
    message: '_dapptaskboard.task-reload',
    duration: 2000,
    closeButtonText: 'close'
  });




--------------------------------------------------------------------------------

_showToast
================================================================================

.. code-block:: typescript

  initializedModule._showToast(arguments);

Shows a Ionic toast message for the current angular modul. Be sure that the module was not stopped by calling this.

----------
Parameters
----------

#. ``toastObj`` - ``any``: toast configuration object

-------
Returns
-------

``Promise`` returns ``any``: Resolved when disappeard

-------
Example
-------

.. code-block:: typescript

  this.toastService.showToast({
    message: '_dapptaskboard.task-reload',
    duration: 2000,
    closeButtonText: 'close'
  });