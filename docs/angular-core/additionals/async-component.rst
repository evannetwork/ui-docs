==============
AsyncComponent
==============

Use the `AsyncComponent <https://github.com/evannetwork/ui-angular-core/blob/develop/src/classes/AsyncComponent>`_ for Components that implements asynchronious ngOnInit functions. The ngOnInit function will be called and processed. If the App is switched very fast, the ngOnDestroy is called before the ngOnInit was resolved. As a result of this, watcher can be bound after ngOnDestroy and will never be detached again. Also, this.ref.detectChanges(); functions are called after the ngOnInit was resolved. If the view is already detached, this will trigger more errors. Extend your component with this class and change your ngOnInit and ngOnDestroy functions into _ngOnInit and _ngOnDestroy. The ref is automatically detached, and the loading attribute is set, until the ngOnInit was resolved. At the end, if the view wasnt destroyed before, the loading will be removed and the functions will be called "this.ref.detectChanges();"

-------
Example
-------

.. code-block:: typescript

  export class DAppsRootComponent extends AsyncComponent {
    private watchRouteChange: Function;
    constructor(
      private core: EvanCoreService,
      private bcc: EvanBCCService,
      private ref: ChangeDetectorRef,
      private routingService: EvanRoutingService
    ) {
      super(ref);
    }
    async _ngOnInit() {
      this.watchRouteChange = this.routingService.subscribeRouteChange(() => this.ref.detectChanges());
      await this.bcc.initialize((accountId) => this.bcc.globalPasswordDialog(accountId));
      await this.core.utils.timeout(1000);
    }
    _ngOnDestroy() {
      this.watchRouteChange();
    }
  }