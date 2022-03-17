# API Objects

The following objects are parameters for or returned by Enter API methods.

### Block object

Returned by [`eth_getBlockByHash`](https://besu.hyperledger.org/en/stable/Reference/API-Methods/#eth\_getblockbyhash) and [`eth_getBlockByNumber`](https://besu.hyperledger.org/en/stable/Reference/API-Methods/#eth\_getblockbynumber).

&#x20;

&#x20;

| Key              | Type              | Value                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| ---------------- | ----------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| number           | Quantity, Integer | Block number. null when block is pending.                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| Hash             | Data, 32 bytes    | Hash of the block. null when block is pending.                                                                                                                                                                                                                                                                                                                                                                                                                              |
| parentHash       | Data, 32 bytes    | Hash of the parent block.                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| Nonce            | Data, 8 bytes     | Hash of the generated proof of work. null when block is pending.                                                                                                                                                                                                                                                                                                                                                                                                            |
| Sha3Uncles       | Data, 32 bytes    | SHA3 of the uncle’s data in the block.                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| logsBloom        | Data, 256 bytes   | Bloom filter for the block logs. null when block is pending.                                                                                                                                                                                                                                                                                                                                                                                                                |
| transactionsRoot | Data, 32 bytes    | Root of the transaction trie for the block.                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| stateRoot        | Data, 32 bytes    | Root of the final state trie for the block.                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| receiptsRoot     | Data, 32 bytes    | Root of the receipts trie for the block.                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| Miner            | Data, 20 bytes    | Address to pay mining rewards to.                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| Difficulty       | Quantity, Integer | Difficulty for this block.                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| totalDifficulty  | Quantity, Integer | Total difficulty of the chain until this block.                                                                                                                                                                                                                                                                                                                                                                                                                             |
| extraData        | Data              | Extra data field for this block. The first 32 bytes is vanity data you can set using the [--miner-extra-data](https://besu.hyperledger.org/en/stable/Reference/CLI/CLI-Syntax/#miner-extra-data) command line option. Stores extra data when used with [Clique](https://besu.hyperledger.org/en/stable/HowTo/Configure/Consensus-Protocols/Clique/#genesis-file) and [IBFT](https://besu.hyperledger.org/en/stable/HowTo/Configure/Consensus-Protocols/IBFT/#genesis-file). |
| size             | Quantity, Integer | Size of block in bytes.                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| gasLimit         | Quantity          | Maximum gas allowed in this block.                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| gasUsed          | Quantity          | Total gas used by all transactions in this block.                                                                                                                                                                                                                                                                                                                                                                                                                           |
| timestamp        | Quantity          | Unix timestamp for block assembly.                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| transactions     | Array             | Array of [transaction objects](https://besu.hyperledger.org/en/stable/Reference/API-Objects/#transaction-object), or 32 byte transaction hashes depending on the specified boolean parameter.                                                                                                                                                                                                                                                                               |
| uncles           | Array             | Array of uncle hashes.                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| baseFeePerGas    | Quantity          | The block’s [base fee per gas](https://besu.hyperledger.org/en/stable/Concepts/Transactions/Transaction-Types/#eip1559-transactions). This field is empty for blocks created before [EIP-1559](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-1559.md).                                                                                                                                                                                                              |

**Fee history results object**

Returned by [eth\_feeHistory](https://besu.hyperledger.org/en/stable/Reference/API-Methods/#eth\_feehistory) for the requested block range. If blocks in the specified block range are not available, then only the fee history for available blocks is returned.

| Key           | Type              | Value                                                                                                                                                                                                                                                                 |
| ------------- | ----------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| oldestBlock   | Quantity, Integer | Lowest number block of the returned range.                                                                                                                                                                                                                            |
| baseFeePerGas | Array             | Array of block base fees per gas, including an extra block value. The extra value is the next block after the newest block in the returned range. Returns zeroes for blocks created before [EIP-1559](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-1559.md). |
| gasUsedRatio  | Array             | Array of block gas used ratios. These are calculated as the ratio of gasUsed and gasLimit.                                                                                                                                                                            |

&#x20;

**Filter options object**

Parameter for [eth\_newFilter](https://besu.hyperledger.org/en/stable/Reference/API-Methods/#eth\_newfilter), [eth\_getLogs](https://besu.hyperledger.org/en/stable/Reference/API-Methods/#eth\_getlogs), and [priv\_getLogs](https://besu.hyperledger.org/en/stable/Reference/API-Methods/#priv\_getlogs). Used to [filter logs](https://besu.hyperledger.org/en/stable/HowTo/Interact/Filters/Accessing-Logs-Using-JSON-RPC/).

&#x20;

| Key       | Type                         | Required/Optional | Value                                                                                                                                                                                        |
| --------- | ---------------------------- | ----------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| fromBlock | Quantity/Tag                 | Optional          | Integer block number or latest, pending, earliest. See [Block Parameter](https://besu.hyperledger.org/en/stable/HowTo/Interact/APIs/Using-JSON-RPC-API/#block-parameter). Default is latest. |
| toBlock   | Quantity/Tag                 | Optional          | Integer block number or latest, pending, earliest. See [Block Parameter](https://besu.hyperledger.org/en/stable/HowTo/Interact/APIs/Using-JSON-RPC-API/#block-parameter). Default is latest. |
| address   | Data/Array                   | Optional          | Contract address or array of addresses from which [logs](https://besu.hyperledger.org/en/stable/Concepts/Events-and-Logs/)originate.                                                         |
| topics    | Array of Data, 32 bytes each | Optional          | Array of topics by which to [filter logs](https://besu.hyperledger.org/en/stable/Concepts/Events-and-Logs/#topic-filters).                                                                   |

&#x20;

&#x20;

​[eth\_getLogs](https://besu.hyperledger.org/en/stable/Reference/API-Methods/#eth\_getlogs) and [priv\_getLogs](https://besu.hyperledger.org/en/stable/Reference/API-Methods/#priv\_getlogs) have an extra key.

&#x20;

| Key       | Type           | Required/Optional | Value                                                                                                       |
| --------- | -------------- | ----------------- | ----------------------------------------------------------------------------------------------------------- |
| blockHash | Data, 32 bytes | Optional          | Hash of block for which to return logs. If you specify blockHash, you cannot specify fromBlock and toBlock. |

&#x20;

**Log object**

Returned by [eth\_getFilterChanges](https://besu.hyperledger.org/en/stable/Reference/API-Methods/#eth\_getfilterchanges) and [priv\_getLogs](https://besu.hyperledger.org/en/stable/Reference/API-Methods/#priv\_getlogs). [Transaction receipt objects](https://besu.hyperledger.org/en/stable/Reference/API-Objects/#transaction-receipt-object) can contain an array of log objects.

&#x20;

| Key              | Type                         | Value                                                                                                                                                                                                                                |
| ---------------- | ---------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| removed          | Tag                          | true if log removed because of a chain reorganization. false if a valid log.                                                                                                                                                         |
| logIndex         | Quantity, Integer            | Log index position in the block. null when log is pending.                                                                                                                                                                           |
| transactionIndex | Quantity, Integer            | Index position of the starting transaction for the log. null when log is pending.                                                                                                                                                    |
| transactionHash  | Data, 32 bytes               | Hash of the starting transaction for the log. null when log is pending.                                                                                                                                                              |
| blockHash        | Data, 32 bytes               | Hash of the block that includes the log. null when log is pending.                                                                                                                                                                   |
| blockNumber      | Quantity                     | Number of block that includes the log. null when log is pending.                                                                                                                                                                     |
| address          | Data, 20 bytes               | Address the log originated from.                                                                                                                                                                                                     |
| data             | Data                         | Non-indexed arguments of the log.                                                                                                                                                                                                    |
| topics           | Array of Data, 32 bytes each | [Event signature hash](https://besu.hyperledger.org/en/stable/Concepts/Events-and-Logs/#event-signature-hash) and 0 to 3 [indexed log arguments](https://besu.hyperledger.org/en/stable/Concepts/Events-and-Logs/#event-parameters). |

&#x20;

&#x20;

**Miner data object**

Returned by [eth\_getMinerDataByBlockHash](https://besu.hyperledger.org/en/stable/Reference/API-Methods/#eth\_getminerdatabyblockhash) and [eth\_getMinerDataByBlockNumber](https://besu.hyperledger.org/en/stable/Reference/API-Methods/#eth\_getminerdatabyblocknumber).

&#x20;

| Key                  | Type              | Value                                                                                                                                                                                                                 |
| -------------------- | ----------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| netBlockReward       | Quantity, Integer | The net block reward, in Wei, is staticBlockReward + transactionFee + uncleInclusionReward.                                                                                                                           |
| staticBlockReward    | Quantity, Integer | The static block reward, in Wei, is preset on a hard fork.                                                                                                                                                            |
| transactionFee       | Quantity, Integer | The transaction fee, in Wei, is sum of upfront cost - refund amount for all transactions.                                                                                                                             |
| uncleInclusionReward | Quantity, Integer | The uncle inclusion reward, in Wei, is static block reward \* number of ommers/32.                                                                                                                                    |
| uncleRewards         | Map               | Map of uncle block hashes and uncle miner coinbase addresses.                                                                                                                                                         |
| coinbase             | Data, 20 bytes    | Coinbase address.                                                                                                                                                                                                     |
| extraData            | Data              | Extra data field for this block. The first 32 bytes is vanity data you can set using the [--miner-extra-data](https://besu.hyperledger.org/en/stable/Reference/CLI/CLI-Syntax/#miner-extra-data) command line option. |
| difficulty           | Quantity, Integer | Difficulty of this block.                                                                                                                                                                                             |
| totalDifficulty      | Quantity, Integer | Total difficulty of the chain until this block.                                                                                                                                                                       |

&#x20;

&#x20;

**Pending transaction object**

Returned by [txpool\_besuPendingTransactions](https://besu.hyperledger.org/en/stable/Reference/API-Methods/#txpool\_besupendingtransactions).

&#x20;

| Key                  | Type              | Value                                                                                                                                                                                                                                                                                                                                                                          |
| -------------------- | ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| accessList           | Array             | (Optional) List of addresses and storage keys the transaction plans to access. Used in [ACCESS\_LIST transactions](https://besu.hyperledger.org/en/stable/Concepts/Transactions/Transaction-Types/#access\_list-transactions) and may be used in [EIP1559 transactions](https://besu.hyperledger.org/en/stable/Concepts/Transactions/Transaction-Types/#eip1559-transactions). |
| from                 | Data, 20 bytes    | Address of the sender.                                                                                                                                                                                                                                                                                                                                                         |
| gas                  | Quantity          | Gas provided by the sender.                                                                                                                                                                                                                                                                                                                                                    |
| gasPrice             | Quantity          | (Optional) Gas price, in Wei, provided by the sender. Not used only in [EIP1559 transactions](https://besu.hyperledger.org/en/stable/Concepts/Transactions/Transaction-Types/#eip1559-transactions).                                                                                                                                                                           |
| maxPriorityFeePerGas | Quantity, Integer | (Optional) Maximum fee, in Wei, the sender is willing to pay per gas above the base fee. Used only in [EIP1559 transactions](https://besu.hyperledger.org/en/stable/Concepts/Transactions/Transaction-Types/#eip1559-transactions).                                                                                                                                            |
| maxFeePerGas         | Quantity, Integer | (Optional) Maximum total fee (base fee + priority fee), in Wei, the sender is willing to pay per gas. Used only in [EIP1559 transactions](https://besu.hyperledger.org/en/stable/Concepts/Transactions/Transaction-Types/#eip1559-transactions).                                                                                                                               |
| hash                 | Data, 32 bytes    | Hash of the transaction.                                                                                                                                                                                                                                                                                                                                                       |
| input                | Data              | Data sent with the transaction to create or invoke a contract.                                                                                                                                                                                                                                                                                                                 |
| nonce                | Quantity          | Number of transactions made by the sender before this one.                                                                                                                                                                                                                                                                                                                     |
| to                   | Data, 20 bytes    | Address of the receiver. null if a contract creation transaction.                                                                                                                                                                                                                                                                                                              |
| transactionType      | String            | Transaction Type                                                                                                                                                                                                                                                                                                                                                               |
| value                | Quantity          | Value transferred, in Wei.                                                                                                                                                                                                                                                                                                                                                     |
| v                    | Quantity          | ECDSA Recovery ID.                                                                                                                                                                                                                                                                                                                                                             |
| r                    | Data, 32 bytes    | ECDSA signature r.                                                                                                                                                                                                                                                                                                                                                             |
| s                    | Data, 32 bytes    | ECDSA signature s.                                                                                                                                                                                                                                                                                                                                                             |

&#x20;

&#x20;

**Private transaction object**

Returned by [priv\_getPrivateTransaction](https://besu.hyperledger.org/en/stable/Reference/API-Methods/#priv\_getprivatetransaction).

&#x20;

| Key            | Type                         | Value                                                                                                                                                                                                                            |
| -------------- | ---------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| from           | Data, 20 bytes               | Address of the sender.                                                                                                                                                                                                           |
| gas            | Quantity                     | Gas provided by the sender.                                                                                                                                                                                                      |
| gasPrice       | Quantity                     | Gas price, in Wei, provided by the sender.                                                                                                                                                                                       |
| hash           | Data, 32 bytes               | Hash of the transaction.                                                                                                                                                                                                         |
| input          | Data                         | The data to create or invoke a contract.                                                                                                                                                                                         |
| nonce          | Quantity                     | Number of transactions made by the sender to the privacy group before this one.                                                                                                                                                  |
| to             | Data, 20 bytes               | null if a contract creation transaction, otherwise, the contract address.                                                                                                                                                        |
| **value**      | Quantity                     | null because private transactions cannot transfer Ether.                                                                                                                                                                         |
| v              | Quantity                     | ECDSA Recovery ID.                                                                                                                                                                                                               |
| r              | Data, 32 bytes               | ECDSA signature r.                                                                                                                                                                                                               |
| s              | Data, 32 bytes               | ECDSA signature s.                                                                                                                                                                                                               |
| privateFrom    | Data, 32 bytes               | [Tessera](https://docs.tessera.consensys.net) public key of the sender.                                                                                                                                                          |
| privateFor     | Array of Data, 32 bytes each | [Tessera](https://docs.tessera.consensys.net) public keys of recipients. Not returned if using privacyGroupId to [send the transaction](https://besu.hyperledger.org/en/stable/Concepts/Privacy/Privacy-Groups/#privacy-types).  |
| privacyGroupId | Data, 32 bytes               | [Tessera](https://docs.tessera.consensys.net) privacy group ID of recipients. Not returned if using privateFor to [send the transaction](https://besu.hyperledger.org/en/stable/Concepts/Privacy/Privacy-Groups/#privacy-types). |
| restriction    | String                       | <p>Must be <a href="https://besu.hyperledger.org/en/stable/Concepts/Privacy/Private-Transactions/">restricted</a>.</p><p> </p>                                                                                                   |

&#x20;

**Range object**

Returned by [debug\_storageRangeAt](https://besu.hyperledger.org/en/stable/Reference/API-Methods/#debug\_storagerangeat).

| Key     | Type   | Value                                                                    |
| ------- | ------ | ------------------------------------------------------------------------ |
| storage | Object | Key hash and value. Pre-image key is null if it falls outside the cache. |
| nextKey | Hash   | Hash of next key if further storage in range. Otherwise, not included.   |

&#x20;

&#x20;

**Structured log object**

Log information returned as part of the [Trace object](https://besu.hyperledger.org/en/stable/Reference/API-Objects/#trace-object).

&#x20;

| Key                    | Type                    | Value                                                                                                                                                                                                                                                                                                                                            |
| ---------------------- | ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| pc                     | Integer                 | Current program counter.                                                                                                                                                                                                                                                                                                                         |
| op                     | String                  | Current OpCode.                                                                                                                                                                                                                                                                                                                                  |
| gas                    | Integer                 | Gas remaining.                                                                                                                                                                                                                                                                                                                                   |
| gasCost                | Integer                 | Cost in wei of each gas unit.                                                                                                                                                                                                                                                                                                                    |
| depth                  | Integer                 | Execution depth.                                                                                                                                                                                                                                                                                                                                 |
| exceptionalHaltReasons | Array                   | One or more strings representing an error condition causing the EVM execution to terminate. These strings suggest that EVM execution terminated for reasons such as running out of gas or attempting to execute an unknown instruction. Generally a single exceptional halt reason returns but it’s possible for more than one to occur at once. |
| stack                  | Array of 32 byte arrays | EVM execution stack before executing current operation.                                                                                                                                                                                                                                                                                          |
| memory                 | Array of 32 byte arrays | Memory space of the contract before executing current operation.                                                                                                                                                                                                                                                                                 |
| storage                | Object                  | Storage entries changed by the current transaction.                                                                                                                                                                                                                                                                                              |

&#x20;

&#x20;

**Trace object**

Returned by [debug\_traceBlock](https://besu.hyperledger.org/en/stable/Reference/API-Methods/#debug\_traceblock), [debug\_traceBlockByHash](https://besu.hyperledger.org/en/stable/Reference/API-Methods/#debug\_traceblockbyhash), [debug\_traceBlockByNumber](https://besu.hyperledger.org/en/stable/Reference/API-Methods/#debug\_traceblockbynumber), and [debug\_traceTransaction](https://besu.hyperledger.org/en/stable/Reference/API-Methods/#debug\_tracetransaction).

&#x20;

| Key         | Type    | Value                                                            |
| ----------- | ------- | ---------------------------------------------------------------- |
| gas         | Integer | Gas used by the transaction.                                     |
| failed      | Boolean | True if transaction failed, otherwise, false.                    |
| returnValue | String  | Bytes returned from transaction execution (without a 0x prefix). |
| structLogs  | Array   | Array of structured log objects.                                 |

&#x20;

&#x20;

**Transaction object**

Returned by [eth\_getTransactionByHash](https://besu.hyperledger.org/en/stable/Reference/API-Methods/#eth\_gettransactionbyhash), [eth\_getTransactionByBlockHashAndIndex](https://besu.hyperledger.org/en/stable/Reference/API-Methods/#eth\_gettransactionbyblockhashandindex), and [eth\_getTransactionByBlockNumberAndIndex](https://besu.hyperledger.org/en/stable/Reference/API-Methods/#eth\_gettransactionbyblocknumberandindex).

&#x20;

| Key                  | Type              | Value                                                                                                                                                                                                                                                                                                                                                                          |
| -------------------- | ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| accessList           | Array             | (Optional) List of addresses and storage keys the transaction plans to access. Used in [ACCESS\_LIST transactions](https://besu.hyperledger.org/en/stable/Concepts/Transactions/Transaction-Types/#access\_list-transactions) and may be used in [EIP1559 transactions](https://besu.hyperledger.org/en/stable/Concepts/Transactions/Transaction-Types/#eip1559-transactions). |
| blockHash            | Data, 32 bytes    | Hash of the block containing this transaction. null when transaction is pending.                                                                                                                                                                                                                                                                                               |
| blockNumber          | Quantity          | Block number of the block containing this transaction. null when transaction is pending.                                                                                                                                                                                                                                                                                       |
| chainID              | Quantity          | Chain ID.                                                                                                                                                                                                                                                                                                                                                                      |
| from                 | Data, 20  bytes   | Address of the sender.                                                                                                                                                                                                                                                                                                                                                         |
| gas                  | Quantity          | Gas provided by the sender.                                                                                                                                                                                                                                                                                                                                                    |
| gasPrice             | Quantity          | (Optional) Gas price, in Wei, provided by the sender. Not used only in [EIP1559 transactions](https://besu.hyperledger.org/en/stable/Concepts/Transactions/Transaction-Types/#eip1559-transactions).                                                                                                                                                                           |
| maxPriorityFeePerGas | Quantity, Integer | (Optional) Maximum fee, in Wei, the sender is willing to pay per gas above the base fee. Used only in [EIP1559 transactions](https://besu.hyperledger.org/en/stable/Concepts/Transactions/Transaction-Types/#eip1559-transactions).                                                                                                                                            |
| maxFeePerGas         | Quantity, Integer | (Optional) Maximum total fee (base fee + priority fee), in Wei, the sender is willing to pay per gas. Used only in [EIP1559 transactions](https://besu.hyperledger.org/en/stable/Concepts/Transactions/Transaction-Types/#eip1559-transactions).                                                                                                                               |
| hash                 | Data, 32 bytes    | Hash of the transaction.                                                                                                                                                                                                                                                                                                                                                       |
| input                | Data              | Data sent with the transaction to create or invoke a contract. For [private transactions](https://besu.hyperledger.org/en/stable/Concepts/Privacy/Privacy-Overview/), it’s a pointer to the transaction location in [Tessera](https://docs.tessera.consensys.net).                                                                                                             |
| nonce                | Quantity          | Number of transactions made by the sender before this one.                                                                                                                                                                                                                                                                                                                     |
| publicKey            | Data, 64 bytes    | Public key of the sender.                                                                                                                                                                                                                                                                                                                                                      |
| raw                  | Data              | This signed transaction in Recursive Length Prefix (RLP) encoded form.                                                                                                                                                                                                                                                                                                         |
| to                   | Data, 20 bytes    | Address of the receiver. null if a contract creation transaction.                                                                                                                                                                                                                                                                                                              |
| transactionIndex     | Quantity, Integer | Index position of the transaction in the block. null when transaction is pending.                                                                                                                                                                                                                                                                                              |
| transactionType      | String            | Transaction Type.                                                                                                                                                                                                                                                                                                                                                              |
| value                | Quantity          | Value transferred, in Wei.                                                                                                                                                                                                                                                                                                                                                     |
| v                    | Quantity          | ECDSA Recovery ID.                                                                                                                                                                                                                                                                                                                                                             |
| r                    | Data, 32 bytes    | ECDSA signature r.                                                                                                                                                                                                                                                                                                                                                             |
| s                    | Data, 32 bytes    | ECDSA signature s.                                                                                                                                                                                                                                                                                                                                                             |

&#x20;****&#x20;

&#x20;****&#x20;

**Transaction call object**

Parameter for [eth\_call](https://besu.hyperledger.org/en/stable/Reference/API-Methods/#eth\_call) and [eth\_estimateGas](https://besu.hyperledger.org/en/stable/Reference/API-Methods/#eth\_estimategas).

Note

All transaction call object parameters are optional for [eth\_estimateGas](https://besu.hyperledger.org/en/stable/Reference/API-Methods/#eth\_estimategas). Only the to parameter is required for [eth\_call](https://besu.hyperledger.org/en/stable/Reference/API-Methods/#eth\_call).

&#x20;

| Key                  | Type              | Value                                                                                                                                                                                                                                                                                    |
| -------------------- | ----------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| from                 | Data, 20 bytes    | Address of the sender.                                                                                                                                                                                                                                                                   |
| to                   | Data, 20 bytes    | Address of the action receiver.                                                                                                                                                                                                                                                          |
| gas                  | Quantity, Integer | Gas price, in Wei, provided by the sender. The default is 0. Can’t be used only in [EIP1559 transactions](https://besu.hyperledger.org/en/stable/Concepts/Transactions/Transaction-Types/#eip1559-transactions).                                                                         |
| gasPrice             | Quantity, Integer | Gas price, in Wei, provided by the sender. The default is 0. Can’t be used only in [EIP1559 transactions](https://besu.hyperledger.org/en/stable/Concepts/Transactions/Transaction-Types/#eip1559-transactions).                                                                         |
| maxPriorityFeePerGas | Quantity, Integer | Maximum fee, in Wei, the sender is willing to pay per gas above the base fee. Can be used only in [EIP1559 transactions](https://besu.hyperledger.org/en/stable/Concepts/Transactions/Transaction-Types/#eip1559-transactions). If used, must specify maxFeePerGas.                      |
| maxFeePerGas         | Quantity, Integer | Maximum total fee (base fee + priority fee), in Wei, the sender is willing to pay per gas. Can be used only in [EIP1559 transactions](https://besu.hyperledger.org/en/stable/Concepts/Transactions/Transaction-Types/#eip1559-transactions). If used, must specify maxPriorityFeePerGas. |
| value                | Quantity, Integer | Value transferred, in Wei.                                                                                                                                                                                                                                                               |
| data                 | Data              | Hash of the method signature and encoded parameters. For details, see [Ethereum Contract ABI](https://solidity.readthedocs.io/en/develop/abi-spec.html).                                                                                                                                 |
| strict               | Tag               | If true, checks that the from account’s ether balance is sufficient to cover the transaction and gas fee. If false, this balance is not checked. The default is false.                                                                                                                   |

&#x20;

&#x20;

**Transaction receipt object**

Returned by [eth\_getTransactionReceipt](https://besu.hyperledger.org/en/stable/Reference/API-Methods/#eth\_gettransactionreceipt).

&#x20;

| Key               | Type              | Value                                                                                                                                                                                                                                                                                             |
| ----------------- | ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| blockHash         | Data, 32 bytes    | Hash of block containing this transaction.                                                                                                                                                                                                                                                        |
| blockNumber       | Quantity          | Block number of block containing this transaction.                                                                                                                                                                                                                                                |
| contractAddress   | Data, 20 bytes    | Contract address created, if contract creation transaction, otherwise, null.                                                                                                                                                                                                                      |
| cumulativeGasUsed | Quantity          | Total amount of gas used by previous transactions in the block and this transaction.                                                                                                                                                                                                              |
| effectiveGasPrice | Quantity          | The [actual value per gas deducted](https://besu.hyperledger.org/en/stable/Concepts/Transactions/Transaction-Types/#eip1559-transactions) from the sender’s account.                                                                                                                              |
| from              | Data, 20 bytes    | Address of the sender.                                                                                                                                                                                                                                                                            |
| gasUsed           | Quantity          | Amount of gas used by this specific transaction.                                                                                                                                                                                                                                                  |
| logs              | Array             | Array of [log objects](https://besu.hyperledger.org/en/stable/Reference/API-Objects/#log-object) generated by this transaction.                                                                                                                                                                   |
| logsBloom         | Data, 256 bytes   | <p>Data, 256 bytes</p><p>Bloom filter for light clients to quickly retrieve related logs.</p>                                                                                                                                                                                                     |
| status            | Quantity          | Either 0x0 (failure), 0x1 (success), or 0x2 (invalid).                                                                                                                                                                                                                                            |
| to                | Data, 20 bytes    | Address of the receiver, if sending ether, otherwise, null.                                                                                                                                                                                                                                       |
| transactionHash   | Data, 32 bytes    | Hash of the transaction.                                                                                                                                                                                                                                                                          |
| transactionIndex  | Quantity, Integer | Index position of transaction in the block.                                                                                                                                                                                                                                                       |
| transactionType   | String            | Transaction Type.                                                                                                                                                                                                                                                                                 |
| revertReason      | String            | ABI-encoded string that displays the [reason for reverting the transaction](https://besu.hyperledger.org/en/stable/HowTo/Send-Transactions/Revert-Reason/). Only available if revert reason is [enabled](https://besu.hyperledger.org/en/stable/Reference/CLI/CLI-Syntax/#revert-reason-enabled). |

&#x20;

&#x20;

Note

For pre-Byzantium transactions, the transaction receipt object includes the following instead of status:

&#x20;

| Key  | Type           | Value                       |
| ---- | -------------- | --------------------------- |
| root | Data, 32 bytes | Post-transaction state root |

&#x20;

&#x20;

**Transaction trace object**

Returned by [trace\_replayBlockTransactions](https://besu.hyperledger.org/en/stable/Reference/API-Methods/#trace\_replayblocktransactions).

&#x20;

| Key             | Type           | Value                                                                                                            |
| --------------- | -------------- | ---------------------------------------------------------------------------------------------------------------- |
| output          | Boolean        | Transaction result. 1 for success and 0 for failure.                                                             |
| stateDiff       | Object         | [State changes in the requested block](https://besu.hyperledger.org/en/stable/Reference/Trace-Types/#statediff). |
| trace           | Array          | [Ordered list of calls to other contracts](https://besu.hyperledger.org/en/stable/Reference/Trace-Types/#trace). |
| vmTrace         | Object         | [Ordered list of EVM actions](https://besu.hyperledger.org/en/stable/Reference/Trace-Types/#vmtrace).            |
| transactionHash | Data, 32 bytes | Hash of the replayed transaction.                                                                                |

&#x20;

**Private transaction receipt object**

Returned by [priv\_getTransactionReceipt](https://besu.hyperledger.org/en/stable/Reference/API-Methods/#priv\_getTransactionReceipt).

&#x20;

| Key                          | Type                    | Value                                                                                                                                                                                                                                                                                             |
| ---------------------------- | ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| blockHash                    | Data, 32 bytes          | Hash of block containing this transaction.                                                                                                                                                                                                                                                        |
| blockNumber                  | Quantity                | Block number of block containing this transaction.                                                                                                                                                                                                                                                |
| contractAddress              | Data, 20 bytes          | Contract address created if a contract creation transaction, otherwise, null.                                                                                                                                                                                                                     |
| from                         | Data, 20 bytes          | Address of the sender.                                                                                                                                                                                                                                                                            |
| logs                         | Array                   | Array of [log objects](https://besu.hyperledger.org/en/stable/Reference/API-Objects/#log-object) generated by this private transaction.                                                                                                                                                           |
| to                           | Data, 20 bytes          | Address of the receiver, if sending ether, otherwise, null.                                                                                                                                                                                                                                       |
| transactionHash              | Data, 32 bytes          | Hash of the private transaction.                                                                                                                                                                                                                                                                  |
| transactionIndex             | Quantity, Integer       | Index position of transaction in the block.                                                                                                                                                                                                                                                       |
| revertReason                 | String                  | ABI-encoded string that displays the [reason for reverting the transaction](https://besu.hyperledger.org/en/stable/HowTo/Send-Transactions/Revert-Reason/). Only available if revert reason is [enabled](https://besu.hyperledger.org/en/stable/Reference/CLI/CLI-Syntax/#revert-reason-enabled). |
| output                       | Data                    | RLP-encoded return value of a contract call if a value returns, otherwise, null.                                                                                                                                                                                                                  |
| commitmentHash               | Data, 32 bytes          | Hash of the privacy marker transaction.                                                                                                                                                                                                                                                           |
| status                       | Quantity                | Either 0x1 (success) or 0x0 (failure).                                                                                                                                                                                                                                                            |
| privateFrom                  | Data, 32 bytes          | [Tessera](https://docs.tessera.consensys.net) public key of the sender.                                                                                                                                                                                                                           |
| privateFor or privacyGroupId | Array or Data, 32 bytes | [Tessera](https://docs.tessera.consensys.net) public keys or privacy group ID of the recipients.                                                                                                                                                                                                  |
| logsBloom                    | Data, 256 bytes         | Bloom filter for light clients to quickly retrieve related logs.                                                                                                                                                                                                                                  |
