================
EvanClaimService
================

.. list-table:: 
   :widths: auto
   :stub-columns: 1

   * - Source
     - `bcc <https://github.com/evannetwork/ui-angular-core/blob/develop/src/services/bcc/claims.ts>`__
   * - Reference Implementation
     - `Claims Overview DApp <https://github.com/evannetwork/ui-core-dapps/tree/develop/dapps/claims/src/components/claims>`_


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
      this.loadClaims();
    }
  );

--------------------------------------------------------------------------------

isClaimLoading
================================================================================

.. code-block:: typescript

  bcService.getCisClaimLoading(claim);

Checks if a claim is current loading (issuing, accepting, deleting).

----------
Parameters
----------

#. ``claim`` - ``any``: the claim object that should be checked (loaded vom api-blockchain-core / getClaims function)

-------
Returns
-------

``boolean``: True if claimn loading, False otherwise.

-------
Example
-------

.. code-block:: typescript

  // check if anything is loading for the claim (accept, issue, delete)
  claim.loading = this.isClaimLoading(claim);


--------------------------------------------------------------------------------

flatClaimsTree
================================================================================

.. code-block:: typescript

  bcService.getCflatClaimsTree(claim, flatClaims, origin);

Use this function when you want to implement the full tree view! Currently we will concadinate
all parents to one.
Picks up a claim and it's origin parents tree structure and traces all claims into a flat
structure for displaying it easily.

----------
Parameters
----------

#. ``claim`` - ``any``: the claim including parents
#. ``flatClaims`` - ``Array<Array<any>>``: The final flatted claims, Array of arrays from the lowest to the highest claim
#. ``origin`` - ``Array<any>``: the flatted claim Array for one parent that will be pushed into the flatClaims array

-------
Example
-------

.. code-block:: typescript

  this.claimService.flatClaimsTree(claim, [ ], [ ]);


--------------------------------------------------------------------------------

flatClaimsToLevels
================================================================================

.. code-block:: typescript

  bcService.getCurreflatClaimsToLevels(claim, levels, index);

Iterates recursivly through all parents of a claim and splits them into specific levels.

----------
Parameters
----------

#. ``claim`` - ``any``: the claim to parse
#. ``levels`` - ``Array<any>``: all parent levels including the name and all claims of this level
#. ``index`` - ``number``: current level index

-------
Returns
-------

``Array<any>``: combined parents splitted into levels

-------
Example
-------

.. code-block:: typescript

  
  this.claimService.flatClaimsToLevels({
    name: '/company/b-s-s/department',
    parent: '/company/b-s-s',
    parents: [
      {
        name: '/company/b-s-s',
        parent: '/company',
        parents: [
          { name: 'company', },
          { name: 'company', },
          { name: 'company', }
        ]
      },
      {
        name: '/company/b-s-s',
        parent: '/company',
        parents: [
          { name: 'company' },
          {
            name: 'company'
            parent: '/',
            parents: [
              { name: '/', },
              { name: '/', }
            ]
          }
        ]
      }
    ]  
  })
  
  // will return =>
  // [
  //   [
  //     { name: '/company/b-s-s', parent: '/company' },
  //     { name: '/company/b-s-s', parent: '/company' }
  //   ],
  //   [
  //     { name: '/company', },
  //     { name: '/company', }
  //     { name: '/company', }
  //     { name: '/company', }
  //     { name: '/company', parent: '/company' }
  //   ]
  //   [
  //     { name: '/', }
  //     { name: '/', }
  //   ]
  // ]


--------------------------------------------------------------------------------

getClaims
================================================================================

.. code-block:: typescript

  bcServicegetClaims(address, topic, isIdentity);

Get all the claims for a specific address.

----------
Parameters
----------

#. ``address`` - ``string``: address to load the claims for.
#. ``topic`` - ``string``: topic to load the claims for.
#. ``isIdentity`` - ``boolean``: optional indicates if the subject is already a identity

-------
Returns
-------

``Promise`` returns ``Array<any>``: all the claims with the following properties.

-------
Example
-------
Reference Implementation: `Claims Overview DApp <https://github.com/evannetwork/ui-core-dapps/tree/develop/dapps/claims/src/components/claims>`_

.. code-block:: typescript

  this.claimsService.getClaims('0x123...', '/test')

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
    subject: address,
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
    ]
    // parent claims not valid
    tree: [ ... ] // result of flatClaimsToLevels
  }

--------------------------------------------------------------------------------

getComputedClaim
================================================================================

.. code-block:: typescript

  bcService.getCurgetComputedClaim(topic, claims);

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
  claim.parents = await this.getClaims(claim.issuerAccount, claim.parent || '/', false);

  // use all the parents and create a viewable computed tree
  claim.tree = this
    .flatClaimsToLevels(claim)
    .map(level => this.getComputedClaim(level.name, level.claims));

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

getProfileActiveClaims
================================================================================

.. code-block:: typescript

  bcService.getCurrentBugetProfileActiveClaims(includeSaving);

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
Reference Implementation: `Profile Claims Component <https://github.com/evannetwork/ui-angular-core/blob/develop/src/components/profile-claims/profile-claims.ts>`_

.. code-block:: typescript

  this.claimsService.getProfileActiveClaims() // => returns [ '/test/twi' ]


--------------------------------------------------------------------------------

ensureClaimDescription
================================================================================

.. code-block:: typescript

  bcService.ensureClaimDescription(claim);

Gets the default description for a claim if it does not exists.

----------
Parameters
----------

#. ``claim`` - ``any``: should the saving flag returned?

-------
Example
-------
.. code-block:: typescript

  await this.ensureClaimDescription(computed);

  
