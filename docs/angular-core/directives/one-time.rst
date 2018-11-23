================
OneTimeDirective
================

.. list-table:: 
   :widths: auto
   :stub-columns: 1

   * - Source
     - `oneTime <https://github.com/evannetwork/ui-angular-core/blob/develop/src/directives/oneTime.ts>`__

Detaches Angular view update bindings to prevent automatic updates.

-------
Example
-------
Reference Implementation: `SplitPane Component <https://github.com/evannetwork/ui-angular-core/blob/develop/src/components/split-pane/split-pane.html>`_

::
  
  <img class="img-large" *oneTime [src]="_DomSanitizer.bypassSecurityTrustUrl(rootDApp.imgWide)" />