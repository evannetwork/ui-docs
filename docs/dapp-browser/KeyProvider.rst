================================================================================
Key Provider
================================================================================

.. list-table:: 
   :widths: auto
   :stub-columns: 1

   * - Class Name
     - KeyProvider
   * - Implements
     - `KeyProviderInterface <https://github.com/evannetwork/dbcp/tree/master/src/encryption/key-provider-interface.ts>`_
   * - Extends
     - `Logger </common/logger.html>`_
   * - Extends
     - `key-provider.ts <https://github.com/evannetwork/ui-dapp-browser/blob/master/src/app/bcc/KeyProvider.ts>`_
   * - Source
     - `key-provider.ts <https://github.com/evannetwork/ui-dapp-browser/blob/develop/src/app/bcc/KeyProvider.ts>`_


This `DApp browser KeyProvider <https://github.com/evannetwork/ui-dapp-browser/blob/master/src/app/bcc/KeyProvider.ts>`_ is a adaption of the original `DBCP KeyProvider <https://github.com/evannetwork/dbcp/blob/develop/src/encryption/key-provider.ts>`_ returns given decryption/encryption keys for a given CryptoInfo. They use a given evan.network profile to retrieve the needed keys to encrypt/decrypt the envelope

------------------------------------------------------------------------------

.. _db_key_provider_constructor:

constructor
================================================================================

.. code-block:: typescript

  new KeyProvider(keys, accountId)

Creates a new KeyProvider instance.

----------
Parameters
----------

#. ``keys`` - ``any``: object with key mappings of accounts (can be empty, will be filled dynamically).
#. ``accountId`` - ``string``: create KeyProvider for specific accountId, default the current logged in accountId will be used.


-------
Returns
-------

``KeyProvider`` instance

-------
Example
-------

.. code-block:: typescript
  
  const keyProvider = new KeyProvider({ });


--------------------------------------------------------------------------------

.. _db_key_provider_setKeys:

setKeys
===================

.. code-block:: javascript

    keyProvider.setKeys();

set the keys for the within the constructor provided or global accountId

-------
Example
-------

.. code-block:: javascript

    runtime.keyProvider.setKeys();

------------------------------------------------------------------------------

.. _db_key_provider_setKeysForAccount:

setKeys
===================

.. code-block:: javascript

    keyProvider.setKeys();

Uses an account id and an encryptionKey to set account specific encryption keys.

-------
Example
-------

.. code-block:: javascript

    keyProvider.setKeysForAccount(this.origin.currentAccountHash, encryptionKey);

------------------------------------------------------------------------------


.. _db_key_provider_getKey:

getKey
===================

.. code-block:: javascript

    keyProvider.getKey(info);

get a encryption/decryption key for a specific CryptoInfo from the associated AccountStore or the loaded evan.network profile

----------
Parameters
----------

#. ``cryptoAlgo`` - ``string``: crypto algorithm

-------
Returns
-------

Promise resolves to ``string``: the found key for the cryptoinfo.

-------
Example
-------

.. code-block:: javascript

    const cryptoInfo = {
      "public": {
        "name": "envelope example"
      },
      "private": "...",
      "cryptoInfo": {
        "algorithm": "unencrypted",
        "keyLength": 256,
        "originator": "0x0000000000000000000000000000000000000001,0x0000000000000000000000000000000000000002",
        "block": 123
      }
    };
    const key = runtime.keyProvider.getKey(info);

.. required for building markup

.. |source logLevel| replace:: ``LogLevel``
.. _source logLevel: https://github.com/evannetwork/api-blockchain-core/blob/develop/docs/common/logger.html#loglevel

.. |source logLogInterface| replace:: ``LogLogInterface``
.. _source logLogInterface: https://github.com/evannetwork/api-blockchain-core/blob/develop/docs/common/logger.html#logloginterface
