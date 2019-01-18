================
EvanVerificationService
================

.. list-table:: 
   :widths: auto
   :stub-columns: 1

   * - Source
     - `bcc <https://github.com/evannetwork/ui-angular-core/blob/develop/src/services/bcc/claims.ts>`__
   * - Reference Implementation
     - `Verifications Overview DApp <https://github.com/evannetwork/ui-core-dapps/tree/develop/dapps/claims/src/components/claims>`_


Blockchain-core wrapper service to handle users claims.

- ``ensRootOwner`` - ``string``: owner of the evan root claim domain (= 0x4a6723fC5a926FA150bAeAf04bfD673B056Ba83D)


--------------------------------------------------------------------------------

getQueueId
================================================================================

.. code-block:: typescript

  bcService.getQueueId(dispatcher, id);

Return the queue id to watch for any action for a demo.

----------
Parameters
----------

#. ``dispatcher`` - ``string``: optional name of the dispatcher (default is * = watch everything)
#. ``id`` - ``string``: optional id for the queue id

-------
Returns
-------

``QueueId``: The handling queue identifier.

-------
Example
-------

.. code-block:: typescript

  this.queueWatcher = await this.queue.onQueueFinish(
    this.claimService.getQueueId(),
    async (reload, results) => {
      this.loadVerifications();
    }
  );

--------------------------------------------------------------------------------

isVerificationLoading
================================================================================

.. code-block:: typescript

  bcService.getCisVerificationLoading(claim);

Checks if a claim is current loading (issuing, accepting, deleting).

----------
Parameters
----------

#. ``claim`` - ``any``: the claim object that should be checked (loaded vom api-blockchain-core / getVerifications function)

-------
Returns
-------

``boolean``: True if claimn loading, False otherwise.

-------
Example
-------

.. code-block:: typescript

  // check if anything is loading for the claim (accept, issue, delete)
  claim.loading = this.isVerificationLoading(claim);

--------------------------------------------------------------------------------

getVerifications
================================================================================

.. code-block:: typescript

  bcServicegetVerifications(subject, topic, isIdentity);

Get all the claims for a specific subject, including all nested verifications for a deep integrity check.

----------
Parameters
----------

#. ``subject`` - ``string``: subject to load the claims for.
#. ``topic`` - ``string``: topic to load the claims for.
#. ``isIdentity`` - ``boolean``: optional indicates if the subject is already a identity

-------
Returns
-------

``Promise`` returns ``Array<any>``: all the claims with the following properties.

-------
Example
-------
Reference Implementation: `Verifications Overview DApp <https://github.com/evannetwork/ui-core-dapps/tree/develop/dapps/claims/src/components/claims>`_

.. code-block:: typescript

  this.claimsService.getVerifications('0x123...', '/test')

  // will return 

  {
    // creator of the claim
    issuer: '0x1813587e095cDdfd174DdB595372Cb738AA2753A',
    // topic of the claim
    name: '/company/b-s-s/employee/swo',
    // -1: Not issued => no claim was issued
    // 0: Issued => issued by a non-issuer parent claim holder, self issued state is 0
    // 1: Confirmed => issued by both, self issued state is 2, values match
    status: 2,
    // claim for account id / contract id
    subject: subject,
    // ???
    value: '',
    // ???
    uri: '',
    // ???
    signature: ''
    // icon for cards display
    icon: 'icon to display',
    
    // warnings
    [
      'issued', // claim.status === 0
      'missing', // no claim exists
      'expired', // is the claim expired?
      'selfIssued' // issuer === subject
      'invalid', // signature is manipulated
      'parentMissing',  // parent path does not exists
      'parentUntrusted',  // root path (/) is not issued by evan
      'notEnsRootOwner' // invalid ens root owner when check topic is /
    ],
    parents: [ ... ],
    parentComputed: [ ... ]
  }

--------------------------------------------------------------------------------

computeVerifications
================================================================================

.. code-block:: typescript

  bcService.computeVerifications(topic, claims);

Takes an array of claims and combines all the states for one quick view.

----------
Parameters
----------

#. ``topic`` - ``string``: topic of all the claims
#. ``claims`` - ``Array<any>``: all claims of a specific topic

-------
Returns
-------

``any``: computed claim including latest creationDate, combined color,  displayName

-------
Example
-------
.. code-block:: typescript

  // load all sub claims
  claim.parents = await this.getVerifications(claim.issuerAccount, claim.parent || '/', false);

  // use all the parents and create a viewable computed tree
  claim.tree = this
    .flatVerificationsToLevels(claim)
    .map(level => this.computeVerifications(level.name, level.claims));

  // returns =>
  //   const computed:any = {
  //     claims: claims,
  //     creationDate: null,
  //     displayName: topic.split('/').pop() || 'evan',
  //     loading: claims.filter(claim => claim.loading).length > 0,
  //     name: topic,
  //     status: -1,
  //     subjects: [ ],
  //     warnings: [ ],
  //   }


--------------------------------------------------------------------------------

getProfileActiveVerifications
================================================================================

.. code-block:: typescript

  bcService.getCurrentBugetProfileActiveVerifications(includeSaving);

Load the list of claim topics, that are configured as active for the current profile

----------
Parameters
----------

#. ``includeSaving`` - ``boolean``: should the saving flag returned?

-------
Returns
-------

``Promise`` returns ``any``: Array of topics or object including claims array and saving property

-------
Example
-------
Reference Implementation: `Profile Verifications Component <https://github.com/evannetwork/ui-angular-core/blob/develop/src/components/profile-claims/profile-claims.ts>`_

.. code-block:: typescript

  this.claimsService.getProfileActiveVerifications() // => returns [ '/test/twi' ]

  
