============
dapp-wrapper
============

.. list-table:: 
   :widths: auto
   :stub-columns: 1

   * - Source
     - `dapp-wrapper <https://github.com/evannetwork/ui-dapps/tree/master/dapps/ui.libs/src/style/dapp-wrapper.scss>`__

Includes the complete styling for the evan.network dapp-wrapper, including left panel navigation, top bar status displays, responsive integration ... The styling is included into the `ui-core <https://github.com/evannetwork/ui-dapps/tree/develop/core/ui.libs>`__ to be able to reuse the styling within several frameworks like react or vue at the same time. Please have a look the `vue.js dapp-wrapper implementation <https://github.com/evannetwork/ui-dapps/tree/master/dapps/evancore.vue.libs/src/components/dapp-wrapper/dapp-wrapper.vue>`_ implementation.

  .. image:: ../../../images/core/dapp-wrapper.png
   :width: 800

For building secondary navigation structures, we suggest to use the `dapp-wrapper-level-2` styling. Just add a dom element with the specific class to your dapp-wrappers content and it will be shown as an white panel. By using the evan `nav list design <../../../core/ui.libs/styling/buttons.html>`__, you can simply add navigation entries to the dapp-wrapper-level-2. (`vue.js dapp-wrapper-level-2 implementation <https://github.com/evannetwork/ui-dapps/tree/master/dapps/evancore.vue.libs/src/components/dapp-wrapper-level-2/dapp-wrapper-level-2.vue>`_).


  .. image:: ../../../images/core/dapp-wrapper-level-2.png
   :width: 400
