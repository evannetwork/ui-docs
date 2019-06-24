================
SingletonService
================

.. list-table:: 
   :widths: auto
   :stub-columns: 1

   * - Source
     - `singleton-service <https://github.com/evannetwork/ui-angular-core/blob/develop/src/services/singleton-service.ts>`__

This service can be used to create Singleton services, that shares it reference everywhere. (**Be aware: this will share services even between dapps that uses the same library! Some Ionic functionallities can have some problems, because runtime references are destroyed after an DApp was closed.**).

--------------------------------------------------------------------------------

create
================================================================================

.. code-block:: typescript

  singletonService.create(SingeltonServiceClass, instance, init, updateOnCoreChange);

Creates an single references for services to handle one time service creations and value bindings.

----------
Parameters
----------

#. ``SingeltonServiceClass`` - ``any``: Class object
#. ``instance`` - ``any``: Current instance of an class.
#. ``init`` - ``Function``: Function to run, if the service was created once
#. ``updateOnCoreChange`` - ``boolean``: Run init function, if evan core gets updated

-------
Example
-------

.. code-block:: typescript

  @Injectable()
  export class SampleService {
    /**
     * Create a singleton service instance. Start screen size watching. Prefill
     * dev ens variables
     */
    constructor(
      private platform: Platform,
      private singleton: SingletonService
    ) {
      return singleton.create(SampleService, this, () => {
        // doo initialization stuff
      });
    }
  }