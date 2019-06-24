==================
EvanPaymentService
==================

.. list-table:: 
   :widths: auto
   :stub-columns: 1

   * - Source
     - `onboarding <https://github.com/evannetwork/ui-angular-core/blob/develop/src/services/bcc/payment.ts>`__

#. ``agentAccountId`` - ``string``: account address of the payment agent.
#. ``channelManagerAccountId`` - ``string``: Manager of the payment channel.
#. ``paymentAgentUrl`` - ``string``: Url to the payment agent server.
#. ``paymentEndPoint`` - ``string``: base endpoint of the payment

--------------------------------------------------------------------------------

requestPaymentAgent
================================================================================

.. code-block:: typescript

  onboarding.requestPaymentAgent(endPoint);

Send an rest get request to the payment agent using the corresponding new build headers.

----------
Parameters
----------

#. ``endPoint`` - ``string``: endpoint that should be called using this.agentEndpoint

-------
Returns
-------

``Promise<any>``: json result of the request

-------
Example
-------
Reference Implementation: `Profile Payment Component <https://github.com/evannetwork/ui-core-dapps/blob/develop/dapps/profile/src/components/payments/payments.ts>`_

.. code-block:: typescript

    // setup channel manager
    this.bcc.payments.setChannelManager(this.paymentService.channelManagerAccountId);

    ...

    const status = await this.paymentService.requestPaymentAgent('getStatus');

    // parse correct value for estimated values
    status.monthlyPayments = Math.floor(status.monthlyPayments).toString();
    status.fundsAvailable = Math.floor(status.fundsAvailable).toString();
    status.estimatedFunds = Math.floor(status.fundsAvailable / status.monthlyPayments);
    status.overallSize = Number(status.monthlyPayments / 100) * 1000;
    this.paymentChannels = await this.paymentService.requestPaymentAgent('getChannels');

    ...

    // find active channels
    const activeChannels = this.paymentChannels.channels
      .filter(channel => channel.state === 'OPEN');

--------------------------------------------------------------------------------

signMessage
================================================================================

.. code-block:: typescript

  onboarding.signMessage(msg, account);

message that should be signed

----------
Parameters
----------

#. ``msg`` - ``string``: message that should be signed
#. ``account`` - ``string``: account id to sign the message with (default = activeAccount)

-------
Returns
-------

``string``: signed message signature

-------
Example
-------
Reference Implementation: `Profile Payment Component <https://github.com/evannetwork/ui-angular-cre/blob/develop/src/services/bcc/payments.ts>`_

.. code-block:: typescript

    const toSignedMessage = this.bcc.web3.utils
      .soliditySha3(new Date().getTime() + activeAccount)
      .replace('0x', '');
    const hexMessage = this.bcc.web3.utils.utf8ToHex(toSignedMessage);
    const signature = await this.signMessage(toSignedMessage, activeAccount);


