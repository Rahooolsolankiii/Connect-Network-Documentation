# Implementation Details and Notes

**Rewards Estimation**

Estimated rewards calculation uses the current status of the blockchain to approximate the amount of Connect Network coins rewarded for participating in staking. The network uses a proof of stake consensus variant to ensure the security of the data inside the blockchain structure.

To calculate the rewards we use the baseRewardPerSecond value of the latest sealed epoch, but the total staked amount of tokens is calculated elsewhere. The epoch does provide a value of total self-staked tokens in that epoch and also the amount of total delegated tokens, but the first value does not contain temporarily offline nodes and, on the other hand, it includes delegated stake in un-delegation. That means the value is not correct for our calculations.

To get the current total staked value, we iterate all the staking records and collect the total staked amount from individual staking.

**Delegation Limits**

The Delegation Limit is calculated from the current self-staked amount of a stake by multiplying it by fixed-rate, specified in the SFC contract. The current value of maximum allowed delegations is 15 times the amount of self-staked Connect Network.

When we calculate the remaining allowed limit, the current delegated amount is subtracted from the total limit. The value is provided by API so you don't have to deal with the calculation yourself. Please note that tokens in un-delegation do not count towards delegated value and so they don't count towards the spent limit of delegations.
