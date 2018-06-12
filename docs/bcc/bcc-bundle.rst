===============================
blockchain-core frontend bundle
===============================

The |source bcc_bundlejs|_ is similar to the blockchain-core runtime and its build to handle several UI steps including blockchain-core instance without account interactions, blockchain-core instance including account id for profile interactions and blockchain-core instance to interact with business centers. It exposes the following Runtime parameters and several functions to create, handle and overwrite them:

- CoreRuntime: |source CoreInstance|_
- ProfileRuntime: |source ProfileInstance|_
- BCRuntime: |source BCInstance|_

--------------------------------------------------------------------------------

Interface: SolcInterface
========================
.. _db_bcc_SolcInterface:

Used to describe smart contract resolve for bundles, ...

----------
Parameters
----------

#. ``getContracts`` - ``any``: Returns compiled contracts object.

-------
Example
-------

.. code-block:: typescript

  solc.getContracts();
  // {
  //   "AbstractDescribed": {
  //     "interface": "[...]"
  //   },
  //   "AbstractENS": {
  //     "interface": "[...]"
  //   },
  //   ...
  // }

--------------------------------------------------------------------------------

Interface: CoreBundle
=====================
.. _db_bcc_CoreBundle:

Core bundle specification (the full result of the |source bcc_bundlejs|_ file).

----------
Parameters
----------
#. |source createCore|_ - ``Function``;
#. |source createAndSetCore|_ - ``Function``;
#. ``ContractLoader`` - |source contract_loader|_;
#. ``CryptoProvider`` - |source CryptoProvider|_;
#. ``Description`` - |source Description|_;
#. ``DfsInterface`` - |source dfs_interface|_;
#. ``EventHub`` - |source EventHub|_;
#. ``Executor`` - |source executor|_;
#. ``Ipfs`` - |source Ipfs|_;
#. ``NameResolver`` - |source name_resolver|_;
#. ``Unencrypted`` - |source Unencrypted|_;
#. ``CoreRuntime`` - |source CoreInstance|_;
#. |source isAccountOnboarded|_ - ``Function``;
#. ``IpfsRemoteConstructor`` - |source ipfs_api|_: require('ipfs-api');
#. ``keystore`` - |source keyStore|_: require('eth-lightwallet/lib/keystore');
#. ``Mnemonic`` - |source Mnemonic|_: require('bitcore-mnemonic');
#. ``KeyProviderInterface`` - |source KeyProviderInterface|_;
#. ``KeyProvider`` - |source KeyProvider|_;

--------------------------------------------------------------------------------

Interface: CoreBundleOptions
============================
.. _db_bcc_CoreBundleOptions:

Used to create a new CoreInstance.

----------
Parameters
----------

#. ``web3`` - |source Web3|_: web3 instance;
#. ``solc`` - |source SolcInterface|_: solc to get contracts;
#. ``config`` - |source config|_: blockchain-core configuration;
#. ``executor`` -  |source executor|_ (optional): blockchain-core executor instance;
#. ``contractLoader`` -  |source contract_loader|_ (optional): blockchain-core contract loader instance;
#. ``description`` -  |source description|_ (optional): blockchain-core description instance;
#. ``dfs`` -  |source dfs_interface|_ (optional): blockchain-core dfs interface instance;
#. ``dfsRemoteNode`` - |source ipfs_api|_ (optional): require('ipfs-api')
#. ``nameResolver`` - |source name_resolver|_ (optional): blockchain-core name resolver instance;
#. ``ipfsCache`` - |source ipfs_cache|_ (optional): ipfs cache specification;

--------------------------------------------------------------------------------

Interface: CoreInstance
=======================
.. _db_bcc_CoreInstance:

Initialized core bundle for blockchain interaction without account specification. 

----------
Parameters
----------

