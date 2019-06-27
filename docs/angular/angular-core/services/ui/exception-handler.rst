====================
EvanExceptionHandler
====================

.. list-table:: 
   :widths: auto
   :stub-columns: 1

   * - Source
     - `exception-handler <https://github.com/evannetwork/ui-angular-core/blob/develop/src/services/ui/exception-handler.ts>`__

Global angular exception handler to prevent uncatched global errors. Will be registered by the `AngularCore <../modules/angular-core.html>`_ module and must not be manually used.

--------------------------------------------------------------------------------

.. _document_handleError:

handleError
================================================================================

.. code-block:: typescript

  exceptionHandler.handleError(error);

Handles an Exception and logs it to the console. 

----------
Parameters
----------

#. ``error`` - ``Error``: Incoming exception that should be parsed

-------
Returns
-------

``Promise`` returns ``void``: resolved when done

-------
Example
-------

.. code-block:: typescript

  // ...