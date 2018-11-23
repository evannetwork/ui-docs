===========
evanGlobals
===========

.. list-table:: 
   :widths: auto
   :stub-columns: 1

   * - Source
     - `evanGlobals <https://github.com/evannetwork/ui-dapp-browser/blob/develop/src/app/main.ts>`__

The `evan globals <https://github.com/evannetwork/ui-dapp-browser/blob/develop/src/app/main.ts>`_ are a runtime object that handles global references for internal functions within the dapp-browser. This is nessecary to remove any dapp-browser dependency from the window object. Maybe this collection will help you.

----------
Parameters
----------

#. ``CoreBundle`` - |source CoreBundle|_: bcc exported CoreBundle;
#. ``CoreRuntime`` - |source CoreInstance|_: bcc active CoreInstance;
#. ``SmartContracts`` - |source smart_contracts|_: Initialized build Object of the SmartContracts;
#. ``System`` - |source SystemJS|_: global DApp browser SystemJS for direct use (normally you will use import { } from 'module-name', because a using DBCP and |source loadDApp|_ functions, SystemJS imports will be registered);
#. ``devMode`` - |source devMode|_: array of dev mode available applications;
#. ``ipfsCatPromise`` - |source ipfsCatPromise|_: promisified ipfs cat function;
#. ``restIpfs`` - |source restIpfs|_: restIpfs export;

.. required for building markup

.. |source CoreBundle| replace:: ``CoreBundle``
.. _source CoreBundle: /bcc/bcc-bundle.html#corebundle

.. |source CoreInstance| replace:: ``CoreInstance``
.. _source CoreInstance: /bcc/bcc-bundle.html#coreinstance

.. |source SystemJS| replace:: ``SystemJS``
.. _source SystemJS: https://github.com/systemjs/systemjs

.. |source System| replace:: ``System``
.. _source System: ../dapp-browser/System

.. |source smart_contracts| replace:: ``SmartContracts``
.. _source smart_contracts: https://github.com/evannetwork/smart-contracts

.. |source loadDApp| replace:: ``dapp.loadDApp``
.. _source loadDApp: ../dapp-browser/dapp.html#loaddappdependencies

.. |source devMode| replace:: ``devMode``
.. _source devMode: ../dapp-browser/utils.html#devMode

.. |source ipfsCatPromise| replace:: ``ipfsCatPromise``
.. _source ipfsCatPromise: ../dapp-browser/ipfs.html#ipfscatpromise

.. |source restIpfs| replace:: ``restIpfs``
.. _source restIpfs: ../dapp-browser/rest-ipfs.html