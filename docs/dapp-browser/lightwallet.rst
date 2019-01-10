===========
lightwallet
===========

.. list-table:: 
   :widths: auto
   :stub-columns: 1

   * - Source
     - `Lightwallet <https://github.com/evannetwork/ui-dapp-browser/blob/develop/src/app/lightwallet.ts>`__

The `lightwallet lib <https://github.com/evannetwork/ui-dapp-browser/blob/develop/src/app/lightwallet.ts>`_ is a wrapper for the original |source lightwallet_keystore|_ and |source bitcore_mnemonic|_. It handles logged in users key vaults and encryption.

--------------------------------------------------------------------------------

.. _db_lightwallet_getKeyStore:

getKeyStore
================================================================================

.. code-block:: typescript

  lightwallet.getKeyStore();

returns CoreBundle.keystore (eth-lightwallet/lib/keystore)

-------
Returns
-------

|source lightwallet_keystore|_: keystore library

-------
Example
-------

.. code-block:: typescript

  const KeyStore = lightwallet.getKeyStore();
  KeyStore.isSeedValid('word1 word2 ... word12');


--------------------------------------------------------------------------------

.. _db_lightwallet_getMnemonicLib:

getMnemonicLib
================================================================================

.. code-block:: typescript

  lightwallet.getMnemonicLib();

returns CoreBundle.Mnemonic

-------
Returns
-------

|source bitcore_mnemonic|_: the Mnemonic lib

-------
Example
-------

.. code-block:: typescript

  const Mnemonic = lightwallet.getMnemonicLib();
  var code = new Mnemonic(Mnemonic.Words.SPANISH);
  code.toString(); // natal hada sutil año sólido papel jamón combate aula flota ver esfera...
  var xpriv = code.toHDPrivateKey();




--------------------------------------------------------------------------------

.. _db_lightwallet_createVault:

createVault
================================================================================

.. code-block:: typescript

  lightwallet.createVault(mnemonic, password);

Creates a new vault instance to handle lightwallet interactions.

----------
Parameters
----------

#. ``mnemonic`` - ``string``: mnemonic to create new vault.
#. ``password`` - ``string``: password to encrypt the vault.

-------
Returns
-------

``Promise`` returns |source lightwallet_keystore|_: vault created using mnemonic, encrypted via password

-------
Example
-------

.. code-block:: typescript

  const vault = await lightwallet.createVault(mnemonic, password);
  const pwDerivedKey = await lightwallet.keyFromPassword(vault, password);


--------------------------------------------------------------------------------

.. _db_lightwallet_setVaultActive:

setVaultActive
================================================================================

.. code-block:: typescript

  lightwallet.setVaultActive(vault);

Serializes a specific vault and saves it to the local storage.

----------
Parameters
----------

#. ``vault`` - |source lightwallet_keystore|_: vault to save locally

-------
Example
-------

.. code-block:: typescript

  const vault = await lightwallet.createVault(mnemonic, password);
  setVaultActive(vault);





--------------------------------------------------------------------------------

.. _db_lightwallet_createVaultAndSetActive:

createVaultAndSetActive
================================================================================

.. code-block:: typescript

  lightwallet.createVaultAndSetActive(mnemonic, password);

Create new vault, set it active and set first account id as active one

----------
Parameters
----------

#. ``mnemonic`` - |source lightwallet_keystore|_: mnemonic to create new vault.
#. ``password`` - ``string``: password to encrypt the vault.

-------
Returns
-------

``Promise`` returns ``void``: resolved when done

-------
Example
-------

.. code-block:: typescript

  await lightwallet.createVaultAndSetActive(mnemonic, password);
  const vault = lightwallet.loadVault()




--------------------------------------------------------------------------------

.. _db_lightwallet_keyFromPassword:

keyFromPassword
================================================================================

.. code-block:: typescript

  lightwallet.keyFromPassword(vault, password);

