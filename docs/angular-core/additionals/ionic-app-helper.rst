================
ionic-app-helper
================

This collection of functions helps you to handle nested ionic angular application starting. Each of the following functions are exposed by the angular-core module and can be imported using the following mechanism:

.. code-block:: typescript

  import {
    createIonicAppElement,
    referenceApplicationRef,
    startAngularApplication,
    stopAngularApplication,
  } from 'angular-core';

createIonicAppElement
referenceApplicationRef
startAngularApplication
stopAngularApplication

--------------------------------------------------------------------------------

.. _angular_core_ionic_app_helper_createIonicAppElement:

createIonicAppElement
================================================================================

.. code-block:: typescript

  createIonicAppElement(container, name);

creates an ionic app container element, appends the dbcp name as id, add evan class names and sets the 'angular-application-ref' property to know, whichs runtime reference needs to deleted later.

----------
Parameters
----------

#. ``container`` - ``Element``: container of the application that should be  bootstrapped
#. ``name`` - ``string``: DBCP.public.name

-------
Returns
-------

``Element``: returns the new ionic-app element

-------
Example
-------

.. code-block:: typescript

  export async function startDApp(container, dbcpName) {
    const ionicAppEl = createIonicAppElement(container, dbcpName);

    await startAngularApplication(DashboardModule, getRoutes());

    container.appendChild(ionicAppEl);
  }




--------------------------------------------------------------------------------

.. _angular_core_ionic_app_helper_referenceApplicationRef:

referenceApplicationRef
================================================================================

.. code-block:: typescript

  referenceApplicationRef(applicationRef, elementRef);

Is used to cache an angular application ref to global context, to be able to clear everything correct. This is used in combination with the `BootstrapComponent <https://github.com/evannetwork/angular-core/blob/master/src/components/bootstrap-component/bootstrap-component.ts>`_ of the angular-core.

----------
Parameters
----------

#. ``applicationRef`` - ``ApplicationRef``: Angular application ref
#. ``elementRef`` - ``Element``: element of the application to handle the applicationRefID

-------
Example
-------

.. code-block:: typescript

  referenceApplicationRef(this.applicationRef, nativeElement);




--------------------------------------------------------------------------------

.. _angular_core_ionic_app_helper_startAngularApplication:

startAngularApplication
================================================================================

.. code-block:: typescript

  startAngularApplication(AppModule, routes);

Starts an angular module within a container and applies root routes.

----------
Parameters
----------

#. ``AppModule`` - ``any``: Angular module definition
#. ``routes`` - ``Routes``: Angular 5 route definitions

-------
Returns
-------

``any``: returns platformBrowser.bootstrapModuleFactory result

-------
Example
-------

.. code-block:: typescript

  export async function startDApp(container, dbcpName) {
    const ionicAppEl = createIonicAppElement(container, dbcpName);

    await startAngularApplication(DashboardModule, getRoutes());

    container.appendChild(ionicAppEl);
  }




--------------------------------------------------------------------------------

.. _angular_core_ionic_app_helper_stopAngularApplication:

stopAngularApplication
================================================================================

.. code-block:: typescript

  stopAngularApplication(container);

Stops an angular application using the element reference that were created by createIonicAppElement.

----------
Parameters
----------

#. ``container`` - ``Element``: container of the application

-------
Example
-------

.. code-block:: typescript

  // for stopping of all ionic angular applications within the dom
  const appElements = document.getElementsByTagName('ion-app');
  for (let i = 0; i < appElements.length; i++) {
    stopAngularApplication(appElements[i].parentElement);
  }