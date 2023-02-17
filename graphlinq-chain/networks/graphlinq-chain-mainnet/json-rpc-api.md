# Json-RPC API

Since GraphLinq Chain is go-ethereum forked, we implement also all of the same routes to interact with the RPC nodes like Ethereum. In order for a software application to interact with the GraphLinq blockchain - either by reading blockchain data or sending transactions to the network - it must connect to a Graphlinq Chain node.

For this purpose, every [GraphLinq Client](execution-clients.md) implements a [JSON-RPC specification](https://github.com/GraphLinq/GraphLinq-Chain/releases), so there are a uniform set of methods that applications can rely on regardless of the specific node or client implementation.

[JSON-RPC](https://www.jsonrpc.org/specification) is a stateless, light-weight remote procedure call (RPC) protocol. It defines several data structures and the rules around their processing. It is transport agnostic in that the concepts can be used within the same process, over sockets, over HTTP, or in many various message passing environments. It uses JSON (RFC 4627) as data format.

### CLIENT IMPLEMENTATIONS <a href="#client-implementations" id="client-implementations"></a>

Ethereum clients each may utilize different programming languages when implementing the JSON-RPC specification. See individual [client documentation](https://ethereum.org/en/developers/docs/nodes-and-clients/#execution-clients) for further details related to specific programming languages. We recommend checking the documentation of each client for the latest API support information.

### CONVENIENCE LIBRARIES <a href="#convenience-libraries" id="convenience-libraries"></a>

While you may choose to interact directly with Ethereum clients via the JSON-RPC API, there are often easier options for dapp developers. Many [JavaScript](https://ethereum.org/en/developers/docs/apis/javascript/#available-libraries) and [backend API](https://ethereum.org/en/developers/docs/apis/backend/#available-libraries) libraries exist to provide wrappers on top of the JSON-RPC API. With these libraries, developers can write intuitive, one-line methods in the programming language of their choice to initialize JSON-RPC requests (under the hood) that interact with Ethereum.

### CONSENSUS CLIENT APIS <a href="#consensus-clients" id="consensus-clients"></a>

This page deals mainly with the JSON-RPC API used by Ethereum execution clients. However, consensus clients also have an RPC API that allows users to query information about the node, request Beacon blocks, Beacon state, and other consensus-related information directly from a node. This API is documented on the [Beacon API webpage](https://ethereum.github.io/beacon-APIs/#/).

An internal API is also used for inter-client communication within a node - that is, it enables the consensus client and execution client to swap data. This is called the 'Engine API' and the specs are available on [Github](https://github.com/ethereum/execution-apis/blob/main/src/engine/common.md).

### EXECUTION CLIENT SPEC <a href="#spec" id="spec"></a>

[Read the full JSON-RPC API spec on GitHub](https://github.com/ethereum/execution-apis).

### CONVENTIONS <a href="#conventions" id="conventions"></a>

#### Hex value encoding <a href="#hex-encoding" id="hex-encoding"></a>

Two key data types get passed over JSON: unformatted byte arrays and quantities. Both are passed with a hex encoding but with different requirements for formatting.

**Quantities**

When encoding quantities (integers, numbers): encode as hex, prefix with "0x", the most compact representation (slight exception: zero should be represented as "0x0").

Here are some examples:

* 0x41 (65 in decimal)
* 0x400 (1024 in decimal)
* WRONG: 0x (should always have at least one digit - zero is "0x0")
* WRONG: 0x0400 (no leading zeroes allowed)
* WRONG: ff (must be prefixed 0x)

#### Unformatted data <a href="#unformatted-data-encoding" id="unformatted-data-encoding"></a>

When encoding unformatted data (byte arrays, account addresses, hashes, bytecode arrays): encode as hex, prefix with "0x", two hex digits per byte.

Here are some examples:

* 0x41 (size 1, "A")
* 0x004200 (size 3, "\0B\0")
* 0x (size 0, "")
* WRONG: 0xf0f0f (must be even number of digits)
* WRONG: 004200 (must be prefixed 0x)

#### The default block parameter <a href="#default-block" id="default-block"></a>

The following methods have an extra default block parameter:

* [eth\_getBalance](https://ethereum.org/en/developers/docs/apis/json-rpc/#eth\_getbalance)
* [eth\_getCode](https://ethereum.org/en/developers/docs/apis/json-rpc/#eth\_getcode)
* [eth\_getTransactionCount](https://ethereum.org/en/developers/docs/apis/json-rpc/#eth\_gettransactioncount)
* [eth\_getStorageAt](https://ethereum.org/en/developers/docs/apis/json-rpc/#eth\_getstorageat)
* [eth\_call](https://ethereum.org/en/developers/docs/apis/json-rpc/#eth\_call)

When requests are made that act on the state of Ethereum, the last default block parameter determines the height of the block.

The following options are possible for the defaultBlock parameter:

* `HEX String` - an integer block number
* `String "earliest"` for the earliest/genesis block
* `String "latest"` - for the latest mined block
* `String "pending"` - for the pending state/transactions

### EXAMPLES <a href="#examples" id="examples"></a>

On this page we provide examples of how to use individual JSON\_RPC API endpoints using the command line tool, [curl](https://curl.se/). These individual endpoint examples are found below in the [Curl examples](https://ethereum.org/en/developers/docs/apis/json-rpc/#curl-examples) section. Further down the page, we also provide an [end-to-end example](https://ethereum.org/en/developers/docs/apis/json-rpc/#usage-example) for compiling and deploying a smart contract using a Geth node, the JSON\_RPC API and curl.

### CURL EXAMPLES <a href="#curl-examples" id="curl-examples"></a>

Examples of using the JSON\_RPC API by making [curl](https://curl.se/) requests to an Ethereum node are provided below. Each example includes a description of the specific endpoint, its parameters, return type, and a worked example of how it should be used.

The curl requests might return an error message relating to the content type. This is because the `--data` option sets the content type to `application/x-www-form-urlencoded`. If your node does complain about this, manually set the header by placing `-H "Content-Type: application/json"` at the start of the call. The examples also do not include the URL/IP & port combination which must be the last argument given to curl (e.g. `127.0.0.1:8545`). A complete curl request including these additional data takes the following form:

```
1curl -H "Content-Type: application/json" -X POST --data '{"jsonrpc":"2.0","method":"web3_clientVersion","params":[],"id":67}' 127.0.0.1:85452
```

### GOSSIP, STATE, HISTORY <a href="#gossip-state-history" id="gossip-state-history"></a>

A handful of core JSON-RPC methods require data from the Ethereum network, and fall neatly into three main categories: _Gossip, State, and History_. Use the links in these sections to jump to each method, or use the table of contents to explore the whole list of methods.

#### Gossip Methods <a href="#gossip-methods" id="gossip-methods"></a>

> These methods track the head of the chain. This is how transactions make their way around the network, find their way into blocks, and how clients find out about new blocks.

* [eth\_blockNumber](https://ethereum.org/en/developers/docs/apis/json-rpc/#eth\_blocknumber)
* [eth\_sendRawTransaction](https://ethereum.org/en/developers/docs/apis/json-rpc/#eth\_sendrawtransaction)

#### State Methods <a href="#state_methods" id="state_methods"></a>

> Methods that report the current state of all the data stored. The "state" is like one big shared piece of RAM, and includes account balances, contract data, and gas estimations.

* [eth\_getBalance](https://ethereum.org/en/developers/docs/apis/json-rpc/#eth\_getbalance)
* [eth\_getStorageAt](https://ethereum.org/en/developers/docs/apis/json-rpc/#eth\_getstorageat)
* [eth\_getTransactionCount](https://ethereum.org/en/developers/docs/apis/json-rpc/#eth\_gettransactioncount)
* [eth\_getCode](https://ethereum.org/en/developers/docs/apis/json-rpc/#eth\_getcode)
* [eth\_call](https://ethereum.org/en/developers/docs/apis/json-rpc/#eth\_call)
* [eth\_estimateGas](https://ethereum.org/en/developers/docs/apis/json-rpc/#eth\_estimategas)

#### History Methods <a href="#history_methods" id="history_methods"></a>

> Fetches historical records of every block back to genesis. This is like one large append-only file, and includes all block headers, block bodies, uncle blocks, and transaction receipts.

* [eth\_getBlockTransactionCountByHash](https://ethereum.org/en/developers/docs/apis/json-rpc/#eth\_getblocktransactioncountbyhash)
* [eth\_getBlockTransactionCountByNumber](https://ethereum.org/en/developers/docs/apis/json-rpc/#eth\_getblocktransactioncountbynumber)
* [eth\_getUncleCountByBlockHash](https://ethereum.org/en/developers/docs/apis/json-rpc/#eth\_getunclecountbyblockhash)
* [eth\_getUncleCountByBlockNumber](https://ethereum.org/en/developers/docs/apis/json-rpc/#eth\_getunclecountbyblocknumber)
* [eth\_getBlockByHash](https://ethereum.org/en/developers/docs/apis/json-rpc/#eth\_getblockbyhash)
* [eth\_getBlockByNumber](https://ethereum.org/en/developers/docs/apis/json-rpc/#eth\_getblockbynumber)
* [eth\_getTransactionByHash](https://ethereum.org/en/developers/docs/apis/json-rpc/#eth\_gettransactionbyhash)
* [eth\_getTransactionByBlockHashAndIndex](https://ethereum.org/en/developers/docs/apis/json-rpc/#eth\_gettransactionbyblockhashandindex)
* [eth\_getTransactionByBlockNumberAndIndex](https://ethereum.org/en/developers/docs/apis/json-rpc/#eth\_gettransactionbyblocknumberandindex)
* [eth\_getTransactionReceipt](https://ethereum.org/en/developers/docs/apis/json-rpc/#eth\_gettransactionreceipt)
* [eth\_getUncleByBlockHashAndIndex](https://ethereum.org/en/developers/docs/apis/json-rpc/#eth\_getunclebyblockhashandindex)
* [eth\_getUncleByBlockNumberAndIndex](https://ethereum.org/en/developers/docs/apis/json-rpc/#eth\_getunclebyblocknumberandindex)

### JSON-RPC API METHODS <a href="#json-rpc-methods" id="json-rpc-methods"></a>

#### web3\_clientVersion <a href="#web3_clientversion" id="web3_clientversion"></a>

Returns the current client version.

**Parameters**

None

**Returns**

`String` - The current client version

**Example**

```
2curl -X POST --data '{"jsonrpc":"2.0","method":"web3_clientVersion","params":[],"id":67}'3// Result4{5  "id":67,6  "jsonrpc":"2.0",7  "result": "Mist/v0.9.3/darwin/go1.4.1"8}9

```

#### web3\_sha3 <a href="#web3_sha3" id="web3_sha3"></a>

Returns Keccak-256 (_not_ the standardized SHA3-256) of the given data.

**Parameters**

1. `DATA` - the data to convert into a SHA3 hash

```
1params: ["0x68656c6c6f20776f726c64"]2
 Copy
```

**Returns**

`DATA` - The SHA3 result of the given string.

**Example**

```
2curl -X POST --data '{"jsonrpc":"2.0","method":"web3_sha3","params":["0x68656c6c6f20776f726c64"],"id":64}'3// Result4{5  "id":64,6  "jsonrpc": "2.0",7  "result": "0x47173285a8d7341e5e972fc677286384f802f8ef42a5ec5f03bbfa254cb01fad"8}9

```

#### net\_version <a href="#net_version" id="net_version"></a>

Returns the current network id.

**Parameters**

None

**Returns**

`String` - The current network id.

The full list of current network IDs is available at [chainlist.org](https://chainlist.org/). Some common ones are: `1`: Ethereum Mainnet `2`: Morden testnet (now deprecated) `3`: Ropsten testnet `4`: Rinkeby testnet `5`: Goerli testnet

**Example**

```
2curl -X POST --data '{"jsonrpc":"2.0","method":"net_version","params":[],"id":67}'3// Result4{5  "id":67,6  "jsonrpc": "2.0",7  "result": "3"8}9
 net_listening
```

Returns `true` if client is actively listening for network connections.

**Parameters**

None

**Returns**

`Boolean` - `true` when listening, otherwise `false`.

**Example**

```
2curl -X POST --data '{"jsonrpc":"2.0","method":"net_listening","params":[],"id":67}'3// Result4{5  "id":67,6  "jsonrpc":"2.0",7  "result":true8}9
```

#### net\_peerCount <a href="#net_peercount" id="net_peercount"></a>

Returns number of peers currently connected to the client.

**Parameters**

None

**Returns**

`QUANTITY` - integer of the number of connected peers.

**Example**

```
2curl -X POST --data '{"jsonrpc":"2.0","method":"net_peerCount","params":[],"id":74}'3// Result4{5  "id":74,6  "jsonrpc": "2.0",7  "result": "0x2" // 28}9
```

#### eth\_protocolVersion <a href="#eth_protocolversion" id="eth_protocolversion"></a>

Returns the current Ethereum protocol version. Note that this method is [not available in Geth](https://github.com/ethereum/go-ethereum/pull/22064#issuecomment-788682924).

**Parameters**

None

**Returns**

`String` - The current Ethereum protocol version

**Example**

```
2curl -X POST --data '{"jsonrpc":"2.0","method":"eth_protocolVersion","params":[],"id":67}'3// Result4{5  "id":67,6  "jsonrpc": "2.0",7  "result": "54"8}9
```

#### eth\_syncing <a href="#eth_syncing" id="eth_syncing"></a>

Returns an object with data about the sync status or `false`.

**Parameters**

None

**Returns**

`Object|Boolean`, An object with sync status data or `FALSE`, when not syncing:

* `startingBlock`: `QUANTITY` - The block at which the import started (will only be reset, after the sync reached his head)
* `currentBlock`: `QUANTITY` - The current block, same as eth\_blockNumber
* `highestBlock`: `QUANTITY` - The estimated highest block

**Example**

```
2curl -X POST --data '{"jsonrpc":"2.0","method":"eth_syncing","params":[],"id":1}'3// Result4{5  "id":1,6  "jsonrpc": "2.0",7  "result": {8    startingBlock: '0x384',9    currentBlock: '0x386',10    highestBlock: '0x454'11  }12}13// Or when not syncing14{15  "id":1,16  "jsonrpc": "2.0",17  "result": false18}19
```

#### eth\_coinbase <a href="#eth_coinbase" id="eth_coinbase"></a>

Returns the client coinbase address.

**Parameters**

None

**Returns**

`DATA`, 20 bytes - the current coinbase address.

**Example**

```
2curl -X POST --data '{"jsonrpc":"2.0","method":"eth_coinbase","params":[],"id":64}'3// Result4{5  "id":64,6  "jsonrpc": "2.0",7  "result": "0x407d73d8a49eeb85d32cf465507dd71d507100c1"8}9
```

#### eth\_mining <a href="#eth_mining" id="eth_mining"></a>

Returns `true` if client is actively mining new blocks.

**Parameters**

None

**Returns**

`Boolean` - returns `true` of the client is mining, otherwise `false`.

**Example**

```
2curl -X POST --data '{"jsonrpc":"2.0","method":"eth_mining","params":[],"id":71}'3//4{5  "id":71,6  "jsonrpc": "2.0",7  "result": true8}9
```

#### eth\_hashrate <a href="#eth_hashrate" id="eth_hashrate"></a>

Returns the number of hashes per second that the node is mining with.

**Parameters**

None

**Returns**

`QUANTITY` - number of hashes per second.

**Example**

```
2curl -X POST --data '{"jsonrpc":"2.0","method":"eth_hashrate","params":[],"id":71}'3// Result4{5  "id":71,6  "jsonrpc": "2.0",7  "result": "0x38a"8}9
```

#### eth\_gasPrice <a href="#eth_gasprice" id="eth_gasprice"></a>

Returns the current price per gas in wei.

**Parameters**

None

**Returns**

`QUANTITY` - integer of the current gas price in wei.

**Example**

```
2curl -X POST --data '{"jsonrpc":"2.0","method":"eth_gasPrice","params":[],"id":73}'3// Result4{5  "id":73,6  "jsonrpc": "2.0",7  "result": "0x1dfd14000" // 8049999872 Wei8}9
```

#### eth\_accounts <a href="#eth_accounts" id="eth_accounts"></a>

Returns a list of addresses owned by client.

**Parameters**

None

**Returns**

`Array of DATA`, 20 Bytes - addresses owned by the client.

**Example**

```
2curl -X POST --data '{"jsonrpc":"2.0","method":"eth_accounts","params":[],"id":1}'3// Result4{5  "id":1,6  "jsonrpc": "2.0",7  "result": ["0x407d73d8a49eeb85d32cf465507dd71d507100c1"]8}9
```

#### eth\_blockNumber <a href="#eth_blocknumber" id="eth_blocknumber"></a>

Returns the number of most recent block.

**Parameters**

None

**Returns**

`QUANTITY` - integer of the current block number the client is on.

**Example**

```
2curl -X POST --data '{"jsonrpc":"2.0","method":"eth_blockNumber","params":[],"id":83}'3// Result4{5  "id":83,6  "jsonrpc": "2.0",7  "result": "0x4b7" // 12078}9
```

#### eth\_getBalance <a href="#eth_getbalance" id="eth_getbalance"></a>

Returns the balance of the account of given address.

**Parameters**

1. `DATA`, 20 Bytes - address to check for balance.
2. `QUANTITY|TAG` - integer block number, or the string `"latest"`, `"earliest"` or `"pending"`, see the [default block parameter](https://ethereum.org/en/developers/docs/apis/json-rpc/#default-block-parameter)

```
1params: ["0x407d73d8a49eeb85d32cf465507dd71d507100c1", "latest"]2
 Copy
```

**Returns**

`QUANTITY` - integer of the current balance in wei.

**Example**

```
2curl -X POST --data '{"jsonrpc":"2.0","method":"eth_getBalance","params":["0x407d73d8a49eeb85d32cf465507dd71d507100c1", "latest"],"id":1}'3// Result4{5  "id":1,6  "jsonrpc": "2.0",7  "result": "0x0234c8a3397aab58" // 1589724902343750008}9
eth_getStorageAt
```

Returns the value from a storage position at a given address.

**Parameters**

1. `DATA`, 20 Bytes - address of the storage.
2. `QUANTITY` - integer of the position in the storage.
3. `QUANTITY|TAG` - integer block number, or the string `"latest"`, `"earliest"` or `"pending"`, see the [default block parameter](https://ethereum.org/en/developers/docs/apis/json-rpc/#default-block-parameter)

**Returns**

`DATA` - the value at this storage position.

**Example** Calculating the correct position depends on the storage to retrieve. Consider the following contract deployed at `0x295a70b2de5e3953354a6a8344e616ed314d7251` by address `0x391694e7e0b0cce554cb130d723a9d27458f9298`.

```
1contract Storage {2    uint pos0;3    mapping(address => uint) pos1;4    function Storage() {5        pos0 = 1234;6        pos1[msg.sender] = 5678;7    }8}9
```

Retrieving the value of pos0 is straight forward:

```
1curl -X POST --data '{"jsonrpc":"2.0", "method": "eth_getStorageAt", "params": ["0x295a70b2de5e3953354a6a8344e616ed314d7251", "0x0", "latest"], "id": 1}' localhost:85452{"jsonrpc":"2.0","id":1,"result":"0x00000000000000000000000000000000000000000000000000000000000004d2"}3
 Copy
```

Retrieving an element of the map is harder. The position of an element in the map is calculated with:

```
1keccack(LeftPad32(key, 0), LeftPad32(map position, 0))2
 Copy
```

This means to retrieve the storage on pos1\["0x391694e7e0b0cce554cb130d723a9d27458f9298"] we need to calculate the position with:

```
1keccak(2  decodeHex(3    "000000000000000000000000391694e7e0b0cce554cb130d723a9d27458f9298" +4      "0000000000000000000000000000000000000000000000000000000000000001"5  )6)7
 Copy
```

The geth console which comes with the web3 library can be used to make the calculation:

```
1> var key = "000000000000000000000000391694e7e0b0cce554cb130d723a9d27458f9298" + "0000000000000000000000000000000000000000000000000000000000000001"2undefined3> web3.sha3(key, {"encoding": "hex"})4"0x6661e9d6d8b923d5bbaab1b96e1dd51ff6ea2a93520fdc9eb75d059238b8c5e9"5
 Copy
```

Now to fetch the storage:

```
1curl -X POST --data '{"jsonrpc":"2.0", "method": "eth_getStorageAt", "params": ["0x295a70b2de5e3953354a6a8344e616ed314d7251", "0x6661e9d6d8b923d5bbaab1b96e1dd51ff6ea2a93520fdc9eb75d059238b8c5e9", "latest"], "id": 1}' localhost:85452{"jsonrpc":"2.0","id":1,"result":"0x000000000000000000000000000000000000000000000000000000000000162e"}3
 Copy
```

#### eth\_getTransactionCount <a href="#eth_gettransactioncount" id="eth_gettransactioncount"></a>

Returns the number of transactions _sent_ from an address.

**Parameters**

1. `DATA`, 20 Bytes - address.
2. `QUANTITY|TAG` - integer block number, or the string `"latest"`, `"earliest"` or `"pending"`, see the [default block parameter](https://ethereum.org/en/developers/docs/apis/json-rpc/#default-block-parameter)

```
1params: [2  "0x407d73d8a49eeb85d32cf465507dd71d507100c1",3  "latest", // state at the latest block4]5
 Copy
```

**Returns**

`QUANTITY` - integer of the number of transactions send from this address.

**Example**

```
2curl -X POST --data '{"jsonrpc":"2.0","method":"eth_getTransactionCount","params":["0x407d73d8a49eeb85d32cf465507dd71d507100c1","latest"],"id":1}'3// Result4{5  "id":1,6  "jsonrpc": "2.0",7  "result": "0x1" // 18}9
```

#### eth\_getBlockTransactionCountByHash <a href="#eth_getblocktransactioncountbyhash" id="eth_getblocktransactioncountbyhash"></a>

Returns the number of transactions in a block from a block matching the given block hash.

**Parameters**

1. `DATA`, 32 Bytes - hash of a block

```
1params: ["0xb903239f8543d04b5dc1ba6579132b143087c68db1b2168786408fcbce568238"]2
 Copy
```

**Returns**

`QUANTITY` - integer of the number of transactions in this block.

**Example**

```
2curl -X POST --data '{"jsonrpc":"2.0","method":"eth_getBlockTransactionCountByHash","params":["0xb903239f8543d04b5dc1ba6579132b143087c68db1b2168786408fcbce568238"],"id":1}'3// Result4{5  "id":1,6  "jsonrpc": "2.0",7  "result": "0xb" // 118}9
```

#### eth\_getBlockTransactionCountByNumber <a href="#eth_getblocktransactioncountbynumber" id="eth_getblocktransactioncountbynumber"></a>

Returns the number of transactions in a block matching the given block number.

**Parameters**

1. `QUANTITY|TAG` - integer of a block number, or the string `"earliest"`, `"latest"` or `"pending"`, as in the [default block parameter](https://ethereum.org/en/developers/docs/apis/json-rpc/#default-block-parameter).

```
1params: [2  "0xe8", // 2323]4
 Copy
```

**Returns**

`QUANTITY` - integer of the number of transactions in this block.

**Example**

```
2curl -X POST --data '{"jsonrpc":"2.0","method":"eth_getBlockTransactionCountByNumber","params":["0xe8"],"id":1}'3// Result4{5  "id":1,6  "jsonrpc": "2.0",7  "result": "0xa" // 108}9
```

#### eth\_getUncleCountByBlockHash <a href="#eth_getunclecountbyblockhash" id="eth_getunclecountbyblockhash"></a>

Returns the number of uncles in a block from a block matching the given block hash.

**Parameters**

1. `DATA`, 32 Bytes - hash of a block

```
1params: ["0xb903239f8543d04b5dc1ba6579132b143087c68db1b2168786408fcbce568238"]2
 Copy
```

**Returns**

`QUANTITY` - integer of the number of uncles in this block.

**Example**

```
2curl -X POST --data '{"jsonrpc":"2.0","method":"eth_getUncleCountByBlockHash","params":["0xb903239f8543d04b5dc1ba6579132b143087c68db1b2168786408fcbce568238"],"id":1}'3// Result4{5  "id":1,6  "jsonrpc": "2.0",7  "result": "0x1" // 18}9
```

#### eth\_getUncleCountByBlockNumber <a href="#eth_getunclecountbyblocknumber" id="eth_getunclecountbyblocknumber"></a>

Returns the number of uncles in a block from a block matching the given block number.

**Parameters**

1. `QUANTITY|TAG` - integer of a block number, or the string "latest", "earliest" or "pending", see the [default block parameter](https://ethereum.org/en/developers/docs/apis/json-rpc/#default-block-parameter)

```
1params: [2  "0xe8", // 2323]4
 Copy
```

**Returns**

`QUANTITY` - integer of the number of uncles in this block.

**Example**

```
2curl -X POST --data '{"jsonrpc":"2.0","method":"eth_getUncleCountByBlockNumber","params":["0xe8"],"id":1}'3// Result4{5  "id":1,6  "jsonrpc": "2.0",7  "result": "0x1" // 18}9
```

#### eth\_getCode <a href="#eth_getcode" id="eth_getcode"></a>

Returns code at a given address.

**Parameters**

1. `DATA`, 20 Bytes - address
2. `QUANTITY|TAG` - integer block number, or the string `"latest"`, `"earliest"` or `"pending"`, see the [default block parameter](https://ethereum.org/en/developers/docs/apis/json-rpc/#default-block-parameter)

```
1params: [2  "0xa94f5374fce5edbc8e2a8697c15331677e6ebf0b",3  "0x2", // 24]5
 Copy
```

**Returns**

`DATA` - the code from the given address.

**Example**

```
2curl -X POST --data '{"jsonrpc":"2.0","method":"eth_getCode","params":["0xa94f5374fce5edbc8e2a8697c15331677e6ebf0b", "0x2"],"id":1}'3// Result4{5  "id":1,6  "jsonrpc": "2.0",7  "result": "0x600160008035811a818181146012578301005b601b6001356025565b8060005260206000f25b600060078202905091905056"8}9
```

#### eth\_sign <a href="#eth_sign" id="eth_sign"></a>

The sign method calculates an Ethereum specific signature with: `sign(keccak256("\x19Ethereum Signed Message:\n" + len(message) + message)))`.

By adding a prefix to the message makes the calculated signature recognizable as an Ethereum specific signature. This prevents misuse where a malicious dapp can sign arbitrary data (e.g. transaction) and use the signature to impersonate the victim.

Note: the address to sign with must be unlocked.

**Parameters**

1. `DATA`, 20 Bytes - address
2. `DATA`, N Bytes - message to sign

**Returns**

`DATA`: Signature

**Example**

```
2curl -X POST --data '{"jsonrpc":"2.0","method":"eth_sign","params":["0x9b2055d370f73ec7d8a03e965129118dc8f5bf83", "0xdeadbeaf"],"id":1}'3// Result4{5  "id":1,6  "jsonrpc": "2.0",7  "result": "0xa3f20717a250c2b0b729b7e5becbff67fdaef7e0699da4de7ca5895b02a170a12d887fd3b17bfdce3481f10bea41f45ba9f709d39ce8325427b57afcfc994cee1b"8}9
```

#### eth\_signTransaction <a href="#eth_signtransaction" id="eth_signtransaction"></a>

Signs a transaction that can be submitted to the network at a later time using with [eth\_sendRawTransaction](https://ethereum.org/en/developers/docs/apis/json-rpc/#eth\_sendrawtransaction).

**Parameters**

1. `Object` - The transaction object

* `from`: `DATA`, 20 Bytes - The address the transaction is sent from.
* `to`: `DATA`, 20 Bytes - (optional when creating new contract) The address the transaction is directed to.
* `gas`: `QUANTITY` - (optional, default: 90000) Integer of the gas provided for the transaction execution. It will return unused gas.
* `gasPrice`: `QUANTITY` - (optional, default: To-Be-Determined) Integer of the gasPrice used for each paid gas, in Wei.
* `value`: `QUANTITY` - (optional) Integer of the value sent with this transaction, in Wei.
* `data`: `DATA` - The compiled code of a contract OR the hash of the invoked method signature and encoded parameters.
* `nonce`: `QUANTITY` - (optional) Integer of a nonce. This allows to overwrite your own pending transactions that use the same nonce.

**Returns**

`DATA`, The signed transaction object.

**Example**

```
2curl -X POST --data '{"id": 1,"jsonrpc": "2.0","method": "eth_signTransaction","params": [{"data":"0xd46e8dd67c5d32be8d46e8dd67c5d32be8058bb8eb970870f072445675058bb8eb970870f072445675","from": "0xb60e8dd61c5d32be8058bb8eb970870f07233155","gas": "0x76c0","gasPrice": "0x9184e72a000","to": "0xd46e8dd67c5d32be8058bb8eb970870f07244567","value": "0x9184e72a"}]}'3// Result4{5    "id": 1,6    "jsonrpc": "2.0",7    "result": "0xa3f20717a250c2b0b729b7e5becbff67fdaef7e0699da4de7ca5895b02a170a12d887fd3b17bfdce3481f10bea41f45ba9f709d39ce8325427b57afcfc994cee1b"8}9
```

#### eth\_sendTransaction <a href="#eth_sendtransaction" id="eth_sendtransaction"></a>

Creates new message call transaction or a contract creation, if the data field contains code.

**Parameters**

1. `Object` - The transaction object

* `from`: `DATA`, 20 Bytes - The address the transaction is sent from.
* `to`: `DATA`, 20 Bytes - (optional when creating new contract) The address the transaction is directed to.
* `gas`: `QUANTITY` - (optional, default: 90000) Integer of the gas provided for the transaction execution. It will return unused gas.
* `gasPrice`: `QUANTITY` - (optional, default: To-Be-Determined) Integer of the gasPrice used for each paid gas.
* `value`: `QUANTITY` - (optional) Integer of the value sent with this transaction.
* `data`: `DATA` - The compiled code of a contract OR the hash of the invoked method signature and encoded parameters.
* `nonce`: `QUANTITY` - (optional) Integer of a nonce. This allows to overwrite your own pending transactions that use the same nonce.

```
1params: [2  {3    from: "0xb60e8dd61c5d32be8058bb8eb970870f07233155",4    to: "0xd46e8dd67c5d32be8058bb8eb970870f07244567",5    gas: "0x76c0", // 304006    gasPrice: "0x9184e72a000", // 100000000000007    value: "0x9184e72a", // 24414062508    data: "0xd46e8dd67c5d32be8d46e8dd67c5d32be8058bb8eb970870f072445675058bb8eb970870f072445675",9  },10]11
Show all Copy
```

**Returns**

`DATA`, 32 Bytes - the transaction hash, or the zero hash if the transaction is not yet available.

Use [eth\_getTransactionReceipt](https://ethereum.org/en/developers/docs/apis/json-rpc/#eth\_gettransactionreceipt) to get the contract address, after the transaction was mined, when you created a contract.

**Example**

```
1// Request2curl -X POST --data '{"jsonrpc":"2.0","method":"eth_sendTransaction","params":[{see above}],"id":1}'3// Result4{5  "id":1,6  "jsonrpc": "2.0",7  "result": "0xe670ec64341771606e55d6b4ca35a1a6b75ee3d5145a99d05921026d1527331"8}9
 Copy
```

#### eth\_sendRawTransaction <a href="#eth_sendrawtransaction" id="eth_sendrawtransaction"></a>

Creates new message call transaction or a contract creation for signed transactions.

**Parameters**

1. `DATA`, The signed transaction data.

```
1params: [2  "0xd46e8dd67c5d32be8d46e8dd67c5d32be8058bb8eb970870f072445675058bb8eb970870f072445675",3]4
 Copy
```

**Returns**

`DATA`, 32 Bytes - the transaction hash, or the zero hash if the transaction is not yet available.

Use [eth\_getTransactionReceipt](https://ethereum.org/en/developers/docs/apis/json-rpc/#eth\_gettransactionreceipt) to get the contract address, after the transaction was mined, when you created a contract.

**Example**

```
1// Request2curl -X POST --data '{"jsonrpc":"2.0","method":"eth_sendRawTransaction","params":[{see above}],"id":1}'3// Result4{5  "id":1,6  "jsonrpc": "2.0",7  "result": "0xe670ec64341771606e55d6b4ca35a1a6b75ee3d5145a99d05921026d1527331"8}9
 Copy
```

#### eth\_call <a href="#eth_call" id="eth_call"></a>

Executes a new message call immediately without creating a transaction on the block chain.

**Parameters**

1. `Object` - The transaction call object

* `from`: `DATA`, 20 Bytes - (optional) The address the transaction is sent from.
* `to`: `DATA`, 20 Bytes - The address the transaction is directed to.
* `gas`: `QUANTITY` - (optional) Integer of the gas provided for the transaction execution. eth\_call consumes zero gas, but this parameter may be needed by some executions.
* `gasPrice`: `QUANTITY` - (optional) Integer of the gasPrice used for each paid gas
* `value`: `QUANTITY` - (optional) Integer of the value sent with this transaction
* `data`: `DATA` - (optional) Hash of the method signature and encoded parameters. For details see [Ethereum Contract ABI in the Solidity documentation](https://docs.soliditylang.org/en/latest/abi-spec.html)

2. `QUANTITY|TAG` - integer block number, or the string `"latest"`, `"earliest"` or `"pending"`, see the [default block parameter](https://ethereum.org/en/developers/docs/apis/json-rpc/#default-block-parameter)

**Returns**

`DATA` - the return value of executed contract.

**Example**

```
1// Request2curl -X POST --data '{"jsonrpc":"2.0","method":"eth_call","params":[{see above}],"id":1}'3// Result4{5  "id":1,6  "jsonrpc": "2.0",7  "result": "0x"8}9
 Copy
```

#### eth\_estimateGas <a href="#eth_estimategas" id="eth_estimategas"></a>

Generates and returns an estimate of how much gas is necessary to allow the transaction to complete. The transaction will not be added to the blockchain. Note that the estimate may be significantly more than the amount of gas actually used by the transaction, for a variety of reasons including EVM mechanics and node performance.

**Parameters**

See [eth\_call](https://ethereum.org/en/developers/docs/apis/json-rpc/#eth\_call) parameters, expect that all properties are optional. If no gas limit is specified geth uses the block gas limit from the pending block as an upper bound. As a result the returned estimate might not be enough to executed the call/transaction when the amount of gas is higher than the pending block gas limit.

**Returns**

`QUANTITY` - the amount of gas used.

**Example**

```
1// Request2curl -X POST --data '{"jsonrpc":"2.0","method":"eth_estimateGas","params":[{see above}],"id":1}'3// Result4{5  "id":1,6  "jsonrpc": "2.0",7  "result": "0x5208" // 210008}9
 Copy
```

#### eth\_getBlockByHash <a href="#eth_getblockbyhash" id="eth_getblockbyhash"></a>

Returns information about a block by hash.

**Parameters**

1. `DATA`, 32 Bytes - Hash of a block.
2. `Boolean` - If `true` it returns the full transaction objects, if `false` only the hashes of the transactions.

```
1params: [2  "0xdc0818cf78f21a8e70579cb46a43643f78291264dda342ae31049421c82d21ae",3  false,4]5
 Copy
```

**Returns**

`Object` - A block object, or `null` when no block was found:

* `number`: `QUANTITY` - the block number. `null` when its pending block.
* `hash`: `DATA`, 32 Bytes - hash of the block. `null` when its pending block.
* `parentHash`: `DATA`, 32 Bytes - hash of the parent block.
* `nonce`: `DATA`, 8 Bytes - hash of the generated proof-of-work. `null` when its pending block.
* `sha3Uncles`: `DATA`, 32 Bytes - SHA3 of the uncles data in the block.
* `logsBloom`: `DATA`, 256 Bytes - the bloom filter for the logs of the block. `null` when its pending block.
* `transactionsRoot`: `DATA`, 32 Bytes - the root of the transaction trie of the block.
* `stateRoot`: `DATA`, 32 Bytes - the root of the final state trie of the block.
* `receiptsRoot`: `DATA`, 32 Bytes - the root of the receipts trie of the block.
* `miner`: `DATA`, 20 Bytes - the address of the beneficiary to whom the mining rewards were given.
* `difficulty`: `QUANTITY` - integer of the difficulty for this block.
* `totalDifficulty`: `QUANTITY` - integer of the total difficulty of the chain until this block.
* `extraData`: `DATA` - the "extra data" field of this block.
* `size`: `QUANTITY` - integer the size of this block in bytes.
* `gasLimit`: `QUANTITY` - the maximum gas allowed in this block.
* `gasUsed`: `QUANTITY` - the total used gas by all transactions in this block.
* `timestamp`: `QUANTITY` - the unix timestamp for when the block was collated.
* `transactions`: `Array` - Array of transaction objects, or 32 Bytes transaction hashes depending on the last given parameter.
* `uncles`: `Array` - Array of uncle hashes.

**Example**

```
1// Request2curl -X POST --data '{"jsonrpc":"2.0","method":"eth_getBlockByHash","params":["0xdc0818cf78f21a8e70579cb46a43643f78291264dda342ae31049421c82d21ae", false],"id":1}'3// Result4{5{6"jsonrpc": "2.0",7"id": 1,8"result": {9    "difficulty": "0x4ea3f27bc",10    "extraData": "0x476574682f4c5649562f76312e302e302f6c696e75782f676f312e342e32",11    "gasLimit": "0x1388",12    "gasUsed": "0x0",13    "hash": "0xdc0818cf78f21a8e70579cb46a43643f78291264dda342ae31049421c82d21ae",14    "logsBloom": "0x00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000",15    "miner": "0xbb7b8287f3f0a933474a79eae42cbca977791171",16    "mixHash": "0x4fffe9ae21f1c9e15207b1f472d5bbdd68c9595d461666602f2be20daf5e7843",17    "nonce": "0x689056015818adbe",18    "number": "0x1b4",19    "parentHash": "0xe99e022112df268087ea7eafaf4790497fd21dbeeb6bd7a1721df161a6657a54",20    "receiptsRoot": "0x56e81f171bcc55a6ff8345e692c0f86e5b48e01b996cadc001622fb5e363b421",21    "sha3Uncles": "0x1dcc4de8dec75d7aab85b567b6ccd41ad312451b948a7413f0a142fd40d49347",22    "size": "0x220",23    "stateRoot": "0xddc8b0234c2e0cad087c8b389aa7ef01f7d79b2570bccb77ce48648aa61c904d",24    "timestamp": "0x55ba467c",25    "totalDifficulty": "0x78ed983323d",26    "transactions": [27    ],28    "transactionsRoot": "0x56e81f171bcc55a6ff8345e692c0f86e5b48e01b996cadc001622fb5e363b421",29    "uncles": [30    ]31}32}33
Show all Copy
```

#### eth\_getBlockByNumber <a href="#eth_getblockbynumber" id="eth_getblockbynumber"></a>

Returns information about a block by block number.

**Parameters**

1. `QUANTITY|TAG` - integer of a block number, or the string `"earliest"`, `"latest"` or `"pending"`, as in the [default block parameter](https://ethereum.org/en/developers/docs/apis/json-rpc/#default-block-parameter).
2. `Boolean` - If `true` it returns the full transaction objects, if `false` only the hashes of the transactions.

```
1params: [2  "0x1b4", // 4363  true,4]5
 Copy
```

**Returns** See [eth\_getBlockByHash](https://ethereum.org/en/developers/docs/apis/json-rpc/#eth\_getblockbyhash)

**Example**

```
1// Request2curl -X POST --data '{"jsonrpc":"2.0","method":"eth_getBlockByNumber","params":["0x1b4", true],"id":1}'3
 Copy
```

Result see [eth\_getBlockByHash](https://ethereum.org/en/developers/docs/apis/json-rpc/#eth\_getblockbyhash)

#### eth\_getTransactionByHash <a href="#eth_gettransactionbyhash" id="eth_gettransactionbyhash"></a>

Returns the information about a transaction requested by transaction hash.

**Parameters**

1. `DATA`, 32 Bytes - hash of a transaction

```
1params: ["0x88df016429689c079f3b2f6ad39fa052532c56795b733da78a91ebe6a713944b"]2
 Copy
```

**Returns**

`Object` - A transaction object, or `null` when no transaction was found:

* `blockHash`: `DATA`, 32 Bytes - hash of the block where this transaction was in. `null` when its pending.
* `blockNumber`: `QUANTITY` - block number where this transaction was in. `null` when its pending.
* `from`: `DATA`, 20 Bytes - address of the sender.
* `gas`: `QUANTITY` - gas provided by the sender.
* `gasPrice`: `QUANTITY` - gas price provided by the sender in Wei.
* `hash`: `DATA`, 32 Bytes - hash of the transaction.
* `input`: `DATA` - the data send along with the transaction.
* `nonce`: `QUANTITY` - the number of transactions made by the sender prior to this one.
* `to`: `DATA`, 20 Bytes - address of the receiver. `null` when its a contract creation transaction.
* `transactionIndex`: `QUANTITY` - integer of the transactions index position in the block. `null` when its pending.
* `value`: `QUANTITY` - value transferred in Wei.
* `v`: `QUANTITY` - ECDSA recovery id
* `r`: `QUANTITY` - ECDSA signature r
* `s`: `QUANTITY` - ECDSA signature s

**Example**

```
1// Request2curl -X POST --data '{"jsonrpc":"2.0","method":"eth_getTransactionByHash","params":["0x88df016429689c079f3b2f6ad39fa052532c56795b733da78a91ebe6a713944b"],"id":1}'3// Result4{5  "jsonrpc":"2.0",6  "id":1,7  "result":{8    "blockHash":"0x1d59ff54b1eb26b013ce3cb5fc9dab3705b415a67127a003c3e61eb445bb8df2",9    "blockNumber":"0x5daf3b", // 613970710    "from":"0xa7d9ddbe1f17865597fbd27ec712455208b6b76d",11    "gas":"0xc350", // 5000012    "gasPrice":"0x4a817c800", // 2000000000013    "hash":"0x88df016429689c079f3b2f6ad39fa052532c56795b733da78a91ebe6a713944b",14    "input":"0x68656c6c6f21",15    "nonce":"0x15", // 2116    "to":"0xf02c1c8e6114b1dbe8937a39260b5b0a374432bb",17    "transactionIndex":"0x41", // 6518    "value":"0xf3dbb76162000", // 429000000000000019    "v":"0x25", // 3720    "r":"0x1b5e176d927f8e9ab405058b2d2457392da3e20f328b16ddabcebc33eaac5fea",21    "s":"0x4ba69724e8f69de52f0125ad8b3c5c2cef33019bac3249e2c0a2192766d1721c"22  }23}24
Show all Copy
```

#### eth\_getTransactionByBlockHashAndIndex <a href="#eth_gettransactionbyblockhashandindex" id="eth_gettransactionbyblockhashandindex"></a>

Returns information about a transaction by block hash and transaction index position.

**Parameters**

1. `DATA`, 32 Bytes - hash of a block.
2. `QUANTITY` - integer of the transaction index position.

```
1params: [2  "0xe670ec64341771606e55d6b4ca35a1a6b75ee3d5145a99d05921026d1527331",3  "0x0", // 04]5
 Copy
```

**Returns** See [eth\_getTransactionByHash](https://ethereum.org/en/developers/docs/apis/json-rpc/#eth\_gettransactionbyhash)

**Example**

```
1// Request2curl -X POST --data '{"jsonrpc":"2.0","method":"eth_getTransactionByBlockHashAndIndex","params":["0xc6ef2fc5426d6ad6fd9e2a26abeab0aa2411b7ab17f30a99d3cb96aed1d1055b", "0x0"],"id":1}'3
 Copy
```

Result see [eth\_getTransactionByHash](https://ethereum.org/en/developers/docs/apis/json-rpc/#eth\_gettransactionbyhash)

#### eth\_getTransactionByBlockNumberAndIndex <a href="#eth_gettransactionbyblocknumberandindex" id="eth_gettransactionbyblocknumberandindex"></a>

Returns information about a transaction by block number and transaction index position.

**Parameters**

1. `QUANTITY|TAG` - a block number, or the string `"earliest"`, `"latest"` or `"pending"`, as in the [default block parameter](https://ethereum.org/en/developers/docs/apis/json-rpc/#default-block-parameter).
2. `QUANTITY` - the transaction index position.

```
1params: [2  "0x29c", // 6683  "0x0", // 04]5
 Copy
```

**Returns** See [eth\_getTransactionByHash](https://ethereum.org/en/developers/docs/apis/json-rpc/#eth\_gettransactionbyhash)

**Example**

```
1// Request2curl -X POST --data '{"jsonrpc":"2.0","method":"eth_getTransactionByBlockNumberAndIndex","params":["0x29c", "0x0"],"id":1}'3
 Copy
```

Result see [eth\_getTransactionByHash](https://ethereum.org/en/developers/docs/apis/json-rpc/#eth\_gettransactionbyhash)

#### eth\_getTransactionReceipt <a href="#eth_gettransactionreceipt" id="eth_gettransactionreceipt"></a>

Returns the receipt of a transaction by transaction hash.

**Note** That the receipt is not available for pending transactions.

**Parameters**

1. `DATA`, 32 Bytes - hash of a transaction

```
1params: ["0x85d995eba9763907fdf35cd2034144dd9d53ce32cbec21349d4b12823c6860c5"]2
 Copy
```

**Returns** `Object` - A transaction receipt object, or `null` when no receipt was found:

* `transactionHash` : `DATA`, 32 Bytes - hash of the transaction.
* `transactionIndex`: `QUANTITY` - integer of the transactions index position in the block.
* `blockHash`: `DATA`, 32 Bytes - hash of the block where this transaction was in.
* `blockNumber`: `QUANTITY` - block number where this transaction was in.
* `from`: `DATA`, 20 Bytes - address of the sender.
* `to`: `DATA`, 20 Bytes - address of the receiver. null when its a contract creation transaction.
* `cumulativeGasUsed` : `QUANTITY` - The total amount of gas used when this transaction was executed in the block.
* `effectiveGasPrice` : `QUANTITY` - The sum of the base fee and tip paid per unit of gas.
* `gasUsed` : `QUANTITY` - The amount of gas used by this specific transaction alone.
* `contractAddress` : `DATA`, 20 Bytes - The contract address created, if the transaction was a contract creation, otherwise `null`.
* `logs`: `Array` - Array of log objects, which this transaction generated.
* `logsBloom`: `DATA`, 256 Bytes - Bloom filter for light clients to quickly retrieve related logs.
* `type`: `DATA` - integer of the transaction type, `0x00` for legacy transactions, `0x01` for access list types, `0x02` for dynamic fees. It also returns _either_ :
* `root` : `DATA` 32 bytes of post-transaction stateroot (pre Byzantium)
* `status`: `QUANTITY` either `1` (success) or `0` (failure)

**Example**

```
1// Request2curl -X POST --data '{"jsonrpc":"2.0","method":"eth_getTransactionReceipt","params":["0x85d995eba9763907fdf35cd2034144dd9d53ce32cbec21349d4b12823c6860c5"],"id":1}'3// Result4{5  "jsonrpc": "2.0",6  "id": 1,7  "result": {8    "blockHash":9      "0xa957d47df264a31badc3ae823e10ac1d444b098d9b73d204c40426e57f47e8c3",10    "blockNumber": "0xeff35f",11    "contractAddress": null, // string of the address if it was created12    "cumulativeGasUsed": "0xa12515",13    "effectiveGasPrice": "0x5a9c688d4",14    "from": "0x6221a9c005f6e47eb398fd867784cacfdcfff4e7",15    "gasUsed": "0xb4c8",16    "logs": [{17      // logs as returned by getFilterLogs, etc.18    }],19    "logsBloom": "0x00...0", // 256 byte bloom filter20    "status": "0x1",21    "to": "0xc02aaa39b223fe8d0a0e5c4f27ead9083c756cc2",22    "transactionHash":23      "0x85d995eba9763907fdf35cd2034144dd9d53ce32cbec21349d4b12823c6860c5",24    "transactionIndex": "0x66",25    "type": "0x2"26  }27}28
Show all Copy
```

#### eth\_getUncleByBlockHashAndIndex <a href="#eth_getunclebyblockhashandindex" id="eth_getunclebyblockhashandindex"></a>

Returns information about a uncle of a block by hash and uncle index position.

**Parameters**

1. `DATA`, 32 Bytes - The hash of a block.
2. `QUANTITY` - The uncle's index position.

```
1params: [2  "0xc6ef2fc5426d6ad6fd9e2a26abeab0aa2411b7ab17f30a99d3cb96aed1d1055b",3  "0x0", // 04]5
 Copy
```

**Returns** See [eth\_getBlockByHash](https://ethereum.org/en/developers/docs/apis/json-rpc/#eth\_getblockbyhash)

**Example**

```
1// Request2curl -X POST --data '{"jsonrpc":"2.0","method":"eth_getUncleByBlockHashAndIndex","params":["0xc6ef2fc5426d6ad6fd9e2a26abeab0aa2411b7ab17f30a99d3cb96aed1d1055b", "0x0"],"id":1}'3
 Copy
```

Result see [eth\_getBlockByHash](https://ethereum.org/en/developers/docs/apis/json-rpc/#eth\_getblockbyhash)

**Note**: An uncle doesn't contain individual transactions.

#### eth\_getUncleByBlockNumberAndIndex <a href="#eth_getunclebyblocknumberandindex" id="eth_getunclebyblocknumberandindex"></a>

Returns information about a uncle of a block by number and uncle index position.

**Parameters**

1. `QUANTITY|TAG` - a block number, or the string `"earliest"`, `"latest"` or `"pending"`, as in the [default block parameter](https://ethereum.org/en/developers/docs/apis/json-rpc/#default-block-parameter).
2. `QUANTITY` - the uncle's index position.

```
1params: [2  "0x29c", // 6683  "0x0", // 04]5
 Copy
```

**Returns** See [eth\_getBlockByHash](https://ethereum.org/en/developers/docs/apis/json-rpc/#eth\_getblockbyhash)

**Note**: An uncle doesn't contain individual transactions.

**Example**

```
1// Request2curl -X POST --data '{"jsonrpc":"2.0","method":"eth_getUncleByBlockNumberAndIndex","params":["0x29c", "0x0"],"id":1}'3
 Copy
```

Result see [eth\_getBlockByHash](https://ethereum.org/en/developers/docs/apis/json-rpc/#eth\_getblockbyhash)

#### eth\_getCompilers <a href="#eth_getcompilers" id="eth_getcompilers"></a>

Returns a list of available compilers in the client.

**Parameters** None

**Returns** `Array` - Array of available compilers.

**Example**

```
1// Request2curl -X POST --data '{"jsonrpc":"2.0","method":"eth_getCompilers","params":[],"id":1}'3// Result4{5  "id":1,6  "jsonrpc": "2.0",7  "result": ["solidity", "lll", "serpent"]8}9
 Copy
```

#### eth\_compileSolidity <a href="#eth_compile_solidity" id="eth_compile_solidity"></a>

Returns compiled solidity code.

**Parameters**

1. `String` - The source code.

```
1params: [2  "contract test { function multiply(uint a) returns(uint d) {   return a * 7;   } }",3]4
 Copy
```

**Returns** `DATA` - The compiled source code.

**Example**

```
1// Request2curl -X POST --data '{"jsonrpc":"2.0","method":"eth_compileSolidity","params":["contract test { function multiply(uint a) returns(uint d) {   return a * 7;   } }"],"id":1}'3// Result4{5  "id":1,6  "jsonrpc": "2.0",7  "result": {8      "code": "0x605880600c6000396000f3006000357c010000000000000000000000000000000000000000000000000000000090048063c6888fa114602e57005b603d6004803590602001506047565b8060005260206000f35b60006007820290506053565b91905056",9      "info": {10        "source": "contract test {\n   function multiply(uint a) constant returns(uint d) {\n       return a * 7;\n   }\n}\n",11        "language": "Solidity",12        "languageVersion": "0",13        "compilerVersion": "0.9.19",14        "abiDefinition": [15          {16            "constant": true,17            "inputs": [18              {19                "name": "a",20                "type": "uint256"21              }22            ],23            "name": "multiply",24            "outputs": [25              {26                "name": "d",27                "type": "uint256"28              }29            ],30            "type": "function"31          }32        ],33        "userDoc": {34          "methods": {}35        },36        "developerDoc": {37          "methods": {}38        }39      }40}41
Show all Copy
```

#### eth\_compileLLL <a href="#eth_compilelll" id="eth_compilelll"></a>

Returns compiled LLL code.

**Parameters**

1. `String` - The source code.

```
1params: ["(returnlll (suicide (caller)))"]2
 Copy
```

**Returns** `DATA` - The compiled source code.

**Example**

```
1// Request2curl -X POST --data '{"jsonrpc":"2.0","method":"eth_compileLLL","params":["(returnlll (suicide (caller)))"],"id":1}'3// Result4{5  "id":1,6  "jsonrpc": "2.0",7  "result": "0x603880600c6000396000f3006001600060e060020a600035048063c6888fa114601857005b6021600435602b565b8060005260206000f35b600081600702905091905056" // the compiled source code8}9
 Copy
```

#### eth\_compileSerpent <a href="#eth_compileserpent" id="eth_compileserpent"></a>

Returns compiled serpent code.

**Parameters**

1. `String` - The source code.

```
1params: ["/* some serpent */"]2
 Copy
```

**Returns** `DATA` - The compiled source code.

**Example**

```
1// Request2curl -X POST --data '{"jsonrpc":"2.0","method":"eth_compileSerpent","params":["/* some serpent */"],"id":1}'3// Result4{5  "id":1,6  "jsonrpc": "2.0",7  "result": "0x603880600c6000396000f3006001600060e060020a600035048063c6888fa114601857005b6021600435602b565b8060005260206000f35b600081600702905091905056" // the compiled source code8}9
 Copy
```

#### eth\_newFilter <a href="#eth_newfilter" id="eth_newfilter"></a>

Creates a filter object, based on filter options, to notify when the state changes (logs). To check if the state has changed, call [eth\_getFilterChanges](https://ethereum.org/en/developers/docs/apis/json-rpc/#eth\_getfilterchanges).

**A note on specifying topic filters:** Topics are order-dependent. A transaction with a log with topics \[A, B] will be matched by the following topic filters:

* `[]` "anything"
* `[A]` "A in first position (and anything after)"
* `[null, B]` "anything in first position AND B in second position (and anything after)"
* `[A, B]` "A in first position AND B in second position (and anything after)"
* `[[A, B], [A, B]]` "(A OR B) in first position AND (A OR B) in second position (and anything after)"
* **Parameters**

1. `Object` - The filter options:

* `fromBlock`: `QUANTITY|TAG` - (optional, default: `"latest"`) Integer block number, or `"latest"` for the last mined block or `"pending"`, `"earliest"` for not yet mined transactions.
* `toBlock`: `QUANTITY|TAG` - (optional, default: `"latest"`) Integer block number, or `"latest"` for the last mined block or `"pending"`, `"earliest"` for not yet mined transactions.
* `address`: `DATA|Array`, 20 Bytes - (optional) Contract address or a list of addresses from which logs should originate.
* `topics`: `Array of DATA`, - (optional) Array of 32 Bytes `DATA` topics. Topics are order-dependent. Each topic can also be an array of DATA with "or" options.

```
1params: [2  {3    fromBlock: "0x1",4    toBlock: "0x2",5    address: "0x8888f1f195afa192cfee860698584c030f4c9db1",6    topics: [7      "0x000000000000000000000000a94f5374fce5edbc8e2a8697c15331677e6ebf0b",8      null,9      [10        "0x000000000000000000000000a94f5374fce5edbc8e2a8697c15331677e6ebf0b",11        "0x0000000000000000000000000aff3454fce5edbc8cca8697c15331677e6ebccc",12      ],13    ],14  },15]16
Show all Copy
```

**Returns** `QUANTITY` - A filter id.

**Example**

```
1// Request2curl -X POST --data '{"jsonrpc":"2.0","method":"eth_newFilter","params":[{"topics":["0x12341234"]}],"id":73}'3// Result4{5  "id":1,6  "jsonrpc": "2.0",7  "result": "0x1" // 18}9
 Copy
```

#### eth\_newBlockFilter <a href="#eth_newblockfilter" id="eth_newblockfilter"></a>

Creates a filter in the node, to notify when a new block arrives. To check if the state has changed, call [eth\_getFilterChanges](https://ethereum.org/en/developers/docs/apis/json-rpc/#eth\_getfilterchanges).

**Parameters** None

**Returns** `QUANTITY` - A filter id.

**Example**

```
1// Request2curl -X POST --data '{"jsonrpc":"2.0","method":"eth_newBlockFilter","params":[],"id":73}'3// Result4{5  "id":1,6  "jsonrpc":  "2.0",7  "result": "0x1" // 18}9
 Copy
```

#### eth\_newPendingTransactionFilter <a href="#eth_newpendingtransactionfilter" id="eth_newpendingtransactionfilter"></a>

Creates a filter in the node, to notify when new pending transactions arrive. To check if the state has changed, call [eth\_getFilterChanges](https://ethereum.org/en/developers/docs/apis/json-rpc/#eth\_getfilterchanges).

**Parameters** None

**Returns** `QUANTITY` - A filter id.

**Example**

```
1// Request2curl -X POST --data '{"jsonrpc":"2.0","method":"eth_newPendingTransactionFilter","params":[],"id":73}'3// Result4{5  "id":1,6  "jsonrpc":  "2.0",7  "result": "0x1" // 18}9
 Copy
```

#### eth\_uninstallFilter <a href="#eth_uninstallfilter" id="eth_uninstallfilter"></a>

Uninstalls a filter with given id. Should always be called when watch is no longer needed. Additionally Filters timeout when they aren't requested with [eth\_getFilterChanges](https://ethereum.org/en/developers/docs/apis/json-rpc/#eth\_getfilterchanges) for a period of time.

**Parameters**

1. `QUANTITY` - The filter id.

```
1params: [2  "0xb", // 113]4
 Copy
```

**Returns** `Boolean` - `true` if the filter was successfully uninstalled, otherwise `false`.

**Example**

```
1// Request2curl -X POST --data '{"jsonrpc":"2.0","method":"eth_uninstallFilter","params":["0xb"],"id":73}'3// Result4{5  "id":1,6  "jsonrpc": "2.0",7  "result": true8}9
 Copy
```

#### eth\_getFilterChanges <a href="#eth_getfilterchanges" id="eth_getfilterchanges"></a>

Polling method for a filter, which returns an array of logs which occurred since last poll.

**Parameters**

1. `QUANTITY` - the filter id.

```
1params: [2  "0x16", // 223]4
 Copy
```

**Returns** `Array` - Array of log objects, or an empty array if nothing has changed since last poll.

* For filters created with `eth_newBlockFilter` the return are block hashes (`DATA`, 32 Bytes), e.g. `["0x3454645634534..."]`.
* For filters created with `eth_newPendingTransactionFilter` the return are transaction hashes (`DATA`, 32 Bytes), e.g. `["0x6345343454645..."]`.
* For filters created with `eth_newFilter` logs are objects with following params:
  * `removed`: `TAG` - `true` when the log was removed, due to a chain reorganization. `false` if its a valid log.
  * `logIndex`: `QUANTITY` - integer of the log index position in the block. `null` when its pending log.
  * `transactionIndex`: `QUANTITY` - integer of the transactions index position log was created from. `null` when its pending log.
  * `transactionHash`: `DATA`, 32 Bytes - hash of the transactions this log was created from. `null` when its pending log.
  * `blockHash`: `DATA`, 32 Bytes - hash of the block where this log was in. `null` when its pending. `null` when its pending log.
  * `blockNumber`: `QUANTITY` - the block number where this log was in. `null` when its pending. `null` when its pending log.
  * `address`: `DATA`, 20 Bytes - address from which this log originated.
  * `data`: `DATA` - contains one or more 32 Bytes non-indexed arguments of the log.
  * `topics`: `Array of DATA` - Array of 0 to 4 32 Bytes `DATA` of indexed log arguments. (In _solidity_: The first topic is the _hash_ of the signature of the event (e.g. `Deposit(address,bytes32,uint256)`), except you declared the event with the `anonymous` specifier.)
* **Example**

```
1// Request2curl -X POST --data '{"jsonrpc":"2.0","method":"eth_getFilterChanges","params":["0x16"],"id":73}'3// Result4{5  "id":1,6  "jsonrpc":"2.0",7  "result": [{8    "logIndex": "0x1", // 19    "blockNumber":"0x1b4", // 43610    "blockHash": "0x8216c5785ac562ff41e2dcfdf5785ac562ff41e2dcfdf829c5a142f1fccd7d",11    "transactionHash":  "0xdf829c5a142f1fccd7d8216c5785ac562ff41e2dcfdf5785ac562ff41e2dcf",12    "transactionIndex": "0x0", // 013    "address": "0x16c5785ac562ff41e2dcfdf829c5a142f1fccd7d",14    "data":"0x0000000000000000000000000000000000000000000000000000000000000000",15    "topics": ["0x59ebeb90bc63057b6515673c3ecf9438e5058bca0f92585014eced636878c9a5"]16    },{17      ...18    }]19}20
Show all Copy
```

#### eth\_getFilterLogs <a href="#eth_getfilterlogs" id="eth_getfilterlogs"></a>

Returns an array of all logs matching filter with given id.

**Parameters**

1. `QUANTITY` - The filter id.

```
1params: [2  "0x16", // 223]4
 Copy
```

**Returns** See [eth\_getFilterChanges](https://ethereum.org/en/developers/docs/apis/json-rpc/#eth\_getfilterchanges)

**Example**

```
1// Request2curl -X POST --data '{"jsonrpc":"2.0","method":"eth_getFilterLogs","params":["0x16"],"id":74}'3
 Copy
```

Result see [eth\_getFilterChanges](https://ethereum.org/en/developers/docs/apis/json-rpc/#eth\_getfilterchanges)

#### eth\_getLogs <a href="#eth_getlogs" id="eth_getlogs"></a>

Returns an array of all logs matching a given filter object.

**Parameters**

1. `Object` - The filter options:

* `fromBlock`: `QUANTITY|TAG` - (optional, default: `"latest"`) Integer block number, or `"latest"` for the last mined block or `"pending"`, `"earliest"` for not yet mined transactions.
* `toBlock`: `QUANTITY|TAG` - (optional, default: `"latest"`) Integer block number, or `"latest"` for the last mined block or `"pending"`, `"earliest"` for not yet mined transactions.
* `address`: `DATA|Array`, 20 Bytes - (optional) Contract address or a list of addresses from which logs should originate.
* `topics`: `Array of DATA`, - (optional) Array of 32 Bytes `DATA` topics. Topics are order-dependent. Each topic can also be an array of DATA with "or" options.
* `blockhash`: `DATA`, 32 Bytes - (optional, **future**) With the addition of EIP-234, `blockHash` will be a new filter option which restricts the logs returned to the single block with the 32-byte hash `blockHash`. Using `blockHash` is equivalent to `fromBlock` = `toBlock` = the block number with hash `blockHash`. If `blockHash` is present in the filter criteria, then neither `fromBlock` nor `toBlock` are allowed.

```
1params: [2  {3    topics: [4      "0x000000000000000000000000a94f5374fce5edbc8e2a8697c15331677e6ebf0b",5    ],6  },7]8
 Copy
```

**Returns** See [eth\_getFilterChanges](https://ethereum.org/en/developers/docs/apis/json-rpc/#eth\_getfilterchanges)

**Example**

```
1// Request2curl -X POST --data '{"jsonrpc":"2.0","method":"eth_getLogs","params":[{"topics":["0x000000000000000000000000a94f5374fce5edbc8e2a8697c15331677e6ebf0b"]}],"id":74}'3
 Copy
```

Result see [eth\_getFilterChanges](https://ethereum.org/en/developers/docs/apis/json-rpc/#eth\_getfilterchanges)

#### eth\_getWork <a href="#eth_getwork" id="eth_getwork"></a>

Returns the hash of the current block, the seedHash, and the boundary condition to be met ("target").

**Parameters** None

**Returns** `Array` - Array with the following properties:

1. `DATA`, 32 Bytes - current block header pow-hash
2. `DATA`, 32 Bytes - the seed hash used for the DAG.
3. `DATA`, 32 Bytes - the boundary condition ("target"), 2^256 / difficulty.

**Example**

```
1// Request2curl -X POST --data '{"jsonrpc":"2.0","method":"eth_getWork","params":[],"id":73}'3// Result4{5  "id":1,6  "jsonrpc":"2.0",7  "result": [8      "0x1234567890abcdef1234567890abcdef1234567890abcdef1234567890abcdef",9      "0x5EED00000000000000000000000000005EED0000000000000000000000000000",10      "0xd1ff1c01710000000000000000000000d1ff1c01710000000000000000000000"11    ]12}13
Show all Copy
```

#### eth\_submitWork <a href="#eth_submitwork" id="eth_submitwork"></a>

Used for submitting a proof-of-work solution.

**Parameters**

1. `DATA`, 8 Bytes - The nonce found (64 bits)
2. `DATA`, 32 Bytes - The header's pow-hash (256 bits)
3. `DATA`, 32 Bytes - The mix digest (256 bits)

```
1params: [2  "0x0000000000000001",3  "0x1234567890abcdef1234567890abcdef1234567890abcdef1234567890abcdef",4  "0xD1FE5700000000000000000000000000D1FE5700000000000000000000000000",5]6
 Copy
```

**Returns** `Boolean` - returns `true` if the provided solution is valid, otherwise `false`.

**Example**

```
1// Request2curl -X POST --data '{"jsonrpc":"2.0", "method":"eth_submitWork", "params":["0x0000000000000001", "0x1234567890abcdef1234567890abcdef1234567890abcdef1234567890abcdef", "0xD1GE5700000000000000000000000000D1GE5700000000000000000000000000"],"id":73}'3// Result4{5  "id":73,6  "jsonrpc":"2.0",7  "result": true8}9
 Copy
```

#### eth\_submitHashrate <a href="#eth_submithashrate" id="eth_submithashrate"></a>

Used for submitting mining hashrate.

**Parameters**

1. `Hashrate`, a hexadecimal string representation (32 bytes) of the hashrate
2. `ID`, String - A random hexadecimal(32 bytes) ID identifying the client

```
1params: [2  "0x0000000000000000000000000000000000000000000000000000000000500000",3  "0x59daa26581d0acd1fce254fb7e85952f4c09d0915afd33d3886cd914bc7d283c",4]5
 Copy
```

**Returns** `Boolean` - returns `true` if submitting went through successfully and `false` otherwise.

**Example**

```
1// Request2curl -X POST --data '{"jsonrpc":"2.0", "method":"eth_submitHashrate", "params":["0x0000000000000000000000000000000000000000000000000000000000500000", "0x59daa26581d0acd1fce254fb7e85952f4c09d0915afd33d3886cd914bc7d283c"],"id":73}'3// Result4{5  "id":73,6  "jsonrpc":"2.0",7  "result": true8}9
 Copy
```

#### db\_putString (deprecated) <a href="#db_putstring" id="db_putstring"></a>

Stores a string in the local database.

**Note** this function is deprecated.

**Parameters**

1. `String` - Database name.
2. `String` - Key name.
3. `String` - String to store.

```
1params: ["testDB", "myKey", "myString"]2
 Copy
```

**Returns** `Boolean` - returns `true` if the value was stored, otherwise `false`.

**Example**

```
1// Request2curl -X POST --data '{"jsonrpc":"2.0","method":"db_putString","params":["testDB","myKey","myString"],"id":73}'3// Result4{5  "id":1,6  "jsonrpc":"2.0",7  "result": true8}9
 Copy
```

#### db\_getString (deprecated) <a href="#db_getstring" id="db_getstring"></a>

Returns string from the local database. **Note** this function is deprecated.

**Parameters**

1. `String` - Database name.
2. `String` - Key name.

```
1params: ["testDB", "myKey"]2
 Copy
```

**Returns** `String` - The previously stored string.

**Example**

```
1// Request2curl -X POST --data '{"jsonrpc":"2.0","method":"db_getString","params":["testDB","myKey"],"id":73}'3// Result4{5  "id":1,6  "jsonrpc":"2.0",7  "result": "myString"8}9
 Copy
```

#### db\_putHex (deprecated) <a href="#db_puthex" id="db_puthex"></a>

Stores binary data in the local database. **Note** this function is deprecated.

**Parameters**

1. `String` - Database name.
2. `String` - Key name.
3. `DATA` - The data to store.

```
1params: ["testDB", "myKey", "0x68656c6c6f20776f726c64"]2
 Copy
```

**Returns** `Boolean` - returns `true` if the value was stored, otherwise `false`.

**Example**

```
1// Request2curl -X POST --data '{"jsonrpc":"2.0","method":"db_putHex","params":["testDB","myKey","0x68656c6c6f20776f726c64"],"id":73}'3// Result4{5  "id":1,6  "jsonrpc":"2.0",7  "result": true8}9
 Copy
```

#### db\_getHex (deprecated) <a href="#db_gethex" id="db_gethex"></a>

Returns binary data from the local database. **Note** this function is deprecated.

**Parameters**

1. `String` - Database name.
2. `String` - Key name.

```
1params: ["testDB", "myKey"]2
 Copy
```

**Returns** `DATA` - The previously stored data.

**Example**

```
1// Request2curl -X POST --data '{"jsonrpc":"2.0","method":"db_getHex","params":["testDB","myKey"],"id":73}'3// Result4{5  "id":1,6  "jsonrpc":"2.0",7  "result": "0x68656c6c6f20776f726c64"8}9
 Copy
```

#### shh\_version (deprecated) <a href="#shh_post" id="shh_post"></a>

Returns the current whisper protocol version.

**Note** this function is deprecated.

**Parameters** None

**Returns** `String` - The current whisper protocol version

**Example**

```
1// Request2curl -X POST --data '{"jsonrpc":"2.0","method":"shh_version","params":[],"id":67}'3// Result4{5  "id":67,6  "jsonrpc": "2.0",7  "result": "2"8}9
 Copy
```

#### shh\_post (deprecated) <a href="#shh_version" id="shh_version"></a>

Sends a whisper message.

**Note** this function is deprecated.

**Parameters**

1. `Object` - The whisper post object:

* `from`: `DATA`, 60 Bytes - (optional) The identity of the sender.
* `to`: `DATA`, 60 Bytes - (optional) The identity of the receiver. When present whisper will encrypt the message so that only the receiver can decrypt it.
* `topics`: `Array of DATA` - Array of `DATA` topics, for the receiver to identify messages.
* `payload`: `DATA` - The payload of the message.
* `priority`: `QUANTITY` - The integer of the priority in a rang from ... (?).
* `ttl`: `QUANTITY` - integer of the time to live in seconds.

```
1params: [2  {3    from: "0x04f96a5e25610293e42a73908e93ccc8c4d4dc0edcfa9fa872f50cb214e08ebf61a03e245533f97284d442460f2998cd41858798ddfd4d661997d3940272b717b1",4    to: "0x3e245533f97284d442460f2998cd41858798ddf04f96a5e25610293e42a73908e93ccc8c4d4dc0edcfa9fa872f50cb214e08ebf61a0d4d661997d3940272b717b1",5    topics: [6      "0x776869737065722d636861742d636c69656e74",7      "0x4d5a695276454c39425154466b61693532",8    ],9    payload: "0x7b2274797065223a226d6",10    priority: "0x64",11    ttl: "0x64",12  },13]14
Show all Copy
```

**Returns** `Boolean` - returns `true` if the message was send, otherwise `false`.

**Example**

```
1// Request2curl -X POST --data '{"jsonrpc":"2.0","method":"shh_post","params":[{"from":"0xc931d93e97ab07fe42d923478ba2465f2..","topics": ["0x68656c6c6f20776f726c64"],"payload":"0x68656c6c6f20776f726c64","ttl":0x64,"priority":0x64}],"id":73}'3// Result4{5  "id":1,6  "jsonrpc":"2.0",7  "result": true8}9
 Copy
```

#### shh\_newIdentity (deprecated) <a href="#shh_newidentity" id="shh_newidentity"></a>

Creates new whisper identity in the client.

**Note** this function is deprecated.

**Parameters** None

**Returns** `DATA`, 60 Bytes - the address of the new identity.

**Example**

```
1// Request2curl -X POST --data '{"jsonrpc":"2.0","method":"shh_newIdentity","params":[],"id":73}'3// Result4{5  "id":1,6  "jsonrpc": "2.0",7  "result": "0xc931d93e97ab07fe42d923478ba2465f283f440fd6cabea4dd7a2c807108f651b7135d1d6ca9007d5b68aa497e4619ac10aa3b27726e1863c1fd9b570d99bbaf"8}9
 Copy
```

#### shh\_hasIdentity (deprecated) <a href="#shh_hasidentity" id="shh_hasidentity"></a>

Checks if the client hold the private keys for a given identity.

**Note** this function is deprecated.

**Parameters**

1. `DATA`, 60 Bytes - The identity address to check.

```
1params: [2  "0x04f96a5e25610293e42a73908e93ccc8c4d4dc0edcfa9fa872f50cb214e08ebf61a03e245533f97284d442460f2998cd41858798ddfd4d661997d3940272b717b1",3]4
 Copy
```

**Returns** `Boolean` - returns `true` if the client holds the privatekey for that identity, otherwise `false`.

**Example**

```
1// Request2curl -X POST --data '{"jsonrpc":"2.0","method":"shh_hasIdentity","params":["0x04f96a5e25610293e42a73908e93ccc8c4d4dc0edcfa9fa872f50cb214e08ebf61a03e245533f97284d442460f2998cd41858798ddfd4d661997d3940272b717b1"],"id":73}'3// Result4{5  "id":1,6  "jsonrpc": "2.0",7  "result": true8}9
 Copy
```

#### shh\_newGroup (deprecated) <a href="#shh_newgroup" id="shh_newgroup"></a>

**Note** this function is deprecated.

**Parameters** None

**Returns** `DATA`, 60 Bytes - the address of the new group. (?)

**Example**

```
1// Request2curl -X POST --data '{"jsonrpc":"2.0","method":"shh_newGroup","params":[],"id":73}'3// Result4{5  "id":1,6  "jsonrpc": "2.0",7  "result": "0xc65f283f440fd6cabea4dd7a2c807108f651b7135d1d6ca90931d93e97ab07fe42d923478ba2407d5b68aa497e4619ac10aa3b27726e1863c1fd9b570d99bbaf"8}9
 Copy
```

#### shh\_addToGroup (deprecated) <a href="#shh_addtogroup" id="shh_addtogroup"></a>

**Note** this function is deprecated.

**Parameters**

1. `DATA`, 60 Bytes - The identity address to add to a group (?).

```
1params: [2  "0x04f96a5e25610293e42a73908e93ccc8c4d4dc0edcfa9fa872f50cb214e08ebf61a03e245533f97284d442460f2998cd41858798ddfd4d661997d3940272b717b1",3]4
 Copy
```

**Returns** `Boolean` - returns `true` if the identity was successfully added to the group, otherwise `false` (?).

**Example**

```
1// Request2curl -X POST --data '{"jsonrpc":"2.0","method":"shh_addToGroup","params":["0x04f96a5e25610293e42a73908e93ccc8c4d4dc0edcfa9fa872f50cb214e08ebf61a03e245533f97284d442460f2998cd41858798ddfd4d661997d3940272b717b1"],"id":73}'3// Result4{5  "id":1,6  "jsonrpc": "2.0",7  "result": true8}9
 Copy
```

#### shh\_newFilter (deprecated) <a href="#shh_newfilter" id="shh_newfilter"></a>

Creates filter to notify, when client receives whisper message matching the filter options. **Note** this function is deprecated.

**Parameters**

1. `Object` - The filter options:

* `to`: `DATA`, 60 Bytes - (optional) Identity of the receiver. _When present it will try to decrypt any incoming message if the client holds the private key to this identity._
* `topics`: `Array of DATA` - Array of `DATA` topics which the incoming message's topics should match. You can use the following combinations:
  * `[A, B] = A && B`
  * `[A, [B, C]] = A && (B || C)`
  * `[null, A, B] = ANYTHING && A && B` `null` works as a wildcard
  *

```
1params: [2  {3    topics: ["0x12341234bf4b564f"],4    to: "0x04f96a5e25610293e42a73908e93ccc8c4d4dc0edcfa9fa872f50cb214e08ebf61a03e245533f97284d442460f2998cd41858798ddfd4d661997d3940272b717b1",5  },6]7
 Copy
```

**Returns** `QUANTITY` - The newly created filter.

**Example**

```
1// Request2curl -X POST --data '{"jsonrpc":"2.0","method":"shh_newFilter","params":[{"topics": ['0x12341234bf4b564f'],"to": "0x2341234bf4b2341234bf4b564f..."}],"id":73}'3// Result4{5  "id":1,6  "jsonrpc":"2.0",7  "result": "0x7" // 78}9
 Copy
```

#### shh\_uninstallFilter (deprecated) <a href="#shh_uninstallfilter" id="shh_uninstallfilter"></a>

Uninstalls a filter with given id. Should always be called when watch is no longer needed. Additionally Filters timeout when they aren't requested with [shh\_getFilterChanges](https://ethereum.org/en/developers/docs/apis/json-rpc/#shh\_getfilterchanges) for a period of time. **Note** this function is deprecated.

**Parameters**

1. `QUANTITY` - The filter id.

```
1params: [2  "0x7", // 73]4
 Copy
```

**Returns** `Boolean` - `true` if the filter was successfully uninstalled, otherwise `false`.

**Example**

```
1// Request2curl -X POST --data '{"jsonrpc":"2.0","method":"shh_uninstallFilter","params":["0x7"],"id":73}'3// Result4{5  "id":1,6  "jsonrpc":"2.0",7  "result": true8}9
 Copy
```

#### shh\_getFilterChanges (deprecated) <a href="#shh_getfilterchanges" id="shh_getfilterchanges"></a>

Polling method for whisper filters. Returns new messages since the last call of this method. **Note** calling the [shh\_getMessages](https://ethereum.org/en/developers/docs/apis/json-rpc/#shh\_getmessages) method, will reset the buffer for this method, so that you won't receive duplicate messages. **Note** this function is deprecated.

**Parameters**

1. `QUANTITY` - The filter id.

```
1params: [2  "0x7", // 73]4
 Copy
```

**Returns** `Array` - Array of messages received since last poll:

* `hash`: `DATA`, 32 Bytes (?) - The hash of the message.
* `from`: `DATA`, 60 Bytes - The sender of the message, if a sender was specified.
* `to`: `DATA`, 60 Bytes - The receiver of the message, if a receiver was specified.
* `expiry`: `QUANTITY` - Integer of the time in seconds when this message should expire (?).
* `ttl`: `QUANTITY` - Integer of the time the message should float in the system in seconds (?).
* `sent`: `QUANTITY` - Integer of the unix timestamp when the message was sent.
* `topics`: `Array of DATA` - Array of `DATA` topics the message contained.
* `payload`: `DATA` - The payload of the message.
* `workProved`: `QUANTITY` - Integer of the work this message required before it was send (?).

**Example**

```
1// Request2curl -X POST --data '{"jsonrpc":"2.0","method":"shh_getFilterChanges","params":["0x7"],"id":73}'3// Result4{5  "id":1,6  "jsonrpc":"2.0",7  "result": [{8    "hash": "0x33eb2da77bf3527e28f8bf493650b1879b08c4f2a362beae4ba2f71bafcd91f9",9    "from": "0x3ec052fc33..",10    "to": "0x87gdf76g8d7fgdfg...",11    "expiry": "0x54caa50a", // 142256666612    "sent": "0x54ca9ea2", // 142256502613    "ttl": "0x64", // 10014    "topics": ["0x6578616d"],15    "payload": "0x7b2274797065223a226d657373616765222c2263686...",16    "workProved": "0x0"17    }]18}19
Show all Copy
```

#### shh\_getMessages (deprecated) <a href="#shh_getmessages" id="shh_getmessages"></a>

Get all messages matching a filter. Unlike `shh_getFilterChanges` this returns all messages.

**Note** this function is deprecated.

**Parameters**

1. `QUANTITY` - The filter id.

```
1params: [2  "0x7", // 73]4
 Copy
```

**Returns** See [shh\_getFilterChanges](https://ethereum.org/en/developers/docs/apis/json-rpc/#shh\_getfilterchanges)

**Example**

```
1// Request2curl -X POST --data '{"jsonrpc":"2.0","method":"shh_getMessages","params":["0x7"3],"id":73}'4
 Copy
```

Result see [shh\_getFilterChanges](https://ethereum.org/en/developers/docs/apis/json-rpc/#shh\_getfilterchanges)

### USAGE EXAMPLE <a href="#usage-example" id="usage-example"></a>

#### Deploying a contract using JSON\_RPC <a href="#deploying-contract" id="deploying-contract"></a>

This section includes a demonstration of how to deploy a contract using only the RPC interface. There are alternative routes to deploying contracts where this complexity is abstracted away—for example, using libraries built on top of the RPC interface such as [web3.js](https://web3js.readthedocs.io/) and [web3.py](https://github.com/ethereum/web3.py). These abstractions are generally easier to understand and less error-prone, but it is still helpful to understand what is happening under the hood.

The following is a straightforward smart contract called `Multiply7` that will be deployed using the JSON-RPC interface to an Ethereum node. This tutorial assumes the reader is already running a Geth node. More information on nodes and clients is available [here](https://ethereum.org/en/developers/docs/nodes-and-clients/run-a-node/). Please refer to individual [client](https://ethereum.org/en/developers/docs/nodes-and-clients/) documentation to see how to start the HTTP JSON-RPC for non-Geth clients. Most clients default to serving on `localhost:8545`.

```
1contract Multiply7 {2    event Print(uint);3    function multiply(uint input) returns (uint) {4        Print(input * 7);5        return input * 7;6    }7}8
```

The first thing to do is make sure the HTTP RPC interface is enabled. This means we supply Geth with the `--http` flag on startup. In this example we use the Geth node on a private development chain. Using this approach we don't need ether on the real network.

```
geth --http --dev console 2>>geth.log
```

This will start the HTTP RPC interface on `http://localhost:8545`.

We can verify that the interface is running by retrieving the Coinbase address and balance using [curl](https://curl.se/). Please note that data in these examples will differ on your local node. If you want to try these commands, replace the request params in the second curl request with the result returned from the first.

```
curl --data '{"jsonrpc":"2.0","method":"eth_coinbase", "id":1}' -H "Content-Type: application/json" localhost:8545{"id":1,"jsonrpc":"2.0","result":["0x9b1d35635cc34752ca54713bb99d38614f63c955"]}
curl --data '{"jsonrpc":"2.0","method":"eth_getBalance", "params": ["0x9b1d35635cc34752ca54713bb99d38614f63c955", "latest"], "id":2}' -H "Content-Type: application/json" localhost:8545{"id":2,"jsonrpc":"2.0","result":"0x1639e49bba16280000"}
```

Because numbers are hex encoded, the balance is returned in wei as a hex string. If we want to have the balance in ether as a number we can use web3 from the Geth console.

```
1web3.fromWei("0x1639e49bba16280000", "ether")2// "410"3
```

Now that there is some ether on our private development chain, we can deploy the contract. The first step is to compile the Multiply7 contract to byte code that can be sent to the EVM. To install solc, the Solidity compiler, follow the [Solidity documentation](https://docs.soliditylang.org/en/latest/installing-solidity.html). (You might want to use an older `solc` release to match [the version of compiler used for our example](https://github.com/ethereum/solidity/releases/tag/v0.4.20).)

The next step is to compile the Multiply7 contract to byte code that can be send to the EVM.

```
echo 'pragma solidity ^0.4.16; contract Multiply7 { event Print(uint); function multiply(uint input) public returns (uint) { Print(input * 7); return input * 7; } }' | solc --bin
======= <stdin>:Multiply7 =======Binary:6060604052341561000f57600080fd5b60eb8061001d6000396000f300606060405260043610603f576000357c0100000000000000000000000000000000000000000000000000000000900463ffffffff168063c6888fa1146044575b600080fd5b3415604e57600080fd5b606260048080359060200190919050506078565b6040518082815260200191505060405180910390f35b60007f24abdb5865df5079dcc5ac590ff6f01d5c16edbc5fab4e195d9febd1114503da600783026040518082815260200191505060405180910390a16007820290509190505600a165627a7a7230582040383f19d9f65246752244189b02f56e8d0980ed44e7a56c0b200458caad20bb0029
```

Now that we have the compiled code we need to determine how much gas it costs to deploy it. The RPC interface has an `eth_estimateGas` method that will give us an estimate.

```
curl --data '{"jsonrpc":"2.0","method": "eth_estimateGas", "params": [{"from": "0x9b1d35635cc34752ca54713bb99d38614f63c955", "data": "0x6060604052341561000f57600080fd5b60eb8061001d6000396000f300606060405260043610603f576000357c0100000000000000000000000000000000000000000000000000000000900463ffffffff168063c6888fa1146044575b600080fd5b3415604e57600080fd5b606260048080359060200190919050506078565b6040518082815260200191505060405180910390f35b60007f24abdb5865df5079dcc5ac590ff6f01d5c16edbc5fab4e195d9febd1114503da600783026040518082815260200191505060405180910390a16007820290509190505600a165627a7a7230582040383f19d9f65246752244189b02f56e8d0980ed44e7a56c0b200458caad20bb0029"}], "id": 5}' -H "Content-Type: application/json" localhost:8545{"jsonrpc":"2.0","id":5,"result":"0x1c31e"}
```

And finally deploy the contract.

```
curl --data '{"jsonrpc":"2.0","method": "eth_sendTransaction", "params": [{"from": "0x9b1d35635cc34752ca54713bb99d38614f63c955", "gas": "0x1c31e", "data": "0x6060604052341561000f57600080fd5b60eb8061001d6000396000f300606060405260043610603f576000357c0100000000000000000000000000000000000000000000000000000000900463ffffffff168063c6888fa1146044575b600080fd5b3415604e57600080fd5b606260048080359060200190919050506078565b6040518082815260200191505060405180910390f35b60007f24abdb5865df5079dcc5ac590ff6f01d5c16edbc5fab4e195d9febd1114503da600783026040518082815260200191505060405180910390a16007820290509190505600a165627a7a7230582040383f19d9f65246752244189b02f56e8d0980ed44e7a56c0b200458caad20bb0029"}], "id": 6}' -H "Content-Type: application/json" localhost:8545{"id":6,"jsonrpc":"2.0","result":"0xe1f3095770633ab2b18081658bad475439f6a08c902d0915903bafff06e6febf"}
```

The transaction is accepted by the node and a transaction hash is returned. This hash can be used to track the transaction. The next step is to determine the address where our contract is deployed. Each executed transaction will create a receipt. This receipt contains various information about the transaction such as in which block the transaction was included and how much gas was used by the EVM. If a transaction creates a contract it will also contain the contract address. We can retrieve the receipt with the `eth_getTransactionReceipt` RPC method.

```
curl --data '{"jsonrpc":"2.0","method": "eth_getTransactionReceipt", "params": ["0xe1f3095770633ab2b18081658bad475439f6a08c902d0915903bafff06e6febf"], "id": 7}' -H "Content-Type: application/json" localhost:8545{"jsonrpc":"2.0","id":7,"result":{"blockHash":"0x77b1a4f6872b9066312de3744f60020cbd8102af68b1f6512a05b7619d527a4f","blockNumber":"0x1","contractAddress":"0x4d03d617d700cf81935d7f797f4e2ae719648262","cumulativeGasUsed":"0x1c31e","from":"0x9b1d35635cc34752ca54713bb99d38614f63c955","gasUsed":"0x1c31e","logs":[],"logsBloom":"0x00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000","status":"0x1","to":null,"transactionHash":"0xe1f3095770633ab2b18081658bad475439f6a08c902d0915903bafff06e6febf","transactionIndex":"0x0"}}
```

Our contract was created on `0x4d03d617d700cf81935d7f797f4e2ae719648262`. A null result instead of a receipt means the transaction has not been included in a block yet. Wait for a moment and check if your miner is running and retry it.

**Interacting with smart contracts**

In this example we will be sending a transaction using `eth_sendTransaction` to the `multiply` method of the contract.

`eth_sendTransaction` requires several arguments, specifically `from`, `to` and `data`. `From` is the public address of our account, and `to` is the contract address. The `data` argument contains a payload that defines which method must be called and with which arguments. This is where the [ABI (application binary interface)](https://docs.soliditylang.org/en/latest/abi-spec.html) comes into play. The ABI is a JSON file that defines how to define and encode data for the EVM.

The bytes of the payload defines which method in the contract is called. This is the first 4 bytes from the Keccak hash over the function name and its argument types, hex encoded. The multiply function accepts an uint which is an alias for uint256. This leaves us with:

```
1web3.sha3("multiply(uint256)").substring(0, 10)2// "0xc6888fa1"3
```

The next step is to encode the arguments. There is only one uint256, say, the value 6. The ABI has a section which specifies how to encode uint256 types.

`int<M>: enc(X)` is the big-endian two’s complement encoding of X, padded on the higher-order (left) side with 0xff for negative X and with zero > bytes for positive X such that the length is a multiple of 32 bytes.

This encodes to `0000000000000000000000000000000000000000000000000000000000000006`.

Combining the function selector and the encoded argument our data will be `0xc6888fa10000000000000000000000000000000000000000000000000000000000000006`.

This can now be sent to the node:

```
curl --data '{"jsonrpc":"2.0","method": "eth_sendTransaction", "params": [{"from": "0xeb85a5557e5bdc18ee1934a89d8bb402398ee26a", "to": "0x6ff93b4b46b41c0c3c9baee01c255d3b4675963d", "data": "0xc6888fa10000000000000000000000000000000000000000000000000000000000000006"}], "id": 8}' -H "Content-Type: application/json" localhost:8545{"id":8,"jsonrpc":"2.0","result":"0x759cf065cbc22e9d779748dc53763854e5376eea07409e590c990eafc0869d74"}
```

Since a transaction was sent, a transaction hash was returned. Retrieving the receipt gives:

```
1{2   blockHash: "0xbf0a347307b8c63dd8c1d3d7cbdc0b463e6e7c9bf0a35be40393588242f01d55",3   blockNumber: 268,4   contractAddress: null,5   cumulativeGasUsed: 22631,6   gasUsed: 22631,7   logs: [{8      address: "0x6ff93b4b46b41c0c3c9baee01c255d3b4675963d",9      blockHash: "0xbf0a347307b8c63dd8c1d3d7cbdc0b463e6e7c9bf0a35be40393588242f01d55",10      blockNumber: 268,11      data: "0x000000000000000000000000000000000000000000000000000000000000002a",12      logIndex: 0,13      topics: ["0x24abdb5865df5079dcc5ac590ff6f01d5c16edbc5fab4e195d9febd1114503da"],14      transactionHash: "0x759cf065cbc22e9d779748dc53763854e5376eea07409e590c990eafc0869d74",15      transactionIndex: 016  }],17  transactionHash: "0x759cf065cbc22e9d779748dc53763854e5376eea07409e590c990eafc0869d74",18  transactionIndex: 019}20
Show all
```

The receipt contains a log. This log was generated by the EVM on transaction execution and included in the receipt. The `multiply` function shows that the `Print` event was raised with the input times 7. Since the argument for the `Print` event was a uint256 we can decode it according to the ABI rules which will leave us with the expected decimal 42. Apart from the data it is worth noting that topics can be used to determine which event created the log:

```
1web3.sha3("Print(uint256)")2// "24abdb5865df5079dcc5ac590ff6f01d5c16edbc5fab4e195d9febd1114503da"3
```

This was just a brief introduction into some of the most common tasks, demonstrating direct usage of the JSON-RPC.

\