Gets the pwDerivedKey to interact with the vault.

----------
Parameters
----------

#. ``vault`` - ``object``: The options used for calling
#. ``password`` - ``string``: this can be set if required, defaults to ``"latest"``

-------
Returns
-------

``Promise`` returns ``Uint8Array``: the pwDerivedKey

-------
Example
-------

.. code-block:: typescript

  const vault = await createVault(mnemonic, password);
  const pwDerivedKey = await keyFromPassword(vault, password);





--------------------------------------------------------------------------------

.. _db_lightwallet_getNewVault:

getNewVault
================================================================================

.. code-block:: typescript

  lightwallet.getNewVault(mnemonic, password);

Creates an new vault and unlocks it

----------
Parameters
----------

#. ``mnemonic`` - |source lightwallet_keystore|_: mnemonic to create new vault.
#. ``password`` - ``string``: password to encrypt the vault.

-------
Returns
-------

``Promise`` returns |source lightwallet_keystore|_: The new vault.

-------
Example
-------

.. code-block:: typescript

  const vault = await lightwallet.getNewVault(mnemonic, password);




--------------------------------------------------------------------------------

.. _db_lightwallet_getAccounts:

getAccounts
================================================================================

.. code-block:: typescript

  lightwallet.getAccounts(vault, amount);

Get an specific amount of accounts from the vault.

----------
Parameters
----------

#. ``vault`` - |source lightwallet_keystore|_: vault to get accounts from
#. ``amount`` - ``number``: number of accounts to return

-------
Returns
-------

``Array<string>``: The accounts.

-------
Example
-------

.. code-block:: typescript

  const accounts = lightwallet.getAccounts(vault, 1); // => [ '0x0...' ]




--------------------------------------------------------------------------------

.. _db_lightwallet_getPrivateKey:

getPrivateKey
================================================================================

.. code-block:: typescript

  lightwallet.getPrivateKey(vault, accountId);

Gets the private key for an account. Given the derived key, decrypts and returns the private key corresponding to address. This should be done sparingly as the recommended practice is for the keystore to sign transactions using signing.signTx, so there is normally no need to export private keys.

----------
Parameters
----------

#. ``vault`` - ``object``: vault where the account lives
#. ``accountId`` - ``string``: account to get the private key from

-------
Returns
-------

``string``: accounts private key for submitting transactions, etc.

-------
Example
-------

.. code-block:: typescript

  lightwallet.getPrivateKey(vault, '0x00...');




--------------------------------------------------------------------------------

.. _db_lightwallet_loadVault:

loadVault
================================================================================

.. code-block:: typescript

  lightwallet.loadVault();

Load locked vault from localStorage or unlocked memory vault.

-------
Returns
-------

|source lightwallet_keystore|_: deserialized, cached vault

-------
Example
-------

.. code-block:: typescript

  const lockedVault = lightwallet.loadVault();





--------------------------------------------------------------------------------

.. _db_lightwallet_setPasswordFunction:

setPasswordFunction
================================================================================

.. code-block:: typescript

  lightwallet.setPasswordFunction(arguments);

Sets the password function. The dapp-browser does not includes any library / framework / css that handles a good and nice ui development (e.g. angular, react, bootstrap, ...). To handle coporate design and a better DApp development freedom, each DApp must specify its own password dialog. In case of Angular 5 development have a look at the default one, provided by the angular-core: globalPasswordDialog https://github.com/evannetwork/ui-angular-core/blob/4f539a2f5492b137d6be82c133427871073c3929/src/services/evan/bcc.ts#L300

----------
Parameters
----------

#. ``newPasswordFunction`` - ``Function``: The new password function

-------
Example
-------

.. code-block:: typescript

  lightwallet.setPasswordFunction(() => {
    return prompt("Please enter your password");
  });



--------------------------------------------------------------------------------

.. _db_lightwallet_getPassword:

getPassword
================================================================================

