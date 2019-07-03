=======
tooltip
=======

.. list-table:: 
   :widths: auto
   :stub-columns: 1

   * - Source
     - `tooltip <https://github.com/evannetwork/ui-core/tree/master/dapps/ui.libs/src/style/tooltip.scss>`__
   * - Bootstrap
     - `tooltips <https://getbootstrap.com/docs/4.3/components/tooltips>`__

==============================  ================================================================================================
Class                           Description 
==============================  ================================================================================================
.evan-tooltip-parent            adds position relative the element
.evan-tooltip                   displays the content within a tooltip, but hidden
.show-tooltip                   displays the tooltip
.bs-tooltip-top                 show the tooltip at the top of the container
.bs-tooltip-bottom              show the tooltip at the bottom of the container
.bs-tooltip-left                show the tooltip at the left of the container
.bs-tooltip-right               show the tooltip at the right of the container
==============================  ================================================================================================

-------
example
-------

.. code-block:: html

  <div class="tooltip evan-tooltip bs-tooltip-top show-tooltip"
    role="tooltip">
    <div class="arrow"></div>
    <div class="tooltip-inner">
      help text
    </div>
  </div>

------------
View Example
------------

.. image:: ../../../images/core/tooltip.png
   :width: 300
