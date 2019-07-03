====================
DAppLoadingComponent
====================

.. list-table:: 
   :widths: auto
   :stub-columns: 1

   * - Source
     - `loading <https://github.com/evannetwork/ui-vue/tree/master/dapps/evancore.vue.libs/src/components/loading>`__
   * - Selector
     - ``evan-loading``
   * - style
     -  `breadcrumbs <https://getbootstrap.com/docs/4.3/components/spinners>`__

replaceme

#. ``replaceme`` - ``Array<{ name: string, fallbackName: string, path: string }>``: active route, splitted by hash and prepared using the following params: name, fallbackName, path

Props
=====

#. ``replaceme`` - ``string``: 


Example
=======

- component usage

  :: vue

    <evan-loading v-if="loading"></evan-loading>
    <div class="container-wide"
      ...
    </div>

- custom loading

  .. code-block:: html

    <div class="evan-loading w-100 h-100 pt-5 pb-5 text-center"
      v-if="loading">
      <div class="spinner-border text-secondary"></div>
    </div>
    <div class="container-wide"
      ...
    </div>

- small loading (e.g. within buttons)

  .. code-block:: html

    <button class="btn btn-rounded btn-primary">
      {{ `save` | translate }}
      <div class="spinner-border spinner-border-sm text-light mr-3"
        v-if="loading">
      </div>
      <i class="mdi mdi-arrow-right label ml-3"
        v-else>
      </i>
    </button>

View Example
============

.. image:: ../../../images/vue/loading.png
   :width: 600

.. image:: ../../../images/vue/loading-button.png
   :width: 300