=========
bccHelper
=========

.. list-table:: 
   :widths: auto
   :stub-columns: 1

   * - Source
     - `bccHelper <https://github.com/evannetwork/ui-dapp-browser/tree/develop/src/app/bcc/bcc.ts>`__

Includes basic functionalities to create profile runtimes and check passwords.

--------------------------------------------------------------------------------

==============
getCoreOptions
==============
.. code-block:: javascript

    accountStore.getCoreOptions(CoreBundle, SmartContracts)

returns the coreOptions for creation a new bcc CoreBundle and SmartContracts object.

----------
Parameters
----------
#. ``CoreBundle`` - |source CoreBundle|_ : blockchain-core ipfs bundle import (System.import('bcc'))
#. ``SmartContracts`` - ``SmartContracts``: smart-contracts ipfs bundle import (System.import('smart-contracts'))

-------
Returns
-------

``CoreBundle`` instance

-------
Example
-------

.. code-block:: typescript

  import * as CoreBundle from 'bcc';
  import * as SmartContracts from 'smart-contracts';
  
  const options = await bccHelper.getCoreOptions(CoreBundle, SmartContracts);

--------------------------------------------------------------------------------

=================
updateCoreRuntime
=================
.. code-block:: javascript

    accountStore.updateCoreRuntime(CoreBundle, SmartContracts)

Loads the current core options and initializes a new CoreRuntime instance.

----------
Parameters
----------
#. ``CoreBundle`` - |source CoreBundle|_ : blockchain-core ipfs bundle import (System.import('bcc'))
#. ``SmartContracts`` - ``SmartContracts``: smart-contracts ipfs bundle import (System.import('smart-contracts'))

-------
Returns
-------

``CoreRuntime`` instance

-------
Example
-------

.. code-block:: typescript

  import * as CoreBundle from 'bcc';
  import * as SmartContracts from 'smart-contracts';
  
  const CoreRuntime = await bccHelper.updateCoreRuntime(CoreBundle, SmartContracts);
  console.log(CoreBundle.CoreRuntime === CoreRuntime) // => true

--------------------------------------------------------------------------------

=========
getSigner
=========
.. code-block:: javascript

    accountStore.getSigner(CoreBundle, provider, accountStore)

Returns the existing executor or creates a new one, for the active current provider.

----------
Parameters
----------
#. ``CoreBundle`` - |source CoreBundle|_ : blockchain-core ipfs bundle import (System.import('bcc'))
#. ``provider`` - ``string`` (default = core.getCurrentProvider()): the current selected provider that should be loaded
#. ``accountStore`` - ``AccountStore`` (default = new AccountStore()): account store to use for the internal signer

-------
Returns
-------

``CoreBundle.SignerInternal || CoreBundle.SignerExternal`` the new Signer Instance

-------
Example
-------

.. code-block:: typescript
  
  import * as CoreBundle from 'bcc';

  const signer = await bccHelper.getSigner(CoreBundle, provider);

--------------------------------------------------------------------------------

===============
setExchangeKeys
===============
.. code-block:: javascript

    accountStore.setExchangeKeys(CoreBundle, accountId)

run keyExchange.setPublicKey

----------
Parameters
----------
#. ``CoreBundle`` - |source CoreBundle|_ : blockchain-core ipfs bundle import (System.import('bcc'))
#. ``accountId`` - ``string``: Account id to set the exchange keys for

-------
Returns
-------

``Promis<void>`` resolved when done

-------
Example
-------

.. code-block:: typescript

  import * as CoreBundle from 'bcc';
  
  await bccHelper.setExchangeKeys(CoreBundle, accountId);

--------------------------------------------------------------------------------

========
startBCC
========
.. code-block:: javascript

    accountStore.startBCC(CoreBundle, SmartContracts, activeAccount, provider)

Setup / update initial blockchain-core structure for current account id and signer.

----------
Parameters
----------
#. ``CoreBundle`` - |source CoreBundle|_ : blockchain-core ipfs bundle import (System.import('bcc'))
#. ``SmartContracts`` - ``SmartContracts``: smart-contracts ipfs bundle import (System.import('smart-contracts'))
#. ``activeAccount`` - ``string``: account id to use
#. ``provider`` - ``string``: provider to use (internal, external, agent)

-------
Returns
-------

``Promis<void>`` resolved when done

-------
Example
-------

