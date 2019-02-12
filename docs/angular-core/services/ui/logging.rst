==================
EvanLoggingService
==================

.. list-table:: 
   :widths: auto
   :stub-columns: 1

   * - Source
     - `logging <https://github.com/evannetwork/ui-angular-core/blob/develop/src/services/ui/logging.ts>`__

Helper to handle |source bcc_log|_ logging reports. The frontend is configured to cache each log that was submitted from everywhere. As a result of this, this service can handle this logs and can create reports for developers for error analysis. 

--------------------------------------------------------------------------------

log
================================================================================

.. code-block:: typescript

  loggingService.log(message, level);

Using `BCC log <https://github.com/evannetwork/api-blockchain-core/blob/develop/docs/common/logger.rst>`_ function to handle a generalized logging mechanism.

----------
Parameters
----------

#. ``message`` - ``string``: log message
#. ``level`` - ``string``: log level as string, defaults to 'info'


-------
Returns
-------

``Promise`` returns ``void``: resolved when done

-------
Example
-------

.. code-block:: javascript

  loggingService.log('test', 'error');




--------------------------------------------------------------------------------

getLogsIncludingQueue
================================================================================

.. code-block:: typescript

  loggingService.getLogsIncludingQueue();

Return all |source logLog|_ including the queue logs

-------
Returns
-------

``Array<any>``: logs including queue

-------
Example
-------

.. code-block:: typescript

  loggingService.getLogsIncludingQueue();
  // => { "timestamp": 1529064180496, "level": "notice", "message": "cool message" }




--------------------------------------------------------------------------------

buildLogObject
================================================================================

.. code-block:: typescript

  loggingService.buildLogObject(logs);

enhance log message with user information

----------
Parameters
----------

#. ``logs`` - ``Array<any>``: logs to use

-------
Returns
-------

``Array<any>``: log object

-------
Example
-------

.. code-block:: typescript

  loggingService.buildLogObject(loggingService.getLogsIncludingQueue())




--------------------------------------------------------------------------------

.. _document_getReportLogs:

getReportLogs
================================================================================

.. code-block:: typescript

  loggingService.getReportLogs(types);

Choose type all for current filtered log. Choose errors for only errors.

----------
Parameters
----------

#. ``type`` - ``string``: all | errors

-------
Returns
-------

``Array<any>``: specific logs for type

-------
Example
-------

.. code-block:: typescript

  loggingService.getReportLogs([ 'error' ]);




--------------------------------------------------------------------------------

.. _document_logQuestionAlert:

logQuestionAlert
================================================================================

.. code-block:: typescript

  loggingService.logQuestionAlert();

Opens an alert to ask the user to log only errors with on click or with loggin dapp.

-------
Returns
-------

``Promise`` returns ``any``: resolved when clicked

-------
Example
-------

.. code-block:: typescript

  await loggingService.logQuestionAlert();




--------------------------------------------------------------------------------

.. _document_sendLogs:

sendLogs
================================================================================

.. code-block:: typescript

  loggingService.sendLogs(types);

Send log object to loggly.

----------
Parameters
----------

#. ``type`` - ``string`` (optional): 'all' (send current filtered logs) | 'errors' (send only errors)

-------
Example
-------

.. code-block:: typescript

  loggingService.sendLogs('errors')




--------------------------------------------------------------------------------

.. _document_copy:

copy
================================================================================

.. code-block:: typescript

  loggingService.copy(types);

Start copying of the error log. Choose type all for current filtered log. Choose errors for only errors.

----------
Parameters
----------

#. ``type`` - ``string`` (optional): 'all' (copy current filtered logs) | 'errors' (copy only errors)

-------
Returns
-------

``Promise`` returns ``void``: resolved when done

-------
Example
-------

.. code-block:: typescript

  loggingService.copy('errors');


























.. |source bcc_log| replace:: ``BCC log``
.. _source bcc_log: https://github.com/evannetwork/api-blockchain-core/blob/develop/docs/common/logger.rst

.. |source logLog| replace:: ``logLog``
.. _source logLog: https://github.com/evannetwork/api-blockchain-core/blob/develop/docs/common/logger.rst#logloginterface