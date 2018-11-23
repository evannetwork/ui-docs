==============
EvanBCCService
==============

.. list-table:: 
   :widths: auto
   :stub-columns: 1

   * - Source
     - `bcc <https://github.com/evannetwork/ui-angular-core/blob/develop/src/services/bcc/bcc.ts>`__

Core blockchain-core angular-core wrapper. Initializes and extends new runtimes from dapp-browser, when user unlocked successfully its account, to  handle correct user encryption keys and object instances

- ``passwordModalPromise`` - ``any``: wait for password dialog to be resolved;
- ``updateBCCPromise`` - ``any``: wait for bcc is updated to be resolved;

`BCCCore or BCCProfile </bcc/bcc-bundle.html>`_ exported runtime values. Mapped from e.g BCC.coreInstance.executor => this.executor

- ``config`` - |source config|_;
- ``rightsAndRoles`` - |source RightsAndRoles|_;
- ``web3`` - |source Web3|_;
- ``contractLoader`` - |source contract_loader|_;
- ``executor`` - |source executor|_;
- ``keyProvider`` - |source KeyProvider|_;
- ``description`` - |source description|_;
- ``nameResolver`` - |source name_resolver|_;
- ``ipldInstance`` - |source ipld|_;
- ``dfs`` - |source dfs_interface|_;
- ``mailbox`` - |source mailbox|_;
- ``keyExchange`` - |source keyExchange|_;
- ``profile`` - |source profile|_;
- ``sharing`` - |source sharing|_;
- ``cryptoProvider`` - |source cryptoProvider|_;
- ``CoreBundle`` - |source CoreBundle|_;
- ``ProfileBundle`` - |source ProfileBundle|_;
- ``dataContract`` - |source dataContract|_;




--------------------------------------------------------------------------------

initialize
================================================================================

.. code-block:: typescript

  bccService.initialize(passwordFunction);

Initialize the bcc service using a password unlocking function.

----------
Parameters
----------

#. ``passwordFunction`` - ``Function``: function that is used to unlock current lightwallet vault

-------
Returns
-------

``Promise`` returns ``void``: resolved when bcc was updated for the current profile

-------
Example
-------

.. code-block:: typescript

  await this.bcc.initialize((accountId) => this.bcc.globalPasswordDialog(accountId));





--------------------------------------------------------------------------------

copyCoreToInstance
================================================================================

.. code-block:: typescript

  bccService.copyCoreToInstance();

Copy BCC core object instances into the service this scope.

--------------------------------------------------------------------------------

copyCoreToInstance
================================================================================

.. code-block:: typescript

  bccService.copyProfileToInstance();

Copy BCC profile object instances into the service this scope.







--------------------------------------------------------------------------------

getSigner
================================================================================

.. code-block:: typescript

  bccService.getSigner(provider);

Returns the existing executor or creates a new one, for the active current provider.

----------
Parameters
----------

#. ``provider`` - ``string`` (default = |source getCurrentProvider|_): The provider

-------
Returns
-------

``Promise`` returns |source SignerInternal|_: The signer.

-------
Example
-------

.. code-block:: typescript

  const signer = this.getSigner(provider);




--------------------------------------------------------------------------------

.. _document_getRightsAndRolesObj:

getRightsAndRolesObj
================================================================================

.. code-block:: typescript

  bccService.getRightsAndRolesObj();

Returns a new rights and roles object instance.

----------
Parameters
----------

#. ``options`` - ``object``: The options used for calling
    * ``from`` - ``string`` (optional): The address the call "transaction" should be made from
#. ``callback`` - ``Function`` (optional): This callback will be fired..
#. ``somethingElse`` - ``string`` (optional): this can be set if required, defaults to ``"latest"``

-------
Returns
-------

|source RightsAndRoles|_: The rights and roles object

-------
Example
-------

.. code-block:: typescript

  rightsAndRoles = this.getRightsAndRolesObj();




--------------------------------------------------------------------------------

.. _document_updateBCC:

updateBCC
================================================================================

.. code-block:: typescript

  bccService.updateBCC(activeAccount, provider, disableKeys);

Setup / update initial blockchain-core structure for current account id and signer.

----------
Parameters
----------

#. ``activeAccount`` - ``string``: current active account
#. ``provider`` - ``string``: internal / external
#. ``disableKeys`` - ``boolean`` (optional): disable keyProvider.setKeys / this.setExchangeKeys, used for disabling key setting, only early ui states

-------
Returns
-------

``Promise`` returns ``void``: solved when bcc is updated

-------
Example
-------

.. code-block:: typescript

  await bccService.updateBCC();






