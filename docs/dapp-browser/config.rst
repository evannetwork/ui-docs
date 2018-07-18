======
config
======

The config represents the blockchain-core configuration that is passed to the |source CoreBundle|_ during the initialization process. This is a derivate of the default `blockchain-core config <https://github.com/evannetwork/api-blockchain-core/blob/develop/src/config.ts>`_.

Each process.evn configuration property can be overwritten using localStorage properties.

-------
Example
-------

.. code-block:: typescript

  const process = {
    env: {
      ENS_ADDRESS: window.localStorage['evan-ens-address'],
      ENS_RESOLVER: window.localStorage['evan-ens-resolver'],
      BC_ROOT: window.localStorage['evan-bc-root'],
      ENS_ROOT: window.localStorage['evan-ens-root'],
      ENS_EVENTS: window.localStorage['evan-ens-events'],
      ENS_PROFILES: window.localStorage['evan-ens-profiles'],
      ENS_MAILBOX: window.localStorage['evan-ens-mailbox'],
    }
  };
  const config = {
    web3Provider: 'ws://localhost:8546',
    nameResolver: {
      ensAddress: process.env.ENS_ADDRESS || '0x937bbC1d3874961CA38726E9cD07317ba81eD2e1',
      ensResolver: process.env.ENS_RESOLVER || '0xDC18774FA2E472D26aB91deCC4CDd20D9E82047e',
      labels: {
        businessCenterRoot: process.env.BC_ROOT || 'taskboard.evan',
        ensRoot: process.env.ENS_ROOT || 'evan',
        factory: 'factory',
        admin: 'admin',
        eventhub: 'eventhub',
        profile: 'profile',
        mailbox: 'mailbox'
      },
      domains: {
        root: ['ensRoot'],
        factory: ['factory', 'businessCenterRoot'],
        adminFactory: ['admin', 'factory', 'ensRoot'],
        businessCenter: ['businessCenterRoot'],
        eventhub: process.env.ENS_EVENTS || ['eventhub', 'ensRoot'],
        profile: process.env.ENS_PROFILES || ['profile', 'ensRoot'],
        profileFactory: ['profile', 'factory', 'ensRoot'],
        mailbox: process.env.ENS_MAILBOX || ['mailbox', 'ensRoot'],
      },
    },
    smartAgents: {
      onboarding: {
        accountId: '0x063fB42cCe4CA5448D69b4418cb89E663E71A139',
      },
    },
    alwaysAutoGasLimit: 1.1,
  }

  export { config }


.. |source CoreBundle| replace:: ``CoreBundle``
.. _source CoreBundle: https://github.com/evannetwork/api-blockchain-core/blob/develop/src/bundles/bcc/bcc.ts