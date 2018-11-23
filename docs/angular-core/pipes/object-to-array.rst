=================
ObjectToArrayPipe
=================

.. list-table:: 
   :widths: auto
   :stub-columns: 1

   * - Source
     - `ObjectToArray <https://github.com/evannetwork/ui-angular-core/blob/develop/src/pipes/ObjectToArray.ts>`__

Transforms an object into an array, to easily \*ngFor repeat for an object.

-------
Example
-------
- typescript

.. code-block:: typescript

  this.listObj = {
    a: {
      name: 'a'
    },
    b: {
      name: 'b'
    },
    c: {
      name: 'c'
    }
  }  

::
  
  <div *ngFor="let entry of listObj | ObjectToArrayPipe">
    {{ entry.name }}
  </div>

**will render: a, b, c**