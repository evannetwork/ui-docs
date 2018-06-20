=============
EvanBcService
=============

BCC business center API wrapper. Manages:
  - bc object initialization
  - bc contract creation & loading
  - bc member loading
  - ... 

- ``joinLeaveBcQueueId`` - |source queueId|_: queue id for checking joining / leaving members
- ``profileQueueId`` - |source queueId|_: queue id for applying business center informations to the users profile

--------------------------------------------------------------------------------

getCurrentBusinessCenter
================================================================================

.. code-block:: typescript

  bcService.getCurrentBusinessCenter(ensDomain);

Gets the current business center. It is created using the BCBundle.createBC runtime function.

----------
Parameters
----------

#. ``ensDomain`` - ``string``: bc ens domain

-------
Returns
-------

``Promise`` returns ``any``: the initialized business center



- ``ensDomain`` - ``string``: bc ens domain
- ``bcAddress`` - ``string``: bc contract address
- ``businessCenter`` - ``any``: BusinessCenter contract address
- ``bcRoles`` - ``RightsAndRoles``: roles object for the business center
- ``ipld`` - ``Ipld``: ipld for the business center
- ``bcProfiles`` - ``BusinessCenterProfile``: profiles object for the business center
- ``description`` - ``Description``: description object for the business center
- ``dataContract`` - ``DataContract``: dataContract specific for the business center

-------
Example
-------

.. code-block:: typescript

  const businessCenter = await this.bcService.getCurrentBusinessCenter('taskboard.evan');





--------------------------------------------------------------------------------

reloadBc
================================================================================

.. code-block:: typescript

  bcService.reloadBc(ensDomain);

Refresh the data of a loaded business center. Have a look at "getCurrentBusinessCenter"

----------
Parameters
----------

#. ``ensDomain`` - ``string``: ens domain to load the bc for

-------
Returns
-------

``Promise`` returns ``any``: `business center object </angular-core/services/bcc/bc.html#getcurrentbusinesscenter>`_

-------
Example
-------

.. code-block:: typescript

  await this.bcService.reloadBc('taskboard.evan');




--------------------------------------------------------------------------------

getMembers
================================================================================

.. code-block:: typescript

  bcService.getMembers(contract, ensDomain);

load the members for a contract within an business center

----------
Parameters
----------

#. ``contract`` - ``any``: contract id or contract object
#. ``ensDomain`` - ``string``: ens domain of the business center

-------
Returns
-------

``Promise`` returns ``Array<string>``: list of members

-------
Example
-------

.. code-block:: typescript

  this.bcService.getMembers(null, 'taskboard.evan')




--------------------------------------------------------------------------------

getProfiles
================================================================================

.. code-block:: typescript

  bcService.getProfiles(members, ensDomain);

Load profiles for an member array

----------
Parameters
----------

#. ``members`` - ``Array<any>``: members to load the profiles for
#. ``ensDomain`` - ``string``: ens domain to load the contact cards from

-------
Returns
-------

``Promise`` returns ``void``: profiles analogous to `addressbook profiles </angularcore/services/bcc/address-book.html#loadaccounts>`_.

-------
Example
-------

.. code-block:: typescript

  const members = await bcService.getMembers(null, ensDomain);
  const profiles = await bcService.getProfiles(members);




--------------------------------------------------------------------------------

getProfileQueueId
================================================================================

.. code-block:: typescript

  bcService.getProfileQueueId(ensDomain);

Creates an queue id for users profile within a business center

----------
Parameters
----------

#. ``ensDomain`` - ``string``: ens domain to create the queue id for

-------
Returns
-------

|source queueId|_: The profile queue identifier.

-------
Example
-------

.. code-block:: typescript

  this.queue.addQueueData(this.getProfileQueueId(ensDomain), {
    alias,
    description: loadedBc.description
  });




--------------------------------------------------------------------------------

isMember
================================================================================

.. code-block:: typescript

  bcService.isMember(accountId, ensDomain);

Checks if a member is joined to a business center

----------
Parameters
----------

#. ``accountId`` - ``string``: account id to check
#. ``ensDomain`` - ``string``: ens domain of the business center

-------
Returns
-------

``Promise`` returns ``boolean``: True if member, False otherwise.

-------
Example
-------

.. code-block:: typescript

  const isUserMember = bcService.isMember('0x000', 'taskboard.evan');





--------------------------------------------------------------------------------

profileSet
================================================================================

.. code-block:: typescript

  bcService.profileSet(ensDomain);

Check if the user has a business center profile

----------
Parameters
----------

#. ``ensDomain`` - ``string``: ens domain of the business center

-------
Returns
-------

``Promise`` returns ``boolean``: true if profile exists, else false

-------
Example
-------

.. code-block:: typescript

  const isProfileSet = bcService.profileSet(ensDomain);




--------------------------------------------------------------------------------

saveProfile
================================================================================

