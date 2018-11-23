=======
loading
=======

.. list-table:: 
   :widths: auto
   :stub-columns: 1

   * - Source
     - `loading <https://github.com/evannetwork/ui-dapp-browser/blob/develop/src/loading.ts>`__

A small `dapp-browser initial loading handler <https://github.com/evannetwork/ui-dapp-browser/blob/develop/src/app/loading.ts>`_. After a DApp was loaded, it needs to call the finishDAppLoading function to hides the initial loading screen. So each DApp can load smoothly in the background and can decide by it self, when it should be shown.

**Attention: During runtime and usage of the `angular-core </angular-core/index.html>` this function will do nothing,  You app is shown from the beginning of the loading progress.**






--------------------------------------------------------------------------------

.. _db_loading_finishDAppLoading:

finishDAppLoading
================================================================================

.. code-block:: typescript

  loading.finishDAppLoading();

Hides the initial loading that is embedded to the root dapp html page. => It will disappear smooth and will be removed when animation is over

-------
Example
-------

.. code-block:: typescript

  loading.finishDAppLoading();

Usage Example: https://github.com/evannetwork/ui-core-dapps/blob/8e26a55a98bcf638ad13e472d5b3a6eb82f587a9/dapps/dashboard/src/components/dashboard/dashboard.ts#L60