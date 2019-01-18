================
EvanVerificationService
================

.. list-table:: 
   :widths: auto
   :stub-columns: 1

   * - Source
     - `bcc <https://github.com/evannetwork/ui-angular-core/blob/develop/src/services/bcc/verifications.ts>`__
   * - Reference Implementation
     - `Verifications Overview DApp <https://github.com/evannetwork/ui-core-dapps/tree/develop/dapps/verifications/src/components/verifications>`_
   * - Wrapper for 
     - `api-blockchain-core library <https://github.com/evannetwork/api-blockchain-core/blob/develop/src/verifications/verifications.ts>`_

Blockchain-core wrapper service to handle users verifications.

- ``ensRootOwner`` - ``string``: owner of the evan root verification domain (= 0x4a6723fC5a926FA150bAeAf04bfD673B056Ba83D)


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
    this.verificationService.getQueueId(),
    async (reload, results) => {
      this.loadVerifications();
    }
  );

--------------------------------------------------------------------------------

isVerificationLoading
================================================================================

.. code-block:: typescript

  bcService.getCisVerificationLoading(verification);

Checks if a verification is current loading (issuing, accepting, deleting).

----------
Parameters
----------

#. ``verification`` - ``any``: the verification object that should be checked (loaded vom api-blockchain-core / getVerifications function)

-------
Returns
-------

``boolean``: True if verificationn loading, False otherwise.

-------
Example
-------

.. code-block:: typescript

  // check if anything is loading for the verification (accept, issue, delete)
  verification.loading = this.isVerificationLoading(verification);

--------------------------------------------------------------------------------

getVerifications
================================================================================

.. code-block:: typescript

  bcServicegetVerifications(subject, topic, isIdentity);

Get all the verifications for a specific subject, including all nested verifications for a deep integrity check.

----------
Parameters
----------

#. ``subject`` - ``string``: subject to load the verifications for.
#. ``topic`` - ``string``: topic to load the verifications for.
#. ``isIdentity`` - ``boolean``: optional indicates if the subject is already a identity

-------
Returns
-------

``Promise`` returns ``Array<any>``: all the verifications with the following properties.

-------
Example
-------
Reference Implementation: `Verifications Overview DApp <https://github.com/evannetwork/ui-core-dapps/tree/develop/dapps/verifications/src/components/verifications>`_

.. code-block:: typescript

  this.verificationsService.getVerifications('0x123...', '/test')

  // will return 

  {
    // creator of the verification
    issuer: '0x1813587e095cDdfd174DdB595372Cb738AA2753A',
    // topic of the verification
    name: '/company/b-s-s/employee/swo',
    // -1: Not issued => no verification was issued
    // 0: Issued => issued by a non-issuer parent verification holder, self issued state is 0
    // 1: Confirmed => issued by both, self issued state is 2, values match
    status: 2,
    // verification for account id / contract id
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
      'issued', // verification.status === 0
      'missing', // no verification exists
      'expired', // is the verification expired?
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

  bcService.computeVerifications(topic, verifications);

Takes an array of verifications and combines all the states for one quick view.

----------
Parameters
----------

#. ``topic`` - ``string``: topic of all the verifications
#. ``verifications`` - ``Array<any>``: all verifications of a specific topic

-------
Returns
-------

``any``: computed verification including latest creationDate, combined color,  displayName

-------
Example
-------
.. code-block:: typescript

  // load all sub verifications
  verification.parents = await this.getVerifications(verification.issuerAccount, verification.parent || '/', false);

  // use all the parents and create a viewable computed tree
  verification.tree = this
    .flatVerificationsToLevels(verification)
    .map(level => this.computeVerifications(level.name, level.verifications));

  // returns =>
  //   const computed:any = {
  //     verifications: verifications,
  //     creationDate: null,
  //     displayName: topic.split('/').pop() || 'evan',
  //     loading: verifications.filter(verification => verification.loading).length > 0,
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

Load the list of verification topics, that are configured as active for the current profile

----------
Parameters
----------

#. ``includeSaving`` - ``boolean``: should the saving flag returned?

-------
Returns
-------

``Promise`` returns ``any``: Array of topics or object including verifications array and saving property

-------
Example
-------
Reference Implementation: `Profile Verifications Component <https://github.com/evannetwork/ui-angular-core/blob/develop/src/components/profile-verifications/profile-verifications.ts>`_

.. code-block:: typescript

  this.verificationsService.getProfileActiveVerifications() // => returns [ '/test/twi' ]

  
