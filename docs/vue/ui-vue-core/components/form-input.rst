=========================
FormControlInputComponent
=========================

.. list-table:: 
   :widths: auto
   :stub-columns: 1

   * - Source
     - `input <https://github.com/evannetwork/ui-vue/tree/master/dapps/evancore.vue.libs/src/components/forms/input>`__
   * - Extends
     - `EvanFormControl <./form-control.html>`_
   * - Selector
     - ``evan-form-control-input``
 
Input element wrapper that extends the the evan form control components. Each parameter that is passed to the component will be binded to the containing input element. So you can easy pass a type, pattern or what ever.

Props
=====
- `EvanFormControl <./form-control.html>`_
- Every property that can be passed to a input element

Example
=======
- `Reference Implementation <https://github.com/evannetwork/ui-core-dapps/blob/master/dapps/components.vue/src/components/forms/forms.vue>`__

- directly using in html

  .. code-block:: html

    <evan-form-control-input
      id="evan-form-test-3"
      label="Label"
      type="number"
      placeholder="Placeholder"
      v-model="testValue"
      :stacked="stacked"
    />

- configuration for a `EvanForm <./form.html>`_

  .. code-block:: js

   this.sampleForm = new EvanForm(this, {
      field3: {
        value: '',
        validate: function(vueInstance: Forms, form: SampleFormInterface) {
          return this.value.length !== 0;
        },
        uiSpecs: {
          type: 'input',
          attr: {
            error: 'custom error',
            label: 'custom label',
            placeholder: 'custom placeholder',
            type: 'number',
            size: 6
          }
        }
      },
    }) as SampleFormInterface;

View Example
============

.. image:: ../../../images/vue/forms/form_1.png
   :width: 800