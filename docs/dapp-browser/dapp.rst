====
dapp
====

.. list-table:: 
   :widths: auto
   :stub-columns: 1

   * - Source
     - `dapp <https://github.com/evannetwork/ui-dapp-browser/tree/develop/src/app/dapp.ts>`__

The `DApp library <https://github.com/evannetwork/ui-dapp-browser/blob/develop/src/app/dapp.ts>`_ is a collection of several functions to handle DApp loading, starting and depdency resolve.

--------------------------------------------------------------------------------

.. _db_dapp_getSplittedVersion:

getSplittedVersion
================================================================================

.. code-block:: typescript

  dapp.getSplittedVersion(versionString);

Splits an version, removes non number characters, reduce length to 3 and adds missing numbers.

----------
Parameters
----------

#. ``versionString`` - ``string`` (optional): Version that should be splitted (eg. "0.1.0")

-------
Returns
-------

``Array<number|string>`` : The splitted version.

-------
Example
-------

.. code-block:: typescript

  getSplittedVersion("0.1.0")
  // [0, 1, 0]




--------------------------------------------------------------------------------

.. _db_dapp_getVersionDBCPHashFromDAppVersion:

getVersionDBCPHashFromDAppVersion
================================================================================

.. code-block:: typescript

  dapp.getVersionDBCPHashFromDAppVersion(requiredVersion, childENS, childDefinition);

Returns the ipfs hash to the dbcp of the child with the correct version.

----------
Parameters
----------

#. ``requiredVersion`` - ``string``: version that should be loaded from the child
#. ``childENS`` - ``string``: ens address of the child (the current deployed version is not listed in the versions object, the function sets the ens address within the versions object with the current version)
#. ``childDefinition`` - ``any``: The version dbcp hash from the specific DApp version.

-------
Returns
-------

``string`` : The version dbcp hash from the specific DApp version.

-------
Example
-------

.. code-block:: typescript

  getVersionDBCPHashFromDAppVersion(
    dependencies[dependency],
    dependency,
    subDefinition
  )
  // returns : Qmb...




--------------------------------------------------------------------------------

.. _db_dapp_getDAppDependencies:

getDAppDependencies
================================================================================

.. code-block:: typescript

  dapp.getDAppDependencies(originName, ensDefinition, depTree, deep);

Loads all (sub) dependencies dbcp's of the provided dapp and set systemjs maps to the correct dbcp hashes.

----------
Parameters
----------

#. ``originName`` - ``string``: name of the module that should be traversed;
#. ``ensDefinition`` - ``any``: ens definition of the module that should be traversed (iterate through dependencies);
#. ``depTree`` - ``Array<Array<n>>`` (default = [ ]): dependency tree of a DApp;
#. ``deep`` - ``number`` (default = 0): recursion count to prevent recursive dependency;

-------
Returns
-------

``Promise`` returns ``Array<Array<n>>``: dependency tree of a DApp

-------
Example
-------

.. code-block:: typescript

  await getDAppDependencies(dappEns, ensDefinition);
  // returns: [
  //   [],
  //   [
  //     {
  //       "name": "angular-libs",
  //       "definition": {
  //         ...
  //       },
  //       "location": "angularlibs.evan!dapp-content"
  //     }
  //   ],
  //   [
  //     {
  //       "name": "angular-core",
  //       "definition": {
  //         ...
  //       },
  //       "location": "angularcore.evan!dapp-content"
  //     }
  //   ]
  // ]




--------------------------------------------------------------------------------

.. _db_bcc_loadDAppDependencies:

loadDAppDependencies
================================================================================

.. code-block:: typescript

  bcc.loadDAppDependencies(dappEns, useDefaultDomain);

Load all dependencies of the dapp using SystemJS and register its ens names, so each DApp can load the dependency using it within import statements.

.. code-block:: typescript

  import {
    ...
  } from 'angular-core';


----------
Parameters
----------

#. ``dappEns`` - ``object``: ens of the dapp
#. ``useDefaultDomain`` - ``boolean`` (optional): decide if the default domain should be used

-------
Returns
-------

``Promise`` returns ``any``: ens definition from the DApp

-------
Example
-------

.. code-block:: typescript

  dapp.loadDAppDependencies(dappEns, useDefaultDomain);

  // returns ens definition
  // {
  //   "name": "angular-libs",
  //   "definition": {
  //     ...
  //   },
  //   "location": "angularlibs.evan!dapp-content"
  // }




--------------------------------------------------------------------------------

.. _db_dapp_loadDApp:

loadDApp
================================================================================

.. code-block:: typescript

  dapp.loadDApp(dappEns, useDefaultDomain);

loads a DApp description and register it's dependencies. Returns the js exported module and the loaded ens definition.

----------
Parameters
----------

#. ``dappEns`` - ``object``: ens of the dapp
#. ``useDefaultDomain`` - ``boolean`` (optional): decide if the default domain should be used

-------
Returns
-------

``Promise`` returns ``any``: returns { module: { ... }, ensDefinition: {...}}

-------
Example
-------

.. code-block:: typescript

  loadDApp('dashboard', true);

  // returns:
  //  {
  //    module: loadedModule,
  //    ensDefinition: ensDefinition
  //  }




--------------------------------------------------------------------------------

.. _db_dapp_startDApp:

startDApp
================================================================================

.. code-block:: typescript

  dapp.startDApp(dappEns, container, useDefaultDomain);

Loads an DApp from ENS, resolves it's dependencies and runs the startDApp function or, in case of an html entrypoint, adds an iframe and loads the url.

----------
Parameters
----------

#. ``dappEns`` - ``object``: ens address to load the dapp from
#. ``container`` - ``Element`` (default = document.body): element where DApp was started
#. ``useDefaultDomain`` - ``boolean`` (optional): decide if the default domain should be used

-------
Returns
-------

``Promise`` returns ``void``: resolved when DApp started

-------
Example
-------

.. code-block:: typescript

  await dapp.startDApp('dashboard.evan');




--------------------------------------------------------------------------------

.. _db_dapp_getDomainName:

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