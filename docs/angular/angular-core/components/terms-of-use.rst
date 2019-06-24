=======================
EvanTermsOfUseComponent
=======================

.. list-table:: 
   :widths: auto
   :stub-columns: 1

   * - Source
     - `global-password <https://github.com/evannetwork/ui-angular-core/blob/develop/src/components/terms-of-use>`__

When the terms of use are changed or no verification management is available during initial page load, the `EvanBCCService initialize method <https://github.com/evannetwork/ui-angular-core/blob/develop/src/services/bcc/bcc.ts>`_ will call a this component as a modal, to force the user to accept the terms of use. It will also create a verification holder for the current user, if it does not exists.

It can be used as reference implementation for custom global password dialogs.

-------
Example
-------
Reference Implementation: `EvanBCCService initialize method <https://github.com/evannetwork/ui-angular-core/blob/develop/src/services/bcc/bcc.ts>`_

- typescript

.. code-block:: typescript

  import {
    EvanCoreService,
    EvanBCCService,
  } from 'angular-libs';

  constructor(
    private core: EvanCoreService,
    private bcc: EvanBCCService,
  ) { }

  ngOnInit() {
    this.termsOfUseModalPromise = this.modalService.createModal(EvanTermsOfUseComponent, {
      bcc: this.bcc,
      core: this.core,
    });
  }

------------
View Example
------------

.. image:: ../../images/angular-core/components/terms-of-use.png
   :width: 600