======
Alerts
======

Used to handle normal `ionic alerts <https://ionicframework.com/docs/components/#alert>`_, enriched for a more detailed view with better stylings.

-------
Example
-------
- Reference Implementation: `Favorites DApp - DApp add component <https://github.com/evannetwork/core-dapps/blob/develop/dapps/favorites/src/components/dapp-add/dapp-add.html>`_
- typescript using `alertService </angular-core/services/ui/alert.html>`_

.. code-block:: typescript

  async showValid(dapp: any): Promise<any> {
    this.alertService.addDAppAlertStyle(dapp);

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

    this.alertService.removeDAppAlertStyle(dapp.name);
  }

- html definition with translation
- Reference Implementation: `Favorites DApp I18N <https://github.com/evannetwork/core-dapps/blob/develop/dapps/favorites/src/i18n/en.ts>`_

::

  ...
  'validMessage': `
    <div class="advanced-alert">
      <div class="alert-img-container">
        <div class="alert-img evan-img-{{ name }}"></div>
      </div>
      <div class="alert-body">
        <h3>{{ name }}</h3>
        <span>{{ description }}</span>
      </div>
    </div>
  `
  ...

------------
View Example
------------

.. image:: /images/angular-sass/alert.png
   :width: 600