--------------------------------------------------------------------------------

.. _document_getProfileForAccount:

getProfileForAccount
================================================================================

.. code-block:: typescript

  bccService.getProfileForAccount(accountId);

Returns an new blockchain-core profile instance. !Attention : It's only builded for load values to check for public and private keys (e.g. used by onboarding or global-password) Executor is the normal one from the global core!!!

----------
Parameters
----------

#. ``accountId`` - ``string``: account id to create a new profile instance for

-------
Returns
-------

|source Profile|_: The profile for account.

-------
Example
-------

.. code-block:: typescript

  bccService.getProfileForAccount('0x000')





--------------------------------------------------------------------------------

.. _document_setExchangeKeys:

setExchangeKeys
================================================================================

.. code-block:: typescript

  bccService.setExchangeKeys(accountId);

run keyExchange.setPublicKey

----------
Parameters
----------

#. ``accountId`` - ``string``: Account id to set the exchange keys for

-------
Returns
-------

``Promise`` returns ``void``: resolved when done

-------
Example
-------

.. code-block:: typescript

  await this.setExchangeKeys(activeAccount);




--------------------------------------------------------------------------------

.. _document_getMetamaskWeb3:

getMetamaskWeb3
================================================================================

.. code-block:: typescript

  bccService.getMetamaskWeb3();

Returns a new web3 instances. If a web3 currentProvider is provided, it will be used.

-------
Returns
-------

``Promise`` returns |source Web3|_: window.web3

-------
Example
-------

.. code-block:: typescript

  getWeb3(provider = this.core.getCurrentProvider()) {
    if (provider === 'metamask') {
      return this.getMetamaskWeb3();
    } else {
      return this.web3;
    }
  }




--------------------------------------------------------------------------------

.. _document_getWeb3:

getWeb3
================================================================================

.. code-block:: typescript

  bccService.getWeb3(provider);

Get the existing web3 or metamask web3.

----------
Parameters
----------

#. ``provider`` - ``string`` (default = |source getCurrentProvider|_): The provider

-------
Returns
-------

``Promise`` returns ``void``: resolved when done

-------
Example
-------

.. code-block:: typescript

  this.getWeb3();





--------------------------------------------------------------------------------

getDomainName
================================================================================

.. code-block:: typescript

  dapp.getDomainName(...subLabels);

builds a full domain name for the current bcc config

----------
Parameters
----------

#. ``Array<string>`` - ``subLabels``: used to enhance nameResolver config

-------
Returns
-------

``The domain name`` : The domain name.

-------
Example
-------

.. code-block:: typescript

  ensDomain = `bcc.${ getDomainName() }!dapp-content`
  // returns: bcc.evan!dapp-content




--------------------------------------------------------------------------------

.. _document_globalPasswordDialog:

globalPasswordDialog
================================================================================

.. code-block:: typescript

  initializedModule.globalPasswordDialog(accountId);

angular-core default password dialog function that is used for lightwallet unlocking.

----------
Parameters
----------

#. ``accountId`` - ``string``: account id to load password for

-------
Returns
-------

``Promise`` returns ``string``: the password

-------
Example
-------

.. code-block:: typescript

  await this.bccService.initialize((accountId) => this.bccService.globalPasswordDialog(accountId));

.. required for building markup
.. |source getCurrentProvider| replace:: ``this.core.getCurrentProvider()``
.. _source getCurrentProvider: /angular-core/services/ui/core.html#getcurrentprovider

.. |source bcc_bundlejs| replace:: ``blockchain-core frontend bundle``
.. _source bcc_bundlejs: https://github.com/evannetwork/api-blockchain-core/blob/develop/src/bundles/bcc/bcc.ts

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
.. _source config: ../../dapp-browser/config.html

.. |source executor| replace:: ``Executor``
.. _source executor: https://github.com/evannetwork/api-blockchain-core/blob/develop/docs/blockchain/executor.rst

.. |source contract_loader| replace:: ``ContractLoader``
.. _source contract_loader: https://github.com/evannetwork/api-blockchain-core/blob/develop/docs/contracts/contract-loader.rst

.. |source description| replace:: ``Description``
.. _source description: https://github.com/evannetwork/api-blockchain-core/blob/develop/docs/blockchain/description.rst

.. |source dfs_interface| replace:: ``DfsInterface``
.. _source dfs_interface: https://github.com/evannetwork/api-blockchain-core/blob/develop/docs/dfs/dfs-interface.rst

.. |source ipfs_api| replace:: ``IpfsRemoteConstructor``
.. _source ipfs_api: https://github.com/ipfs/js-ipfs-api