.. code-block:: typescript

  bcService.saveProfile(arguments);

Save the alias of a user to business center profile

----------
Parameters
----------

#. ``alias`` - ``string``: alias to save
#. ``ensDomain`` - ``string``: ens domain of the business center

-------
Returns
-------

``Promise`` returns ``void``: resolved when done

-------
Example
-------

.. code-block:: typescript

  bcService.saveProfile('cool alias', 'taskboard.evan');





--------------------------------------------------------------------------------

getBCContracts
================================================================================

.. code-block:: typescript

  bcService.getBCContracts(ensDomain);

Get your contracts for a specific business center.

----------
Parameters
----------

#. ``ensDomain`` - ``string``: ens domain of the business center

-------
Returns
-------

``Promise`` returns ``Array<any>``: The bc contracts. ([ this.getBCContract() ])

-------
Example
-------

.. code-block:: typescript

  const bcContracts = bcService.getBCContracts('taskboard.evan');





--------------------------------------------------------------------------------

getBCContract
================================================================================

.. code-block:: typescript

  initializedModule.getBCContract(ensDomain, contract);

load a contract of a business center

----------
Parameters
----------

#. ``ensDomain`` - ``string``: ens domain of the business center
#. ``contractId`` - ``string``: The contract identifier

-------
Returns
-------

``Promise`` returns ``any``: The bc contract.

-------
Example
-------

.. code-block:: typescript

  const bcContract = bcService.getBCContract('taskboard.evan', '0x000');





--------------------------------------------------------------------------------

getJoinLeaveBcQueueId
================================================================================

.. code-block:: typescript

  bcService.getJoinLeaveBcQueueId(ensDomain);

Gets the join leave bc QueueId.

----------
Parameters
----------

#. ``ensDomain`` - ``string``: The ens domain

-------
Returns
-------

|source queueId|_: The join leave bc queue identifier.

-------
Example
-------

.. code-block:: typescript

  const queueId = bcService.getJoinLeaveBcQueueId('taskboard.evan');




--------------------------------------------------------------------------------

joinBcViaQueue
================================================================================

.. code-block:: typescript

  bcService.joinBcViaQueue(ensDomain);

Join a business center using the bc profile QueueId

----------
Parameters
----------

#. ``ensDomain`` - ``string``: The ens domain

-------
Returns
-------

``Promise`` returns ``void``: resolved when done

-------
Example
-------

.. code-block:: typescript

  await joinBcViaQueue('taskboard.evan');




--------------------------------------------------------------------------------

executeOperationOnBc
================================================================================

.. code-block:: typescript

  bcService.executeOperationOnBc(ensDomain, operation);

Run a business-center contract function.

----------
Parameters
----------

#. ``ensDomain`` - ``string``: ens domain of the business center
#. ``operation`` - ``string``: contract function

-------
Returns
-------

``Promise`` returns ``void``: resolved when done

-------
Example
-------

.. code-block:: typescript

  await this.executeOperationOnBC(ensDomain, 'join');


--------------------------------------------------------------------------------

joinBc
================================================================================

.. code-block:: typescript

  bcService.joinBc(ensDomain);

Join a business center

----------
Parameters
----------

#. ``ensDomain`` - ``string``: ens domain of the business center

-------
Returns
-------

``Promise`` returns ``void``: resolved when done

-------
Example
-------

.. code-block:: typescript

  await bcService.joinBc('taskboard.evan');





--------------------------------------------------------------------------------

leaveBc
================================================================================

.. code-block:: typescript

  bcService.leaveBc(ensDomain);

leave a business center

----------
Parameters
----------

#. ``ensDomain`` - ``string``: ens domain of the business center

-------
Returns
-------

``Promise`` returns ``void``: resolved when done

-------
Example
-------

.. code-block:: typescript

  await bcService.leaveBc('taskboard.evan');

.. |source queueId| replace:: ``QueueId``
.. _source queueId: /angular-core/services/bcc/queue-utilities.html#queueid

.. |source RightsAndRoles| replace:: ``RightsAndRoles``
.. _source RightsAndRoles: https://github.com/evannetwork/blockchain-core/blob/develop/docs/contracts/rights-and-roles.rst

.. |source Ipld| replace:: ``Ipld``
.. _source Ipld: https://github.com/evannetwork/blockchain-core/blob/develop/docs/dfs/ipld.rst

.. |source BusinessCenterProfile| replace:: ``BusinessCenterProfile``
.. _source BusinessCenterProfile: https://github.com/evannetwork/blockchain-core/blob/develop/docs/profile/business-center-profile.rst

.. |source DataContract| replace:: ``DataContract``
.. _source DataContract: https://github.com/evannetwork/blockchain-core/blob/develop/docs/contracts/data-contract.rst

.. |source description| replace:: ``Description``
.. _source description: https://github.com/evannetwork/blockchain-core/blob/develop/docs/blockchain/description.rst

