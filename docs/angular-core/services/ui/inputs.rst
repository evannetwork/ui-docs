================
EvanInputService
================

.. list-table:: 
   :widths: auto
   :stub-columns: 1

   * - Source
     - `inputs <https://github.com/evannetwork/ui-angular-core/blob/develop/src/services/ui/inputs.ts>`__

Helper that improves input selection on mobile devices. It will scroll automatically, so the input will appear within the viewport.





--------------------------------------------------------------------------------

.. _document_scrollToActiveInput:

scrollToActiveInput
================================================================================

.. code-block:: typescript

  inputsService.scrollToActiveInput();

checks for an active dom element and scrolls the users viewport to this input

-------
Example
-------

.. code-block:: typescript

  inputsService.scrollToActiveInput();