#. ``web3`` - |source Web3|_: web3 instance;
#. ``description`` -  |source description|_ (optional): blockchain-core description instance;
#. ``nameResolver`` - |source name_resolver|_ (optional): blockchain-core name resolver instance;
#. ``dfs`` -  |source dfs_interface|_ (optional): blockchain-core dfs interface instance;
#. ``contractLoader`` -  |source contract_loader|_ (optional): blockchain-core contract loader instance;
#. ``executor`` -  |source executor|_ (optional): blockchain-core executor instance;
#. ``solc`` - |source SolcInterface|_: solc to get contracts;
#. ``contracts`` - |source smart_contracts|_: precompiled smart-contracts specification;
#. ``config`` - |source config|_: blockchain-core configuration;

--------------------------------------------------------------------------------

Interface: ProfileBundle
========================
.. _db_bcc_ProfileBundle:

Options to initialize a new |source ProfileInstance|_.

----------
Parameters
----------
#. |source create|_ - ``source Function``;
#. |source createAndSet|_ - ``Function``;
#. ``ProfileRuntime`` - |source ProfileInstance|_;
#. ``Aes`` - |source Aes|_;
#. ``Ipld`` - |source Ipld|_;
#. ``KeyExchange`` - |source KeyExchange|_;
#. ``Logger`` - |source Logger|_;
#. ``Mailbox`` - |source Mailbox|_;
#. ``Onboarding`` - |source Onboarding|_;
#. ``Profile`` - |source Profile|_;
#. ``RightsAndRoles`` - |source RightsAndRoles|_;
#. ``Sharing`` - |source Sharing|_;
#. ``SignerExternal`` - |source SignerExternal|_;
#. ``SignerInternal`` - |source SignerInternal|_;

--------------------------------------------------------------------------------

Interface: ProfileBundleOptions
===============================
.. _db_bcc_ProfileBundleOptions:

Options to initialize a new |source ProfileInstance|_.

----------
Parameters
----------
#. ``CoreBundle`` - |source CoreBundle|_;
#. ``coreOptions`` - |source CoreBundleOptions|_;
#. ``accountId`` - ``string``: account id to initialize the profile instance for;
#. ``signer`` - |source SignerInternal|_ or |source SignerExternal|_;
#. ``keyProvider`` - |source KeyProvider|_;

--------------------------------------------------------------------------------

Interface: ProfileInstance
==========================
.. _db_bcc_ProfileInstance:

Bundled runtime for blockchain-core interaction for a specific account.

----------
Parameters
----------
#. ``ipldInstance`` - |source Ipld|_;
#. ``keyExchange`` - |source KeyExchange|_;
#. ``mailbox`` - |source Mailbox|_;
#. ``profile`` - |source Profile|_;
#. ``sharing`` - |source Sharing|_;
#. ``dataContract`` - |source DataContract|_;
#. ``keyProvider`` - |source KeyProvider|_;
#. ``coreInstance`` - |source CoreInstance|_;

--------------------------------------------------------------------------------

Interface: BCBundleOptions
==========================
.. _db_bcc_BCBundleOptions:

Bundle Options for the BCInstance.

----------
Parameters
----------
#. ``ensDomain`` - ``string``: ens domain for the business center that should be initialized;
#. ``ProfileBundle`` - |source ProfileBundle|_;

--------------------------------------------------------------------------------

Interface: BCInstance
=====================
.. _db_bcc_BCInstance:

Bundled runtime for blockchain-core interaction for a specific account and business center.

----------
Parameters
----------
#. ``ensDomain`` - ``string``: ens domain for the business center that should be initialized;
#. ``bcAddress`` - ``string``: contract addess of the business center;
#. ``businessCenter`` - ``source any``: business center contract instance (CoreRuntime.contractLoader.loadContract('BusinessCenter', bcAddress));
#. ``bcRoles`` - |source RightsAndRoles|_;
#. ``ipld`` - |source Ipld|_;
#. ``bcProfiles`` - |source BusinessCenterProfile|_;
#. ``description`` - ``any``: loaded description from the ens address of the bc;
#. ``dataContract`` - |source DataContract|_;

--------------------------------------------------------------------------------

.. _db_bcc_createCore:

