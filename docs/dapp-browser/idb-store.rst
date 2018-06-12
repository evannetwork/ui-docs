================================================================================
IDBStore
================================================================================

IndexDB store wrapper.


--------------------------------------------------------------------------------

.. _module_name_constructor:

constructor
================================================================================

.. code-block:: typescript

  new IDBStore(dbName, storeName);

Creates a new IDBStore instance.

----------
Parameters
----------

#. ``options`` - ``IDBStoreOptions``: options for IDBStore constructor.
    * ``log`` - ``Function`` (optional): function to use for logging: ``(message, level) => {...}``
    * ``logLevel`` - |source logLevel|_ (optional): messages with this level will be logged with ``log``
    * ``logLog`` - |source logLogInterface|_ (optional): container for collecting log messages
    * ``logLogLevel`` - |source logLevel|_ (optional): messages with this level will be pushed to ``logLog``

-------
Returns
-------

``IDBStore`` instance

-------
Example
-------

.. code-block:: typescript
  
  const ModuleName = new IDBStore({
    // ...
  });



.. required for building markup
.. |source logLevel| replace:: ``LogLevel``
.. _source logLevel: logger.html#LogLevel

.. |source logLogInterface| replace:: ``LogLogInterface``
.. _source logLogInterface: logger.html#LogLogInterface