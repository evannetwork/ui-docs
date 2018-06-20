============================
ContractListEntriesComponent
============================

Contract paged listentry display. Each `DataContract <https://github.com/evannetwork/blockchain-core/blob/develop/docs/contracts/data-contract.rst>`_ can have several list definitions to store its necessary data in. Each of this lists can grow to an large list of elements. To be able to page this entries easily this component can be used.

Shows simply a button, when the user will be able to page to the next page. Else nothing will be displayed, only the OnUpdate function is called so you can load your list entries like you want.

------
Inputs
------

#. ``contractId`` - ``string``: contract to load the  data for
#. ``listName`` - ``string``: list name to load the data for
#. ``count`` - ``number``: page size to split the loaded bunches in
#. ``reverse`` - ``boolean``: should the data loaded reverse?
#. ``dfsStorage`` - ``boolean`` (default = true): store values in dfs
#. ``encryptedHashes`` - ``boolean`` (default = true): encrypt hashes from values
#. ``onUpdate`` - ``Function``: is emitted when new data was loaded

-----
Usage
-----
In this exmapled we are saved sub contract ids within a list and load the dbcp definition for the contracts.

- component.ts

.. code-block:: typescript

  import { prottle } from 'bcc';
  import {
    EvanBCCService,
    EvanCoreService
  } from 'angular-core';

  ...

  private loadedEntries: Array<string>;

  constructor(
    private bccService: EvanBCCService,
    private core: EvanCoreService
  ) {}

  ngOnInit() {
    ...
    this.contractId = '0x000...';
    this.loadedEntries = [ ];
    ...
  }

  onUpdate(listEntries = this.listEntryComponent.listEntries) {
    if (listEntries.length > 0) {
      await prottle(10, listEntries.map(listEntry => async () => {
        listEntry = listEntry.substring(0, 42);

        if (!this.loadedEntries.find(entry => entry.address === listEntry)) {
          this.loadedEntries.push(
            await this.bccService.description.getDescriptionFromContract(listEntry, this.core.activeAccount())
          );
        }
      });
    }
  }


- component.html

::
  
  <ion-list>
    <ion-item *ngFor="entry of loadedEntries">{{ entry }}</ion-item>
  </ion-list>

  <contract-listentries #listEntryComponent
    [contractId]="contractId"
    [count]="10"
    [dfsStorage]="false"
    [encryptedHashes]="false"
    [listName]="'biglist'"
    [reverse]="true"
    [onUpdate]="loadTasks.bind(this)">
  </contract-listentries>