.. code-block:: typescript

  lightwallet.getPassword(accountId);

Shows the global-password modal that should return the users password as a string. Be sure that the "lightwallet.setPasswordFunction" was called before, to setup the password function that should be used.

----------
Parameters
----------

#. ``accountId`` - ``string``: additional account id to get the password from

-------
Returns
-------

``Promise`` returns ``string``: password input

-------
Example
-------

.. code-block:: typescript

  const pw = await lightwallet.getPassword('0x00');






--------------------------------------------------------------------------------

.. _db_lightwallet_loadUnlockedVault:

loadUnlockedVault
================================================================================

.. code-block:: typescript

  lightwallet.loadUnlockedVault();

Return current unlocked vault. Asks for password when vault is locked.

-------
Returns
-------

|source lightwallet_keystore|_: unlocked vault

-------
Example
-------

.. code-block:: typescript

  const vault = await lightwallet.loadUnlockedVault();
  console.log(vault.encryptionKey);






--------------------------------------------------------------------------------

.. _db_lightwallet_getEncryptionKey:

getEncryptionKey
================================================================================

.. code-block:: typescript

  lightwallet.getEncryptionKey();

Returns the encryption key for the current password.

-------
Returns
-------

``Promise`` returns ``string``: encryption key

-------
Example
-------

.. code-block:: typescript

  const encryptionKey = await lightwallet.getEncryptionKey();





--------------------------------------------------------------------------------

.. _db_lightwallet_getEncryptionKeyFromPassword:

getEncryptionKeyFromPassword
================================================================================

.. code-block:: typescript

  lightwallet.getEncryptionKeyFromPassword(accountId, password);

Hashes a password using sha3.

----------
Parameters
----------

#. ``accountId`` - ``string``: accountId for that the privateKey should be generated
#. ``password`` - ``string``: password that should be hashed

-------
Returns
-------

``string``: resolved when done

-------
Example
-------

.. code-block:: typescript

  profile.ipld.keyProvider.setKeysForAccount(
    accountId,
    lightwallet.getEncryptionKeyFromPassword(accountId, this.password)
  );




--------------------------------------------------------------------------------

.. _db_lightwallet_deleteActiveVault:

deleteActiveVault
================================================================================

.. code-block:: typescript

  lightwallet.deleteActiveVault();

Remove current active vault from browser.

-------
Example
-------

.. code-block:: typescript

  lightwallet.deleteActiveVault();


.. _db_lightwallet_isValidMnemonic:

isValidMnemonic
================================================================================

.. code-block:: typescript

  lightwallet.isValidMnemonic(mnemonic);

Returns if an mnemonic is a valid mnemonic. (wrapper for |source lightwallet_keystore|_.isSeedValid)

----------
Parameters
----------

#. ``mnemonic`` - ``string``: The options used for calling

-------
Returns
-------

``void``: True if valid mnemonic, False otherwise.

-------
Example
-------

.. code-block:: typescript

  lightwallet.isSeedValid('word1 word2 ... word12');


--------------------------------------------------------------------------------

.. _db_lightwallet_isValidMnemonicWord:

isValidMnemonicWord
================================================================================

.. code-block:: typescript

  lightwallet.isValidMnemonicWord(word);

Returns if an word is a valid mnemonic word.

----------
Parameters
----------

#. ``word`` - ``string``: word to check

-------
Returns
-------

``boolean``: True if valid mnemonic word, False otherwise.

-------
Example
-------

.. code-block:: typescript

  lightwallet.isValidMnemonicWord('cucumber'); // => false

.. |source lightwallet_keystore| replace:: ``lightwallet.keystore``
.. _source lightwallet_keystore: https://github.com/ConsenSys/eth-lightwallet/blob/master/lib/keystore.js

.. |source bitcore_mnemonic| replace:: ``bitcore-mnemonic``
.. _source bitcore_mnemonic: https://github.com/bitpay/bitcore-mnemonic