createCore
================================================================================

.. code-block:: typescript

  bcc.createCore(options);

Creates a new CoreInstance

----------
Parameters
----------

#. ``options`` - |source CoreBundleOptions|_: The core options

-------
Returns
-------

``CoreInstance``: new CoreInstance instance

-------
Example
-------

.. code-block:: typescript

  bcc.createCore(options);


--------------------------------------------------------------------------------

.. _db_bcc_createAndSetCore:

createAndSetCore
================================================================================

.. code-block:: typescript

  bcc.createAndSetCore(options);

Creates a new CoreInstance and update the CoreInstance export.

----------
Parameters
----------

#. ``options`` - |source CoreBundleOptions|_: The core options

-------
Returns
-------

``CoreInstance``: new CoreInstance instance

-------
Example
-------

.. code-block:: typescript

  bcc.createCore(options);

Usage Example: https://github.com/evannetwork/dapp-browser/blob/develop/src/app/bcc/bcc.ts


--------------------------------------------------------------------------------

.. _db_bcc_setCore:

setCore
================================================================================

.. code-block:: typescript

  bcc.setCore(coreInstance);

Overwrite the current CoreInstance

----------
Parameters
----------

#. ``coreInstance`` - |source CoreInstance|_: core instance to overwrite

-------
Example
-------

.. code-block:: typescript

  bcc.setCore(CoreInstance)

Usage Example: https://github.com/evannetwork/dapp-browser/blob/develop/src/app/bcc/bcc.ts


--------------------------------------------------------------------------------

.. _db_bcc_create:

create
================================================================================

.. code-block:: typescript

  bcc.create(options);

Creates a new ProfileInstance

----------
Parameters
----------

#. ``options`` - |source ProfileBundleOptions|_: profile bundle options

-------
Returns
-------

|source ProfileInstance|_ : the new profile instance

-------
Example
-------

.. code-block:: typescript

  bcc.create(options)

Usage Example: https://github.com/evannetwork/angular-core/blob/develop/src/services/bcc/bcc.ts




--------------------------------------------------------------------------------

.. _db_bcc_createAndSet:

createAndSet
================================================================================

.. code-block:: typescript

  bcc.createAndSet(options);

Create a new ProfileInstance and update the ProfileInstance export.

----------
Parameters
----------

#. ``options`` - |source ProfileBundleOptions|_: profile bundle options

-------
Returns
-------

|source ProfileInstance|_ : the new profile instance

-------
Example
-------

.. code-block:: typescript

  bcc.create(options)

Usage Example: https://github.com/evannetwork/angular-core/blob/develop/src/services/bcc/bcc.ts




--------------------------------------------------------------------------------

.. _db_bcc_createBC:

createBC
================================================================================

.. code-block:: typescript

  bcc.createBC(options);

Create a new BCInstance.

----------
Parameters
----------

#. ``options`` - |source BCBundleOptions|_: options for the business center

-------
Returns
-------

``BCInstance`` : the new bc instance

-------
Example
-------

.. code-block:: typescript

  bcc.createBC(options)

Usage Example: https://github.com/evannetwork/angular-core/blob/develop/src/services/bcc/bc.ts




--------------------------------------------------------------------------------

.. _db_bcc_createAndSetBC:

createAndSetBC
================================================================================

.. code-block:: typescript

  bcc.createAndSetBC(options);

Creates and set BCInstance.

----------
Parameters
----------

#. ``options`` - |source BCBundleOptions|_: options for the business center

-------
Returns
-------

``BCInstance`` : the new bc instance

-------
Example
-------

.. code-block:: typescript

  bcc.createBC(options)

Usage Example: https://github.com/evannetwork/angular-core/blob/develop/src/services/bcc/bc.ts




--------------------------------------------------------------------------------

.. _db-bcc_isAccountOnboarded:

isAccountOnboarded
================================================================================

.. code-block:: typescript

  bcc.isAccountOnboarded(accountId);

Function description

----------
Parameters
----------

#. ``accountId`` - ``string``: account id to test

