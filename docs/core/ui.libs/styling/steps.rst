=====
steps
=====

.. list-table:: 
   :widths: auto
   :stub-columns: 1

   * - Source
     - `config <https://github.com/evannetwork/ui-core/tree/master/dapps/ui.libs/src/style/config.scss>`__

Styling for html steppers.

-------
Example
-------

.. code-block:: html

  <div class="evan-steps">
    <div class="evan-step-header mt-3">
      <button class="btn">
        <span class="stepper-circle"
          :class="{
            'bg-primary': isActive,
            'bg-secondary': !disabled,
            'bg-gray': disabled,
          }">
          1
        </span>
        <span>Step 1</span>
      </button>
      <button class="btn">
        <span class="stepper-circle"
          :class="{
            'bg-primary': isActive,
            'bg-secondary': !disabled,
            'bg-gray': disabled,
          }">
          1
        </span>
        <span>Step 1</span>
      </button>
      <button class="btn">
        <span class="stepper-circle"
          :class="{
            'bg-primary': isActive,
            'bg-secondary': !disabled,
            'bg-gray': disabled,
          }">
          1
        </span>
        <span>Step 1</span>
      </button>
    </div>


------------
View Example
------------

.. image:: ../../../images/core/steps.png
   :width: 600
