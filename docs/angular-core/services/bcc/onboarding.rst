=====================
EvanOnboardingService
=====================

Onboarding wrapper service, with some utility functions. Primary used by the core-dapps/onboarding Dapp.

--------------------------------------------------------------------------------

isOnboarded
================================================================================

.. code-block:: typescript

  onboarding.isOnboarded(accountId);

Check if the account id is onboarded. Uses a custom created blockchain-core profile => not depending on global core instance

----------
Parameters
----------

#. ``accountId`` - ``string``: account id to check

-------
Returns
-------

``boolean``: True if onboarded, False otherwise.

-------
Example
-------

.. code-block:: typescript

  await onboardingService.isOnboarded();




--------------------------------------------------------------------------------

.. _document_getOnboardingQueryParams:

getOnboardingQueryParams
================================================================================

.. code-block:: typescript

  onboardingService.getOnboardingQueryParams();

Get the current onboarding params with default values.

-------
Returns
-------

``any``: Original query parameters from the page from which we were redirected to onboarding.

-------
Example
-------

.. code-block:: typescript

  // https://dashboard.evan.network/#/dashboard.evan
  onboardingService.getOnboardingQueryParams();
  // => { "origin": "dashboard.evan" }




--------------------------------------------------------------------------------

.. _document_finishOnboarding:

finishOnboarding
================================================================================

.. code-block:: typescript

  initializedModule.finishOnboarding();

Finish onboarding process.

- update blockchain-core for current provider and accountId
- navigate to dashboard or latest route

-------
Example
-------

.. code-block:: typescript

  onboardingService.finishOnboarding();




--------------------------------------------------------------------------------

goToOnboarding
================================================================================

.. code-block:: typescript

  onboardingService.goToOnboarding();

Navigate to onboarding.

-------
Example
-------

.. code-block:: typescript

  onboardingService.goToOnboarding();