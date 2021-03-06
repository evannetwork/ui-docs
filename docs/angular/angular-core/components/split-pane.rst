======================
EvanSplitPaneComponent
======================

.. list-table:: 
   :widths: auto
   :stub-columns: 1

   * - Source
     - `split-pane <https://github.com/evannetwork/ui-angular-core/blob/develop/src/components/split-pane>`__

Create easy Dashboards

  - generates an left panel using Ionic (will be folded on small displays)
  - With a click into the header it will show a small view on big devices.
  - include footer select box to navigate to root dapps

**Notice: powerfull in combination with DApps that using dapp-wrapper.**

ng-content selectors:

  - "header" for top bar replacement (customHeader parameter must be true)
  - "evan-menu-content" for left panel contents
  - "evan-content" for right side

------
Inputs
------
- ``disableSidepanel`` : use dashboard wrapper functions, but hide the sidepanel
- ``customHeader`` : Check if a custom header should be displayed

------
Events
------

- ``smallToolbarToggled`` : Event triggered, when user clicks of dashboard header
- ``rootDAppLoaded`` : Event triggered, when a new root dapp was loaded (can be submitted multiple times)

-------
Example
-------
Reference Implementation: `Dashboard DApp <https://github.com/evannetwork/ui-core-dapps/blob/develop/dapps/dashboard/src/components/dashboard/dashboard.html>`_

- typescript

.. code-block:: typescript

  this.dapps = await this.descriptionService.getMultipleDescriptions([
    'favorites',
    'addressbook',
    'mailbox',
    'profile'
  ]);

- html

::
  
  <evan-split-pane #splitPane *ngIf="!loading" (smallToolbarToggled)="ref.detectChanges()">
    <div evan-menu-content>
      <ion-list>
        <button ion-item menuClose 
          color="light" 
          *ngFor="let dapp of dapps"
          routerLink="./{{ dapp.ensAddress }}"
          routerLinkActive="active">
          <ion-avatar item-start *ngIf="dapp.imgSquare">
            <img item-start large *oneTime [src]="_DomSanitizer.bypassSecurityTrustUrl(dapp.imgSquare)" />
          </ion-avatar>
          <h2 *ngIf="!splitPane.isSmallToolbar()">{{ dapp.translated.name | translate }}</h2>
          <h3 *ngIf="!splitPane.isSmallToolbar()">{{ dapp.translated.description | translate }}</h3>
          <div class="left-panel-notification"
            *ngIf="dapp.name === 'mailbox' && mailboxService.newMailCount > 0">
            {{ mailboxService.newMailCount > 9 ? 9 + '+' : mailboxService.newMailCount }}
          </div>
        </button>
      </ion-list>
    </div>
    <div evan-content
      [@routerTransition]="o?.activatedRouteData?.state">
      <router-outlet #o="outlet"></router-outlet>
    </div>
  </evan-split-pane>

------------
View Example
------------
- normal view

.. image:: ../../../images/angular-core/components/evan-split-pane.png
   :width: 600

- small view

.. image:: ../../../images/angular-core/components/evan-split-pane-small.png
   :width: 600