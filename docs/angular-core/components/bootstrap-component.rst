==================
BootstrapComponent
==================

Generic evan.network Angular 5 featured DApp bootstrap component.
  - helpers for dynamic routing configurations for dynamic parent routes
  - registers referenceApplicationRef for correct deleting later
  - uses referenceApplicationRef to register angular appliction runtime to `ionic-app-helper </angular-core/additional/ionic-app-helper.html#referenceapplicationref>`_ to be able to destroy the angular context correctly after app stopping

**Use this everytime to bootstrap your Angular applications.**

-----
Usage
-----
Used in every feature `DApp module <https://evannetwork.github.io/dapps/angular/hello-world>`_.

.. code-block:: typescript

  imports.push(IonicModule.forRoot(BootstrapComponent, {
    mode: 'md'
  }));