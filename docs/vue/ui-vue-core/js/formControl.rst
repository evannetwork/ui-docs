===========
formControl
===========

.. list-table:: 
   :widths: auto
   :stub-columns: 1

   * - Source
     - `forms <https://github.com/evannetwork/ui-vue/tree/master/dapps/evancore.vue.libs/src/forms.ts>`__

Represents one formular input and handles dirty and error flags, also runs validations.

#. ``dirty`` - ``boolean``: Is the current element dirty? Error will be only returned, if an error is available.
#. ``_error`` - ``string``: Error returned by validation handler
#. ``error`` - ``string``: Returns only an error, when the control is set to dirty. So intially the formular does not display an error. Only when it was changed once.
#. ``name`` - ``string``: Form control name (e.g. name, password, ...)
#. ``$ref`` - ``string``: Returns the vue element reference (vueInstance.$refs[this.name])
#. ``_value`` - ``string``: Original value, without custom setter amd getter
#. ``value`` - ``string``: Overwrite the value getter / setter, so we automatically check for errors, when an validate was applied.
#. ``_validate`` - ``Function|undefined``: validate function that will be runned when the value was changed
#. ``vueInstance`` - ``VueComponent``: Original vue instance to directly access component references within the control
#. ``form`` - `EvanForm <https://github.com/evannetwork/ui-vue/tree/master/dapps/evancore.vue.libs/src/forms.ts>`__: Parent evan form, so the form `isValid` flag can be set automatically
#. ``validating`` - ``boolean``: True, when an asynchronious validate function was applied and this validation is running

--------------------------------------------------------------------------------

.. _formControl_constructor:

constructor
================================================================================

.. code-block:: typescript

  new FormControl(options);

Creates a new FormControl instance.

----------
Parameters
----------

#. ``name`` - ``string``: Form control name
#. ``value`` - ``any``: initial control value
#. ``vueInstance`` - ``Vue``: Original vue instance to directly access component references within the control
#. ``validate`` - ``Function``: Runs the within the constructor provided validate function. The provided function should should return true, if everything is fine. Should return false, string, object, ... to mark the formControl as invalid and to set the internal error parameter. The function can also be return a Promise. During the asynchronious validation is running, the validating flag is set to true.
#. ``form`` - ``EvanForm``: Parent evan form, so the form is valid flag can be set automatically
#. ``uiSpecs`` - ``EvanFormControlUISpecs``: Used to describe the evan form control automatic rendering.
  #. ``type`` - ``string``: Input type of the component that should be rendered (input, select, files)
  #. ``attr`` - ``any``: attributes that should be passed to the `evan-control-* <./../components/form-control.html>`__ component
    #. ``placeholder`` - ``string``: 
    #. ``error`` - ``string``: Mark the input invalid
    #. ``label`` - ``string``: The label for the input field.
    #. ``options`` - ``Array<{ label: string, value: any }>``: The selectable options. Can be an array of label-value pairs or an array of strings.
    #. ``size`` - ``number``: Bootstrap grid size
    #. ``disabled`` - ``number``: Disable the input field
    #. ``id`` - ``string``: The id for the input field.
    #. ``stacked`` - ``boolean``: Enable stacked to show labels and inputs not on oneline.

-------
Returns
-------

``FormControl`` instance

-------
Example
-------
- `FormControl Reference Implementation <https://github.com/evannetwork/ui-core-dapps/blob/master/dapps/addressbook.vue/src/components/contact-form/contact-form.ts>`__


.. code-block:: typescript
  
  this.accountId = new FormControl(
    'accountId',
    '0x1813587e095cDdfd174DdB595372Cb738AA2753A',
    this,
    function(vueInstance: ContactAddComponent, form: ContactFormInterface) {
      if (!web3.utils.isAddress(this.value)) {
        return 'invalid-address';
      } else {
        return true;
      }
    }
  });

.. code-block:: html

  <div class="form-group w-100">
    <label for="accountId">
      {{ `accountId.title` | translate }} *
    </label>
    <input class="form-control" required
      id="accountId" ref="accountId"
      :class="{ 'is-invalid' : form.accountId.error }"
      :placeholder="`accountId.desc` | translate"
      v-model="accountId.value"
      @blur="accountId.setDirty()">
    <div class="invalid-feedback">
      {{ accountId.error | translate }}
    </div>
  </div>




--------------------------------------------------------------------------------

.. _formControl_setDirty:

setDirty
================================================================================

.. code-block:: typescript

  formControl.setDirty();

Sets the control into dirty mode.

-------
Example
-------

.. code-block:: typescript

  this.accountId.setDirty();




--------------------------------------------------------------------------------

.. _formControl_validate:

validate
================================================================================

.. code-block:: typescript

  formControl.validate();

Runs the within the constructor provided validate function. The provided function should should
return true, if everything is fine. Should return false, string, object, ... to mark the formControl
as invalid and to set the internal error parameter. The function can also be return a Promise.
During the asynchronious validation is running, the validating flag is set to true.

The function will be automatically execute by using the `formControl.value` setter.


-------
Example
-------

.. code-block:: typescript

  this.accountId.value = 'cool id';
  console.log(this.accountId.error);
  // 'invalid-address'

