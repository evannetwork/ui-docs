=======================
EvanFileSelectComponent
=======================

.. list-table:: 
   :widths: auto
   :stub-columns: 1

   * - Source
     - `file-select <https://github.com/evannetwork/ui-angular-core/blob/develop/src/components/file-select>`__

file selector component for HTML 5 &IOS & Anroid

------
Inputs
------

#. ``label`` - ``string``: this component is displayed like an ionic input, defines property or hides it
#. ``buttonText`` - ``string``: optional button text that should be displayed for the add button
#. ``ngModel`` - ``string``: files that should be uploaded
#. ``disabled`` - ``string``: disable file select or not
#. ``accept`` - ``string``: input type="file" accept attribute
#. ``downloadable`` - ``string``: enable download of files
#. ``minFiles`` - ``string``: minimum amount of files that must be uploaded
#. ``maxFiles`` - ``string``: maximum amount of files that can be uploaded
#. ``multiple`` - ``string``: are multiple files allowed?

------
Outputs
------

#. ``onChange`` - ``string``: Event emitter to tell using component, that something has changed

-------
Example
-------

- html

::

  <evan-file-select name="attachments"
    *ngIf="offer.payload.attachments"
    [(ngModel)]="offer.payload.attachments"
    (onChange)="ref.detectChanges()"
    disabled="true"
    downloadable="true">
  </evan-file-select>
