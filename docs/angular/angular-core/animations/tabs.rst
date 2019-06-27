========================
createTabSlideTransition
========================

.. list-table:: 
   :widths: auto
   :stub-columns: 1

   * - Source
     - `tabs <https://github.com/evannetwork/ui-angular-core/blob/develop/src/animations/tabs.ts>`__

.. code-block:: typescript

  createTabSlideTransition(arguments);

Create an transition to create an tab sliding transition effect.

-------
Returns
-------

`AnimationEntryMetadata``: the animation definition

-------
Example
-------

Can be used within the component creation:

- component.ts

.. code-block:: typescript

  @Component({
    ...
    animations: [
      createTabSlideTransition(),
    ]
  })

- component.html

:: 

  <div class="evan-tabs-container" [@tabSlideTransition]="activeTab">
    <div *ngIf="activeTab === 0"></div>
    <div *ngIf="activeTab === 1"></div>
    <div *ngIf="activeTab === 2"></div>
  </div>
