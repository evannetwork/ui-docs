=======================
createOpacityTransition
=======================

.. list-table:: 
   :widths: auto
   :stub-columns: 1

   * - Source
     - `opacity <https://github.com/evannetwork/ui-angular-core/blob/develop/src/animations/opacity.ts>`__

.. code-block:: typescript

  createOpacityTransition();

Create an transition to create an opacity transition effect. ==> Smooth disappearing

-------
Returns
-------

`AnimationEntryMetadata``: the opacity transition

-------
Example
-------

Can be used within the component creation:

- component.ts

.. code-block:: typescript

  @Component({
    ...
    animations: [
      createOpacityTransition(),
    ]
  })

- component.html

:: 

  <div *ngIf="**" [@opacityTransition]></div>