-------
Returns
-------

``Promise`` returns ``boolean``: True if account onboarded, False otherwise

-------
Example
-------

.. code-block:: typescript

  bcc.isAccountOnboarded('0x000...');
  // returns true / false


--------------------------------------------------------------------------------

.. required for building markup
.. |source bcc_bundlejs| replace:: ``blockchain-core frontend bundle``
.. _source bcc_bundlejs: https://github.com/evannetwork/blockchain-core/blob/develop/src/bundles/bcc/bcc.ts

.. |source CoreBundle| replace:: ``CoreBundle``
.. _source CoreBundle: /bcc/bcc-bundle.html#corebundle

.. |source CoreBundleOptions| replace:: ``CoreBundleOptions``
.. _source CoreBundleOptions: /bcc/bcc-bundle.html#corebundleoptions

.. |source CoreInstance| replace:: ``CoreInstance``
.. _source CoreInstance: /bcc/bcc-bundle.html#coreinstance

.. |source ProfileInstance| replace:: ``ProfileInstance``
.. _source ProfileInstance: /bcc/bcc-bundle.html#profileinstance

.. |source BCInstance| replace:: ``BCInstance``
.. _source BCInstance: /bcc/bcc-bundle.html#bcinstance

.. |source BCBundleOptions| replace:: ``BCBundleOptions``
.. _source BCBundleOptions: /bcc/bcc-bundle.html#bcbundleoptions

.. |source ProfileBundle| replace:: ``ProfileBundle``
.. _source ProfileBundle: /bcc/bcc-bundle.html#profilebundle

.. |source ProfileBundleOptions| replace:: ``ProfileBundleOptions``
.. _source ProfileBundleOptions: /bcc/bcc-bundle.html#profilebundleoptions

.. |source SolcInterface| replace:: ``SolcInterface``
.. _source SolcInterface: /bcc/bcc-bundle.html#solcionterface

.. |source createCore| replace:: ``createCore``
.. _source createCore: /bcc/bcc-bundle.html#createcore

.. |source createAndSetCore| replace:: ``createAndSetCore``
.. _source createAndSetCore: /bcc/bcc-bundle.html#createandsetcore

.. |source create| replace:: ``create``
.. _source create: /bcc/bcc-bundle.html#create

.. |source createAndSet| replace:: ``createAndSet``
.. _source createAndSet: /bcc/bcc-bundle.html#createandset

.. |source Web3| replace:: ``Web3``
.. _source Web3: https://github.com/ethereum/web3.js

.. |source config| replace:: ``config``
.. _source config: /dapp-browser/config.html

.. |source executor| replace:: ``Executor``
.. _source executor: https://github.com/evannetwork/blockchain-core/blob/develop/docs/blockchain/executor.rst

.. |source contract_loader| replace:: ``ContractLoader``
.. _source contract_loader: https://github.com/evannetwork/blockchain-core/blob/develop/docs/contracts/contract-loader.rst

.. |source description| replace:: ``Description``
.. _source description: https://github.com/evannetwork/blockchain-core/blob/develop/docs/blockchain/description.rst

.. |source dfs_interface| replace:: ``DfsInterface``
.. _source dfs_interface: https://github.com/evannetwork/blockchain-core/blob/develop/docs/dfs/dfs-interface.rst

.. |source ipfs_api| replace:: ``IpfsRemoteConstructor``
.. _source ipfs_api: https://github.com/ipfs/js-ipfs-api

.. |source name_resolver| replace:: ``NameResolver``
.. _source name_resolver: https://github.com/evannetwork/blockchain-core/blob/develop/docs/blockchain/name-resolver.rst

.. |source ipfs_cache| replace:: ``IpfsCache``
.. _source ipfs_cache: /dapp-browser/ipfs-cache.html

.. |source smart_contracts| replace:: ``SmartContracts``
.. _source smart_contracts: https://github.com/evannetwork/smart-contracts

