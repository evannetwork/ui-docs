=======================
createOpacityTransition
=======================

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