================
EvanAlertService
================

`Ionic AlertController <https://ionicframework.com/docs/api/components/alert/AlertController/>`_ wrapper for easier usage.

--------------------------------------------------------------------------------

showAlert
================================================================================

.. code-block:: typescript

  alertService.showAlert(title, message, buttons, inputs);

Ionic AlertController.create wrapper to handle translations of the form.

----------
Parameters
----------

#. ``title`` - ``string|any``: Title    'title'   || { key: 'title', translateOptions: { } }
#. ``message`` - ``string|any``: Message  'message' || { key: 'message', translateOptions: { } }
#. ``buttons`` - ``Array<any``: Buttons that should be display
#. ``inputs`` - ``Array<any>``: Inputs that should be displayed

-------
Returns
-------

``Alert``: this.alertCtrl.create result

-------
Example
-------

For a bigger example view showSubmitAlert

.. code-block:: typescript

  await this
    .alertService.showAlert(
      '_dappdapps.alert.validTitle',
      {
        key: '_dappdapps.alert.dappMessage',
        translateOptions: dapp
      }
    );


--------------------------------------------------------------------------------

showSubmitAlert
================================================================================

.. code-block:: typescript

  alertService.showSubmitAlert(arguments);

Function description

----------
Parameters
----------

#. ``title`` - ``string|any``: 'title' || { title: '', translateOptions: { } }
#. ``message`` - ``string|any``: 'message' || { title: '', translateOptions: { } }
#. ``cancelText`` - ``string``: 'cancelText' || { title: '', translateOptions: { } }
#. ``submitText`` - ``string``: 'submitText' || { title: '', translateOptions: { } }
#. ``inputs`` - ``Array<any>``: Inputs that should be displayed

-------
Returns
-------

``Promise`` returns ``any``: promise that is deployed on button reject / resolve

-------
Example
-------

.. code-block:: typescript

  await this
    .alertService.showSubmitAlert(
      '_dappdapps.alert.validTitle',
      {
        key: '_dappdapps.alert.dappMessage',
        translateOptions: dapp
      },
      'cancel',
      'submit'
    );




--------------------------------------------------------------------------------

.. _document_addDAppAlertStyle:

addDAppAlertStyle
================================================================================

.. code-block:: typescript

  alertService.addDAppAlertStyle(arguments);

Adds an temporary style to show a better looking alert using the definition colors and img.

----------
Parameters
----------

#. ``DApp bookmark definition`` - ``any``: DApp bookmark definition

-------
Example
-------
Reference Implementation: `Favorites DApp <https://github.com/evannetwork/ui-core-dapps/blob/develop/dapps/favorites/src/components/dapp-add/dapp-add.ts>`_

.. code-block:: typescript

  this.alertService.addDAppAlertStyle(this.dapps[dappKey]);




--------------------------------------------------------------------------------

.. _document_removeDAppAlertStyle:

removeDAppAlertStyle
================================================================================

.. code-block:: typescript

  alertService.removeDAppAlertStyle(definition);

Remove an temporary style that was used for the DApp definition style.

----------
Parameters
----------

#. ``definition`` - ``any``: DApp bookmark definition

-------
Example
-------
Reference Implementation: `Favorites DApp <https://github.com/evannetwork/ui-core-dapps/blob/develop/dapps/favorites/src/components/dapp-add/dapp-add.ts>`_

.. code-block:: typescript

  alertService.removeDAppAlertStyle(definition);
