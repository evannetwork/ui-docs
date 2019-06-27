====================
bootstrap-theme-evan
====================

.. list-table:: 
   :widths: auto
   :stub-columns: 1

   * - Source
     - `bootstrap-theme-evan <https://github.com/evannetwork/ui-core/tree/master/dapps/evan.bootstrap.libs>`__


Usage
=====
The full `bootstrap <https://getbootstrap.com/>`__ configurations are enhanced to be able to be configured during application runtime using css variables. Have a look at the following variables list that is defined within the `@evan.network/ui variables <https://github.com/evannetwork/ui-core/blob/master/dapps/ui.libs/src/style/definitions/evan.theme.scss>`__

- dbcp.json

.. code-block:: json

  {
    "public": {
      "dapp": {
        "dependencies": {
          "evan.bootstrap.libs": "^4.3.1"
        }
      }
    }
  }

- package.json

.. code-block:: json

  {
    "dependencies": {
      "@evan.network/bootstrap-theme-evan": "^4.3.1"
    },
  }

- custom.scss
  
.. code-block:: scss

  @import '~@evan.network/bootstrap-theme-evan/dist/evan.bootstrap.libs.css';


