=========================
FormControlSelectComponent
=========================

.. list-table:: 
   :widths: auto
   :stub-columns: 1

   * - Source
     - `select <https://github.com/evannetwork/ui-vue/tree/master/dapps/evancore.vue.libs/src/components/forms/select>`__
   * - Extends
     - `EvanFormControl <./form-control.html>`_
   * - Selector
     - ``evan-form-control-select``
 
Select element wrapper that extends the the evan form control components. Each parameter that is passed to the component will be binded to the containing select element. So you can easy pass a type, pattern or what ever.

Props
=====
- `EvanFormControl <./form-control.html>`_
- Every property that can be passed to a select element

#. ``options`` - ``Array<{ label: string, value: string }|string>``: Array of select options including a label or value, or only a string that is used for both.

Example
=======
- `Reference Implementation <https://github.com/evannetwork/ui-core-dapps/blob/master/dapps/components.vue/src/components/forms/forms.vue>`__

- directly using in html

  .. code-block:: html

    <evan-form-control-select
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
          type: 'select',
          attr: {
            error: 'custom error',
            label: 'custom label',
            type: 'number',
            size: 6,
            options: this.options,
          }
        }
      },
    }) as SampleFormInterface;

View Example
============

.. image:: ../../../images/vue/forms/form_1.png
   :width: 800