========
EvanForm
========

.. list-table:: 
   :widths: auto
   :stub-columns: 1

   * - Source
     - `forms <https://github.com/evannetwork/ui-vue/tree/master/dapps/evancore.vue.libs/src/forms.ts>`__

Generalized data representation for a evan.network formular. Handles full validation and error handling logic. Uses the EvanFormControls to handle all controls seperated and calculates them into one status detail into this class.

#. ``controls`` - ``Array<string>``: list of control names that were applied to the form.
#. ``vueInstance`` - ``VueComponent``: The vue instance of for validation etc..
#. ``isValid`` - ``boolean``: Is everything valid within the form?

Each control that is passed into the constructor or that is added by the `addControl` function will be available within the form instance. You should create your own form interface to easily interact with the form sub properties.

--------------------------------------------------------------------------------

.. _form_example:

Example
=======
- `Reference implementation <https://github.com/evannetwork/ui-core-dapps/tree/develop/dapps/addressbook.vue/src/components/add>`__

.. code-block:: typescript

  interface ContactFormInterface extends EvanForm {
    accountId: EvanFormControl;
    alias: EvanFormControl;
    email: EvanFormControl;
    emailInvite: EvanFormControl;
    eve: EvanFormControl;
    tags: EvanFormControl;
  }

  this.contactForm = (<ContactFormInterface>new EvanForm(this, {
      alias: {
        value: 'the alias',
        validate: function(vueInstance: ContactAddComponent, form: ContactFormInterface) {
          return this.value.length !== 0;
        }
      },
      ...
    }
  );

  console.log(this.contactForm.alias.value);
  // 'the alias'


--------------------------------------------------------------------------------

.. _form_validateEmail:

validateEmail
================================================================================

.. code-block:: typescript

  EvanForm.validateEmail(email);

Checks for an valid email address.

----------
Parameters
----------

#. ``email`` - ``string``: String that should be checked

-------
Returns
-------

``boolean``: true if valid email, false if not

-------
Example
-------

.. code-block:: typescript

  this.email = new FormControl(
    'email',
    '',
    this,
    function(vueInstance: ContactAddComponent, form: ContactFormInterface) {
      if (!EvanForm.validateEmail(this.value)) {
        return 'invalid-email';
      } else {
        return true;
      }
    }
  });

  this.email.value = 'test_teeeest@!@.de';
  console.log(this.email.error);
  // 'invalid-email'

--------------------------------------------------------------------------------

.. _form_validateEthAddress:

validateEthAddress
================================================================================

.. code-block:: typescript

  EvanForm.validateEthAddress(address);

Checks for an valid eth address. (e.g.: '0x1813587e095cDdfd174DdB595372Cb738AA2753A')

----------
Parameters
----------

#. ``address`` - ``string``: String that should be checked

-------
Returns
-------

``boolean``: true if valid address, false if not

-------
Example
-------

.. code-block:: typescript

  this.accountId = new FormControl(
    'accountId',
    '',
    this,
    function(vueInstance: ContactAddComponent, form: ContactFormInterface) {
      if (!EvanForm.validateEthAddress(this.value)) {
        return 'invalid-address';
      } else {
        return true;
      }
    }
  });

  this.accountId.value = '0xhello';
  console.log(this.accountId.error);
  // 'invalid-address'

--------------------------------------------------------------------------------

.. _evanForm_constructor:

constructor
================================================================================

.. code-block:: typescript

  new EvanForm(options);

Creates a new EvanForm instance.

----------
Parameters
----------

#. ``vueInstance`` - ``any``: options for EvanForm constructor.
#. ``controls`` - ``{ [s: string]: EvanFormControlOptions }``: Object of controls that should be added. Key represents the name of the control, all other parameters that can be passed to a form control can be added too (validate, error, value, ...).

  #. ``name`` - ``string``: Form control name (will be passed automatically using controlKey)
  #. ``value`` - ``any``: initial control value
  #. ``vueInstance`` - ``Vue``: Original vue instance to directly access component references within the control
  #. ``validate`` - ``Function``: Runs the within the constructor provided validate function. The provided function should should return true, if everything is fine. Should return false, string, object, ... to mark the formControl as invalid and to set the internal error parameter. The function can also be return a Promise. During the asynchronious validation is running, the validating flag is set to true.
  #. ``uiSpecs`` - `EvanFormControl uiSpecs <./formControl.html>`__: Optional object that defines ui specifications for automatic formular rendering


-------
Returns
-------

``EvanForm`` instance

-------
Example
-------
Please have a look at the basic example `basic example <./evanForm.html#example>`__




--------------------------------------------------------------------------------

.. _form_validateControls:

validateControls
================================================================================

.. code-block:: typescript

  form.validateControls();

Iterate through all controls, checks if they are valid and sets the form `isValid` parameter. This function will be runned automatically by running the controls validate function. As a result of this, you can simply change the control values and the control and the form will be validated.

-------
Example
-------

.. code-block:: typescript

  form.alias.value = '';
  console.log(form.isValid)
  // false




--------------------------------------------------------------------------------

.. _form_addControl:

addControl
================================================================================

.. code-block:: typescript

  form.addControl(controlKey, control);

Function description

----------
Parameters
----------

#. ``controlKey`` - ``string``: name of the control
#. ``control`` - ``EvanFormControlOptions``: control options
  #. ``name`` - ``string``: Form control name (will be passed automatically using controlKey)
  #. ``value`` - ``any``: initial control value
  #. ``vueInstance`` - ``Vue``: Original vue instance to directly access component references within the control
  #. ``validate`` - ``Function``: Runs the within the constructor provided validate function. The provided function should should return true, if everything is fine. Should return false, string, object, ... to mark the formControl as invalid and to set the internal error parameter. The function can also be return a Promise. During the asynchronious validation is running, the validating flag is set to true.

-------
Example
-------

.. code-block:: typescript

  this.contactForm.addControl('accountId', {
    value: '',
    validate: function(vueInstance: ContactAddComponent, form: ContactFormInterface) {
      if (!EvanForm.validEthAddress(this.value)) {
        return '_addressbook.contact-form.accountId.error-invalid';
      } else {
        return true;
      }
    }
  });




--------------------------------------------------------------------------------

.. _form_removeControl:

removeControl
================================================================================

.. code-block:: typescript

  form.removeControl(controlKey);

Removes a control from the controlKeys list and from the control instance. Also runs validateControls to ensure latest validation status.

----------
Parameters
----------

#. ``controlKey`` - ``string``: controlKey of the control (e.g.: alias)

-------
Example
-------

.. code-block:: typescript

  this.contactForm.addControl('accountId')

  console.log(this.contactForm.accountId.value)
  // throws error, accountId is not available
