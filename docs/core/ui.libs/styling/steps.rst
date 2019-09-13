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

- large steps

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

- small steps

  .. code-block:: html

    <div class="evan-step-header-sm">
      <button class="btn">
        <span class="stepper-circle active"></span>
        <div role="tooltip" class="tooltip evan-tooltip bs-tooltip-top">
          <div class="arrow"></div>
          <div class="tooltip-inner">
            step 1
          </div>
        </div>
      </button>
      <button class="btn">
        <span class="stepper-circle active"></span>
        <div role="tooltip" class="tooltip evan-tooltip bs-tooltip-top">
          <div class="arrow"></div>
          <div class="tooltip-inner">
            step 2
          </div>
        </div>
      </button>
      <button class="btn">
        <span class="stepper-circle active"></span>
        <div role="tooltip" class="tooltip evan-tooltip bs-tooltip-top">
          <div class="arrow"></div>
          <div class="tooltip-inner">
            step 3
          </div>
        </div>
      </button>
    </div>

------------
View Example
------------

  .. image:: ../../../images/core/steps.png
     :width: 600
