Changelog
=========

0.9.1
-----

 - Replaced term `donation` and `donationBenefactor` with `fee` and `feeRecipient` (done)
 - Replaced term `payment` to `bounty`. (done)
 - Removed the hardcoding of FEE_RECIPIENT to be passed in on creation of schedulers. (done)
 - Added an indexed parameter to `RequestCreated()` event in RequestFactory.sol (done)
 - Peg contracts to compiler version 0.4.19 (done)
 - Change `paymentData.hasBenefactor()` to `paymentData.hasFeeRecipient()` (done)
 - Tidied up and cleaned the test suite. ( in progress )

0.9.0-beta
----------

- Update contracts to solidity 0.4.18.
- Digger.sol removed due to `EIP 150`_ making it obsolete.
- All stack depth checking also obsolete due to `EIP150`_ removed.
- SafeSendLib.sol removed due to Solidity keywords `transfer` and `send` making it obsolete.
- Simplified scheduling API to singular `schedule()` function.
- Added the `proxy()` function to `TransactionRequest` contract.
- Integrate Truffle framework.
- Rewrote entire test suite to use Truffle.
- Revamped the documentation.


0.8.0 (unreleased)
------------------

- Full rewrite of all contracts.
- Support for both time and block based scheduling.
- New permissionless call tracker now used to track scheduled calls.
- Donation address can now be configured.
- Request execution window size is now configurable.
- Reserved claim window size is now configurable.
- Freeze period is now configurable.
- Claim window size is now configurable.
- All payments now support pull mechanism for retrieving payments.


0.7.0
-----

- Scheduled calls can now specify a required gas amount.  This takes place of
  the ``suggestedGas`` api from 0.6.0
- Scheduled calls can now send value along with the transaction.
- Calls now protect against stack depth attacks.  This is configurable via the
  ``requiredStackDepth`` option.
- Calls can now be scheduled as soon as 10 blocks in the future.
- Experimental implementation of market-based value for the ``defaultPayment``
- ``scheduleCall`` now has 31 different call signatures.


0.6.0
-----

- Each scheduled call now exists as it's own contract, referred to as a call
  contract.
- Removal of the Caller Pool
- Introduction of the claim api for call.
- Call Portability.  Scheduled calls can now be trustlessly imported into
  future versions of the service.


0.5.0
-----

- Each scheduled call now exists as it's own contract, referred to as a call
  contract.
- The authorization API has been removed. It is now possible for the contract
  being called to look up ``msg.sender`` on the scheduling contract and find
  out who scheduled the call.
- The account management API has been removed.  Each call contract now manages
  it's own gas money, the remainder of which is given back to the scheduler
  after the call is executed.
- All of the information that used to be stored about the call execution is now
  placed in event logs (gasUsed, wasSuccessful, wasCalled, etc)


0.4.0
-----

- Convert Alarm service to use library contracts for all functionality.
- CallerPool contract API is now integrated into the Alarm API


0.3.0
-----

- Convert Alarm service to use `Grove`_ for tracking scheduled call ordering.
- Enable logging most notable Alarm service events.
- Two additional convenience functions for invoking ``scheduleCall`` with
  **gracePeriod** and **nonce** as optional parameters.


0.2.0
-----

- Fix for `Issue 42`_.  Make the free-for-all bond bonus restrict itself to the
  correct set of callers.
- Re-enable the right tree rotation in favor of removing three ``getLastX``
  function.  This is related to the pi-million gas limit which is restricting
  the code size of the contract.


0.1.0
-----

- Initial release.


.. _EIP150: https://ethereum.stackexchange.com/questions/9398/how-does-eip-150-change-the-call-depth-attack
.. _Issue 42: https://github.com/pipermerriam/ethereum-alarm-clock/issues/42
.. _Grove: https://github.com/pipermerriam/ethereum-grove
