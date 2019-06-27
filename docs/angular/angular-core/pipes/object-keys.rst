==========
objectKeys
==========

.. list-table:: 
   :widths: auto
   :stub-columns: 1

   * - Source
     - `objectKeys <https://github.com/evannetwork/ui-angular-core/blob/develop/src/pipes/object-keys.ts>`__

Transforms an object into an array, to easily ngFor repeat for an object

-------
Example
-------
- typescript

.. code-block:: typescript

  this.listObj = {
    a: {
      name: 'a123'
    },
    b: {
      name: 'b123'
    },
    c: {
      name: 'c123'
    }
  }  

::
  
  <div *ngFor="let key of listObj | objectKeys">
    {{ key }}
  </div>

**will render: a, b, c**