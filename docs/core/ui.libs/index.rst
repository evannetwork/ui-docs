=======
ui.libs
=======

.. list-table:: 
   :widths: auto
   :stub-columns: 1

   * - Source
     - `ui.libs <https://github.com/evannetwork/ui-core/tree/master/dapps/ui.libs>`__

This project include general and global, framework independent (without angular, vue, react, ...) evan.network functionallities and bootstrap configured stylings. Using this library, generalized evan.network applications can be build. The style includes the `evan.bootstrap.libs <https://github.com/evannetwork/ui-core/tree/master/dapps/evan.bootstrap.libs>`__ definition. The full bootstrap configurations are enhanced to be able to be configured during application runtime using css variables.

The following functionalities are included:
  - configuration values for runtime environments
  - Dispatcher & Queue Logic for a batch / step data synchronization
  - File handling
  - stylings (buttons, tables, steppers, contents, texts, ...)
  - styling css variables

Usage
=====

- dbcp.json

.. code-block:: json

  {
    "public": {
      "dapp": {
        "dependencies": {
          "ui.libs": "^1.4.0"
        }
      }
    }
  }

- package.json

.. code-block:: json

  {
    "dependencies": {
      "@evan.network/ui": "^1.4.0"
    },
  }

- typescript

  .. code-block:: ts

    import { Dispatcher, DispatcherInstance } from '@evan.network/ui';

- custom.scss
  
  .. code-block:: scss

    @import '~@evan.network/ui/dist/ui.libs.css';

Content
=======

.. toctree::
  :maxdepth: 2
  :glob:
  :caption: JS

  js


.. toctree::
  :maxdepth: 2
  :glob:
  :caption: Stylings

  stylings


.. toctree::
  :maxdepth: 2
  :glob:
  :caption: Assets

  assets
