======================
EvanDescriptionService
======================

`Blockchain core description <https://github.com/evannetwork/blockchain-core/blob/develop/docs/blockchain/description.rst>`_ class wrapper.

--------------------------------------------------------------------------------

getEvanENSAddress
================================================================================

.. code-block:: typescript

  descriptionService.getEvanENSAddress(ensAddress);

Returns an full evan ENS address.

----------
Parameters
----------

#. ``ensAddress`` - ``string``: ENS postfix (dappdapps =>  dappdapps.evan.test)

-------
Returns
-------

``string``: The evan ens address.

-------
Example
-------

.. code-block:: typescript

  descriptionService.getEvanENSAddress('favorites') // => favorites.evan




--------------------------------------------------------------------------------

.. _document_getDescription:

getDescription
================================================================================

.. code-block:: typescript

  descriptionService.getDescription(arguments);

Load the DBCP description and check if the ens address and it's DApp behind can be added.

Adds additional runtime properties for easier ui checks:
- adds translation values for the current language
- name without spaces
- ens address
- status (invalid, valid, already_added)

----------
Parameters
----------

#. ``ensAddress`` - ``string``: Ens Address to load the DApp from
#. ``clearDescription`` - ``boolean``: remove runtime values like ensAddress, status, translated, trimmedName, currentLang

-------
Returns
-------
https://github.com/evannetwork/dbcp/blob/master/wiki/Example-DBCP-file.md



``Promise`` returns ``any``: return the enchanced descriptions

-------
Example
-------

.. code-block:: typescript

  descriptionService.getDescription('favorites.evan', false)




--------------------------------------------------------------------------------

.. _document_getMultipleDescriptions:

getMultipleDescriptions
================================================================================

.. code-block:: typescript

  descriptionService.getMultipleDescriptions(ensAddresses);

Takes an array of dapp names and loads their description from the ens.

----------
Parameters
----------

#. ``ensAddresses`` - ``Array<string>``: ENS-Addresses to load

-------
Returns
-------

``Promise`` returns ``any``: multiple descriptions.

-------
Example
-------

.. code-block:: typescript

  await descriptionService.multipleDescriptions([
    'favorites',
    'contacts',
    ...
  ])




--------------------------------------------------------------------------------

.. _document_getENSOriginUrl:

getENSOriginUrl
================================================================================

.. code-block:: typescript

  descriptionService.getENSOriginUrl(ensAddress);

Gets the ens origin url.

----------
Parameters
----------

#. ``ensAddress`` - ``string``: The options used for calling

-------
Returns
-------

``string``: The ens origin url.

-------
Example
-------

- typescript

.. code-block:: typescript

  import {
    getDomainName
  } from 'dapp-browser';
  ...

  this.ensOrigin = this.description.getENSOriginUrl(`cool-dapp.${ getDomainName() }`);

::

  <img *oneTime [src]="_DomSanitizer.bypassSecurityTrustUrl(ensOrigin + '/cool-img.png')" />