.. |source CryptoProvider| replace:: ``CryptoProvider``
.. _source CryptoProvider: https://github.com/evannetwork/blockchain-core/blob/develop/docs/encryption/crypto-provider.rst

.. |source EventHub| replace:: ``EventHub``
.. _source EventHub: https://github.com/evannetwork/blockchain-core/blob/develop/docs/blockchain/event-hub.rst

.. |source Ipfs| replace:: ``Ipfs``
.. _source Ipfs: https://github.com/evannetwork/blockchain-core/blob/develop/docs/dfs/ipfs.rst

.. |source Unencrypted| replace:: ``Unencrypted``
.. _source Unencrypted: https://github.com/evannetwork/blockchain-core/blob/develop/docs/encryption/cryptor-unencrypted.rst

.. |source isAccountOnboarded| replace:: ``isAccountOnboarded``
.. _source isAccountOnboarded: /bcc/bcc-bundle.html#isaccountonboarded

.. |source keyStore| replace:: ``KeyStore``
.. _source keyStore: https://github.com/ConsenSys/eth-lightwallet/blob/master/lib/keystore.js

.. |source Mnemonic| replace:: ``Mnemonic``
.. _source Mnemonic: https://github.com/bitpay/bitcore-mnemonic

.. |source KeyProviderInterface| replace:: ``KeyProviderInterface``
.. _source KeyProviderInterface: https://github.com/evannetwork/blockchain-core/blob/develop/docs/encryption/key-provider.rst

.. |source KeyProvider| replace:: ``KeyProvider``
.. _source KeyProvider: https://github.com/evannetwork/blockchain-core/blob/develop/docs/encryption/key-provider.rst

.. |source SignerInternal| replace:: ``SignerInternal``
.. _source SignerInternal: https://github.com/evannetwork/blockchain-core/blob/develop/docs/blockchain/signer.rst

.. |source SignerExternal| replace:: ``SignerExternal``
.. _source SignerExternal: https://github.com/evannetwork/blockchain-core/blob/develop/docs/blockchain/signer.rst

.. |source Aes| replace:: ``Aes``
.. _source Aes: https://github.com/evannetwork/blockchain-core/blob/develop/docs/encryption/cryptor-aes.rst

.. |source Ipld| replace:: ``Ipld``
.. _source Ipld: https://github.com/evannetwork/blockchain-core/blob/develop/docs/dfs/ipld.rst

.. |source KeyExchange| replace:: ``KeyExchange``
.. _source KeyExchange: https://github.com/evannetwork/blockchain-core/blob/develop/docs/profile/key-exchange.rst

.. |source Logger| replace:: ``Logger``
.. _source Logger: https://github.com/evannetwork/blockchain-core/blob/develop/docs/common/logger.html

.. |source Mailbox| replace:: ``Mailbox``
.. _source Mailbox: https://github.com/evannetwork/blockchain-core/blob/develop/docs/profile/mailbox.rst

.. |source Onboarding| replace:: ``Onboarding``
.. _source Onboarding: https://github.com/evannetwork/blockchain-core/blob/develop/docs/profile/onboarding.rst

.. |source Profile| replace:: ``Profile``
.. _source Profile: https://github.com/evannetwork/blockchain-core/blob/develop/docs/profile/profile.rst

.. |source RightsAndRoles| replace:: ``RightsAndRoles``
.. _source RightsAndRoles: https://github.com/evannetwork/blockchain-core/blob/develop/docs/contracts/rights-and-roles.rst

.. |source Sharing| replace:: ``Sharing``
.. _source Sharing: https://github.com/evannetwork/blockchain-core/blob/develop/docs/contracts/sharing.rst

.. |source DataContract| replace:: ``DataContract``
.. _source DataContract: https://github.com/evannetwork/blockchain-core/blob/develop/docs/contracts/data-contract.rst

.. |source BusinessCenterProfile| replace:: ``BusinessCenterProfile``
.. _source BusinessCenterProfile: https://github.com/evannetwork/blockchain-core/blob/develop/docs/profile/business-center-profile.rst
