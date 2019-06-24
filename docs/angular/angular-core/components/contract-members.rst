========================
ContractMembersComponent
========================

.. list-table:: 
   :widths: auto
   :stub-columns: 1

   * - Source
     - `contract-members <https://github.com/evannetwork/ui-angular-core/blob/develop/src/components/contract-members>`__

Contract member management component. Allows you to show existing members of contracts and, if you want, to collect more users that can be invited by your code.

------
Inputs
------

#. ``members`` - ``string``: new member account ids that should be added to the contract
#. ``contractMemberStates`` - ``string``: members states of the contract
#. ``label`` - ``string``: this component is displayed like an ionic input, defines property or hides it
#. ``placeholder`` - ``string``: replace input placeholder
#. ``maxMembers`` - ``number``: max users that can be added
#. ``origin`` - ``string``: already added user accounts
#. ``readonly`` - ``string``: show display or add mode

------
Outpus
------

#. ``onChange`` - ``EventEmitter<any>``: Event trigger that is called when something has changed (account moved / removed)

-------------
Public Params
-------------

#. ``touched`` - ``string``: if the menu was opened and closed, the component "gets touched"

-------
Example
-------
Reference Implementation: `Task DApp detail <https://github.com/evannetwork/ui-core-dapps/blob/develop/dapps/dashboard/src/index.ts>`_

.. code-block:: typescript

  import {
    RightsAndRoles
  } from 'bcc';

  import {
    EvanBCCService,
    EvanCoreService,
  } from 'angular-libs';
    
  constructor(
    private bccService: EvanBCCService,
  ) { }

  async ngOnInit() {
    this.membersToAdd = [ ];
    this.taskAddress = '0x000';

    this.task = await this.bcc.dataContract.getEntry(
      taskAddress,
      'metadata',
      this.core.activeAccount()
    );

    this.task.states = loadTaskStates(this.task);
    this.task.members = loadTaskStates(this.task);
  }

  async loadTaskStates(task) {
    const states = { };
    for (let member of task.members) {
      states[member] = await this.getMemberState(task.address, member);
    }
    return states;
  }

  async getMemberState(contractId?: string, accountId?: string) {
    if (accountId === this.core.activeAccount()) {
      const contractInstance = this.bccService.contractLoader.loadContract('BaseContract', contractId);
      return await this.bccService.executor.executeContractCall(contractInstance, 'getConsumerState', accountId);
    }
  }

  async getMembers(contractId: string) {
    const bcRoles = new RightsAndRoles({
      contractLoader: this.bccService.contractLoader,
      executor: this.bccService.executor,
      nameResolver: this.bccService.nameResolver,
    });
    const members = await bcRoles.getMembers(contractId);

    // make them unique
    return members.filter(
      (member, index, a) => index === a.indexOf(member)
    );
  }

::

  <span *ngIf="task.members.length === 0">{{ '_dapptaskboard.no-members' | translate }}</span>
  <contract-members
    [(members)]="membersToAdd"
    [origin]="task.members"
    [readonly]="!(amITheCreator() && task.contractState == 2)"
    [contractMemberStates]="task.states"
    (onChange)="ref.detectChanges()">
    <h3 label>{{ 'custom-label' | translate }}</h3>
  </contract-members>

  <div *ngIf="membersToAdd.length > 0">
    <button ion-button round outline icon-start (click)="addMembers()">
      <ion-icon name="person-add"></ion-icon>
      {{ '_dapptaskboard.invite-members' | translate }}
    </button>
  </div>

------------
View Example
------------

.. image:: ../../images/angular-core/components/contract_members.png
   :width: 600