.. |source name_resolver| replace:: ``NameResolver``
.. _source name_resolver: https://github.com/evannetwork/api-blockchain-core/blob/develop/docs/blockchain/name-resolver.rst

.. |source ipfs_cache| replace:: ``IpfsCache``
.. _source ipfs_cache: ../../dapp-browser/ipfs-cache.html

.. |source smart_contracts| replace:: ``SmartContracts``
.. _source smart_contracts: https://github.com/evannetwork/smart-contracts

.. |source CryptoProvider| replace:: ``CryptoProvider``
.. _source CryptoProvider: https://github.com/evannetwork/api-blockchain-core/blob/develop/docs/encryption/crypto-provider.rst

.. |source EventHub| replace:: ``EventHub``
.. _source EventHub: https://github.com/evannetwork/api-blockchain-core/blob/develop/docs/blockchain/event-hub.rst

.. |source Ipfs| replace:: ``Ipfs``
.. _source Ipfs: https://github.com/evannetwork/api-blockchain-core/blob/develop/docs/dfs/ipfs.rst

.. |source Unencrypted| replace:: ``Unencrypted``
.. _source Unencrypted: https://github.com/evannetwork/api-blockchain-core/blob/develop/docs/encryption/cryptor-unencrypted.rst

.. |source isAccountOnboarded| replace:: ``isAccountOnboarded``
.. _source isAccountOnboarded: /bcc/bcc-bundle.html#isaccountonboarded

.. |source keyStore| replace:: ``KeyStore``
.. _source keyStore: https://github.com/ConsenSys/eth-lightwallet/blob/master/lib/keystore.js

.. |source Mnemonic| replace:: ``Mnemonic``
.. _source Mnemonic: https://github.com/bitpay/bitcore-mnemonic

.. |source KeyProviderInterface| replace:: ``KeyProviderInterface``
.. _source KeyProviderInterface: https://github.com/evannetwork/api-blockchain-core/blob/develop/docs/encryption/key-provider.rst

.. |source KeyProvider| replace:: ``KeyProvider``
.. _source KeyProvider: https://github.com/evannetwork/api-blockchain-core/blob/develop/docs/encryption/key-provider.rst

.. |source SignerInternal| replace:: ``SignerInternal``
.. _source SignerInternal: https://github.com/evannetwork/api-blockchain-core/blob/develop/docs/blockchain/signer.rst

.. |source SignerExternal| replace:: ``SignerExternal``
.. _source SignerExternal: https://github.com/evannetwork/api-blockchain-core/blob/develop/docs/blockchain/signer.rst

.. |source Aes| replace:: ``Aes``
.. _source Aes: https://github.com/evannetwork/api-blockchain-core/blob/develop/docs/encryption/cryptor-aes.rst

.. |source Ipld| replace:: ``Ipld``
.. _source Ipld: https://github.com/evannetwork/api-blockchain-core/blob/develop/docs/dfs/ipld.rst

.. |source KeyExchange| replace:: ``KeyExchange``
.. _source KeyExchange: https://github.com/evannetwork/api-blockchain-core/blob/develop/docs/profile/key-exchange.rst

.. |source Logger| replace:: ``Logger``
.. _source Logger: https://github.com/evannetwork/api-blockchain-core/blob/develop/docs/common/logger.html

.. |source Mailbox| replace:: ``Mailbox``
.. _source Mailbox: https://github.com/evannetwork/api-blockchain-core/blob/develop/docs/profile/mailbox.rst

.. |source Onboarding| replace:: ``Onboarding``
.. _source Onboarding: https://github.com/evannetwork/api-blockchain-core/blob/develop/docs/profile/onboarding.rst

.. |source Profile| replace:: ``Profile``
.. _source Profile: https://github.com/evannetwork/api-blockchain-core/blob/develop/docs/profile/profile.rst

.. |source RightsAndRoles| replace:: ``RightsAndRoles``
.. _source RightsAndRoles: https://github.com/evannetwork/api-blockchain-core/blob/develop/docs/contracts/rights-and-roles.rst

.. |source Sharing| replace:: ``Sharing``
.. _source Sharing: https://github.com/evannetwork/api-blockchain-core/blob/develop/docs/contracts/sharing.rst

.. |source DataContract| replace:: ``DataContract``
.. _source DataContract: https://github.com/evannetwork/api-blockchain-core/blob/develop/docs/contracts/data-contract.rst

.. |source BusinessCenterProfile| replace:: ``BusinessCenterProfile``
.. _source BusinessCenterProfile: https://github.com/evannetwork/api-blockchain-core/blob/develop/docs/profile/business-center-profile.rst
