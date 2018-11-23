====================
createGrowTransition
====================

.. list-table:: 
   :widths: auto
   :stub-columns: 1

   * - Source
     - `grow <https://github.com/evannetwork/ui-angular-core/blob/develop/src/animations/grow.ts>`__


.. code-block:: typescript

  createGrowTransition();

Creates an new grow transition Angular 5 trigger animation (element will start by an height of zero and will be increased to the original one). 

-------
Returns
-------

`AnimationEntryMetadata``: returns the grow transition

-------
Example
-------

Can be used within the component creation:

- component.ts

.. code-block:: typescript

  @Component({
    ...
    animations: [
      createGrowTransition(),
    ]
  })

- component.html

:: 

  <div *ngIf="**" [@growTransition]></div>
