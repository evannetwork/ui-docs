====================
FormControlComponent
====================

.. list-table:: 
   :widths: auto
   :stub-columns: 1

   * - Source
     - `control <https://github.com/evannetwork/ui-dapps/tree/master/dapps/evancore.vue.libs/src/components/forms/control>`__
   * - Selector
     - ``evan-form-control``

The form control is a general wrapper for any evan.network form control, like files, input, select. It handles general display configurations like inline or stacked label mode and handles the control properties like label, placeholder, error, id, disabled... Each control inherits this component to handle main properties and the layout definitions.


Props
=====

#. ``value`` - ``string``: The value for the input field.
#. ``label`` - ``string``: The label for the input field.
#. ``id`` - ``string``: The id for the input field.
#. ``error`` - ``string``: Mark the input invalid
#. ``disabled`` - ``string``: Disable the input field
#. ``stacked`` - ``boolean``: Enable stacked to show labels and inputs not on oneline.
#. ``size`` - ``boolean``: Bootstrap grid size

Example
=======
- `Reference Implementation <https://github.com/evannetwork/ui-dapps/blob/master/dapps/evancore.vue.libs/src/components/forms/input/input.vue>`__

.. code-block:: html

  <evan-form-control v-bind="$props">
    <input class="form-control"
      :class="{ 'is-invalid' : error }"
      :id="id"
      :value="value"
      @blur="$emit('blur')"
      @focus="$parent.$emit('setFocus')"
      @input="$emit('input', $event.target.value)"
    />
  </evan-form-control>

View Example
============

.. image:: ../../../images/vue/forms/form_1.png
   :width: 800