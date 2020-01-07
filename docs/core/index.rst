====
core
====

.. list-table:: 
   :widths: auto
   :stub-columns: 1

   * - Source
     - `ui-dapps <https://github.com/evannetwork/ui-dapps>`__

All evan.network dapps and dapp libraries are included into the `ui-dapps <https://github.com/evannetwork/ui-dapps>`__.

DApp Wrappers
=============
DApp wrappers for the blockchain core, the smart contracts core, ... are constructed simply, to exclude the wanted library from build and map the correct original package name. E.g.: The @evan.network/api-blockchain-core library is published using the ens address `bcc.evan`. Within the DBCP of the using DApp, this lib is referenced within the dbcp.json as dependency. Within the application it self, `@evan.network/api-blockchain-core` can be imported normally using `import * as bcc from '@evan.network/api-blockchain-core'`.

Open Source libraries
=====================
The following open source library wrapper dapps are defined:

  - `evan.bootstrap.libs <https://github.com/evannetwork/ui-dapps/tree/master/dapps/evan.bootstrap.libs>`__
  - `materialicons.libs <https://github.com/evannetwork/ui-dapps/tree/master/dapps/materialicons.libs>`__
  - `themify.libs <https://github.com/evannetwork/ui-dapps/tree/master/dapps/themify.libs>`__
  - `d3.libs <https://github.com/evannetwork/ui-dapps/tree/master/dapps/d3.libs>`__
  - `fontawesome.libs <https://github.com/evannetwork/ui-dapps/tree/master/dapps/fontawesome.libs>`__
  - `moment.libs <https://github.com/evannetwork/ui-dapps/tree/master/dapps/moment.libs>`__
  - `dexie.libs <https://github.com/evannetwork/ui-dapps/tree/master/dapps/dexie.libs>`__
  - `lodash.libs <https://github.com/evannetwork/ui-dapps/tree/master/dapps/lodash.lib>`__

The `evan.bootstrap.libs` is a wrapper for `bootstrap V4.3 <https://getbootstrap.com/docs/4.3/getting-started/introduction>`__. All the variables are adjusted to be able to inserted via css variables. Have a look at the css variables to configure it: `ui.libs variables <./ui.libs/styling/variables.html>`__

evan.network libraries
======================
The following evan.network libraries are available:

  - `ui.libs <https://github.com/evannetwork/ui-dapps/tree/master/dapps/ui.libs>`__
  - `bcc <https://github.com/evannetwork/ui-dapps/tree/master/dapps/bcc>`__
  - `smartcontracts <https://github.com/evannetwork/ui-dapps/tree/master/dapps/smartcontracts>`__