.. code-block:: typescript

  import * as CoreBundle from 'bcc';
  import * as SmartContracts from 'smart-contracts';

  await bccHelper.startBCC(CoreBundle, SmartContracts);

--------------------------------------------------------------------------------

====================
getProfileForAccount
====================
.. code-block:: javascript

    accountStore.getProfileForAccount(CoreBundle, accountId)

Setup / update initial blockchain-core structure for current account id and signer.

----------
Parameters
----------
#. ``CoreBundle`` - |source CoreBundle|_ : blockchain-core ipfs bundle import (System.import('bcc'))
#. ``accountId`` - ``string``: account id to create a new profile instance for

-------
Returns
-------

``Promis<void>`` resolved when done

-------
Example
-------

.. code-block:: typescript

  import * as CoreBundle from 'bcc';
  import * as SmartContracts from 'smart-contracts';

  const profile = await bccHelper.getProfileForAccount(CoreBundle, SmartContracts);

  // set the keys for the temporary profile using the password input, so we can try to get the
  // private key
  profile.ipld.keyProvider.setKeysForAccount(
    accountId,
    lightwallet.getEncryptionKeyFromPassword(accountId, password)
  );

  let targetPrivateKey;
  try {
    targetPrivateKey = await profile.getContactKey(
      accountId,
      'dataKey'
    );
  } catch (ex) { }

  // if the private key for this account could be loaded, the password is valid
  if (targetPrivateKey) {
    return true;
  } else {
    return false;
  }

--------------------------------------------------------------------------------

======================
isAccountPasswordValid
======================
.. code-block:: javascript

    accountStore.isAccountPasswordValid(CoreBundle, accountId, password)

Check if the password for a given account id and its profile is valid.

----------
Parameters
----------
#. ``CoreBundle`` - |source CoreBundle|_ : blockchain-core ipfs bundle import (System.import('bcc'))
#. ``accountId`` - ``string``: account id to check
#. ``password`` - ``string``: password to check

-------
Returns
-------

``Promis<boolean>`` True if account password valid, False otherwise

-------
Example
-------

.. code-block:: typescript

  import {
    getDomainName,
    lightwallet,
    utils,
  } from '@evan.network/dapp-browser';

  lightwallet.setPasswordFunction(async () => {
    // bind login function so we can resolve the initial promise, when login is done
    const loginPromise = new Promise(resolve => finishedLogin = (password: string) => {
      router.push({ path: `${ basePath }` });

      resolve(password);
    });

    // navigate the user to the login page
    router.push({ path: `${ basePath }/login` });

    return loginPromise;
  });

  // .....................................

  import * as CoreBundle from 'bcc';
  import * as SmartContracts from 'smart-contracts';

  if (await bccHelper.isAccountPasswordValid(CoreBundle, accountId, password)) {
    finishedLogin(password);
  } else {
    // handle invalid password
  }


--------------------------------------------------------------------------------

====================
createDefaultRuntime
====================
.. code-block:: javascript

    accountStore.createDefaultRuntime(CoreBundle, accountId, encryptionKey, privateKey, runtimeConfig, web3, dfs)

Wraps the original create default runtime bcc function to simplify key and account map management.

----------
Parameters
----------
#. ``CoreBundle`` - |source CoreBundle|_: blockchain-core ipfs bundle
#. ``accountId`` - ``string``: account id to create the runtime for
#. ``encryptionKey`` - ``string``: enryption key of the users profile
#. ``privateKey`` - ``string``: account id's private key
#. ``config`` - ``any``: overwrite the ui configuration with a custom config
#. ``web3`` - ``any``: overwrite the CoreRuntime web3 with a new one
#. ``dfs`` - ``any``: overwrite the CoreRuntime dfs with a new one

-------
Returns
-------

``Promis<any>`` the new bcc defaultruntime

-------
Example
-------

.. code-block:: typescript

  import * as bcc from 'bcc';
  import {
    bccHelper,
    lightwallet,
  } from '@evan.network/dapp-browser';

  const vault = await lightwallet.getNewVault('test faucet ...', 'xyazqw91923');
  const accountId = lightwallet.getAccounts(vault, 1)[0]; 

  // create a new runtime
  const runtime = await bccHelper.createDefaultRuntime(
    bcc,
    accountId,
    vault.encryptionKey,
    lightwallet.getPrivateKey(vault, accountId),
  );

