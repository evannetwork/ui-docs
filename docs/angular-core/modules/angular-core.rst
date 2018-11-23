===========
AngularCore
===========

.. list-table:: 
   :widths: auto
   :stub-columns: 1

   * - Source
     - `AngularCore <https://github.com/evannetwork/ui-angular-core/blob/develop/src/modules/index.ts>`__

Angular Core Module that includes all components, services, directives and pipes that are described in this documentation. Besides of the core parts, several libraries are also included: 

- CommonModule (|source angular_common|_)
- IonicModule (|source ionic_angular|_)
- TranslateModule (|source ngx_translate|_)
- FormsModule (|source angular_forms|_)
- IonTagsInputModule (|source ionic_tags_input|_)
- RouterModule (|source angular_router|_)
- NgCircleProgressModule (|source ng_circle_progress|_)
- ZXingScannerModule (|source qr_code_scanner_module|_)

-------
Example
-------
- module.ts

.. code-block:: typescript

  import {
    AngularCore,
  } from 'angular-core';

  @NgModule({
    ...
    imports: [
      CommonModule,
      AngularCore,
    ],
    ...
  })
  class SampleModule {
    constructor() { }
  }

- component.ts

.. code-block:: typescript

  import {
    createOpacityTransition,
    EvanBCCService,
    EvanBookmarkService,
    EvanQueue,
    EvanAlertService,
    EvanRoutingService,
    EvanModalService,
    EvanCoreService,
    EvanUtilService
  } from 'angular-core';

  @Component({
    selector: 'dapp-list',
    templateUrl: 'dapp-list.html',
    animations: [
      createOpacityTransition()
    ]
  })

  export class DAppListComponent implements OnInit, OnDestroy {
    private dappKeys: Array<string>;
    private dapps: any;
    private filterString: string;
    private loading: boolean;
    private clearQueue: Function
    private showItemPopover: string;

    constructor(
      public _DomSanitizer: DomSanitizer,
      public routing: EvanRoutingService,
      private bcc: EvanBCCService,
      private bookmarkService: EvanBookmarkService,
      private queue: EvanQueue,
      private alertService: EvanAlertService,
      private popoverCtrl: PopoverController,
      private modalService: EvanModalService,
      private core: EvanCoreService,
      public utils: EvanUtilService
    ) { }

    ...
  
.. |source angular_common| replace:: ``@angular/common``
.. _source angular_common: https://github.com/evannetwork/api-blockchain-core/blob/develop/docs/encryption/key-provider.rst

.. |source ionic_angular| replace:: ``ionic-angular``
.. _source ionic_angular: https://github.com/evannetwork/api-blockchain-core/blob/develop/docs/encryption/key-provider.rst

.. |source ngx_translate| replace:: ``@ngx-translate/core``
.. _source ngx_translate: https://github.com/evannetwork/api-blockchain-core/blob/develop/docs/encryption/key-provider.rst

.. |source angular_forms| replace:: ``@angular/forms``
.. _source angular_forms: https://github.com/evannetwork/api-blockchain-core/blob/develop/docs/encryption/key-provider.rst

.. |source ionic_tags_input| replace:: ``ionic-tags-input``
.. _source ionic_tags_input: https://github.com/evannetwork/api-blockchain-core/blob/develop/docs/encryption/key-provider.rst

.. |source angular_router| replace:: ``@angular/router``
.. _source angular_router: https://github.com/evannetwork/api-blockchain-core/blob/develop/docs/encryption/key-provider.rst

.. |source ng_circle_progress| replace:: ``ng-circle-progress``
.. _source ng_circle_progress: https://github.com/evannetwork/api-blockchain-core/blob/develop/docs/encryption/key-provider.rst

.. |source qr_code_scanner_module| replace:: ``qr-code-scanner module``
.. _source qr_code_scanner_module: https://github.com/evannetwork/api-blockchain-core/blob/develop/docs/encryption/key-provider.rst