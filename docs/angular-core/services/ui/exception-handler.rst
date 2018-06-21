====================
EvanExceptionHandler
====================

Global angular exception handler to prevent uncatched global errors. Will be registered by the `AngularCore </angular-core/modules/angular-core.html>`_ module and must not be manually used.

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