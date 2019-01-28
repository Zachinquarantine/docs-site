# How to Access Binance Chain

[Get Started](get-started.md) pages already talk about access Binance Chain and DEX via 
Wallet and Explorers. Here we would like to dive into some technology details for access 
in a programming way.

There are 3 ways to read and write data from Binance chain:

## Web API
The `Accelerated Node` infrastructure provide easy access via http REST API and WebSocket 
push APIs. There are mulitple endpoints from different validator infrastructures. Please 
check the [Web API Reference](api-reference/dex-api.md)

## Node, and Node RPC
There are public accessible node peers that joins the Binance Chain network. They usually 
provide RPC calls. Please check the [Node RPC Reference](api-reference/node-rpc.md).

You can also run a [full node](fullnode.md) by yourself, so that you would have a local server 
to send RPC requests and read Chain information off.

## Command Line Interface
Essentially command line interfaces are just tools that wrap the incoming command line arguments and call RPCs. Please check the [Command Line Referenace](api-reference/cli.md).


## Write APIs
You can only write to Binance Chain via `Transactions`. Both Web API and Node RPC provide 
a `broadcastTx` API to submit a `signed and encoded` transaction onto the Binance Chain. The detailed process would be like the below:

### Message Composition
The transaction message and related information would be packed into a `payload`, which is the so called [`Standard Transaction`](encoding.md#standard-transaction-to-use-and-encode-for-binance_chain). 

The transaction body, memo, signature, etc. fill in the `Standard Transaction and encoded and broadcast out together onto Binance Chain.

### Transaction Encoding 
Encoding defines the way how transactions are serialized and transferred between clients and nodes, 
and different nodes themselves. [here](encoding.md) has a detailed specification on the transaction 
types and encoding logic.

### Signature
Signature is the evidence to prove the sender owns the transaction. It would be performed in the below actions:

1. Compose a data structure. please note `msgs`, `memo`, `source`, `data` are the same as in the above `payload`.

    - `chain_id`: a string, unique ID for the Chain, it stays the same for most time, but may vary as Binance Chain evolves;
    - `account_number`: a string for a 64-bit integer, an identifier number associated with the signing address
    - `sequence`: a string for a a 64-bit integer, please check [the below](#account_and_sequence_number)
    - `memo`: a string, a short sentence of remark for the transaction
    - `msgs`: a byte array, **json encoded** transaction messages, please check the [encoding](encoding.md) section.
    - `source`: a string for a 64 bits integer, which is an identifier for transaction incoming tools
    - `data`: byte array, reserved for future use


2. Encode the above data structure in json, with ordered key,  Specifically:

    - Maps have their keys sorted lexicographically
    - Structs keys are marshalled in the order defined in the struct


3. Sign SHA256 of the encoded byte array, to create an ECDSA signature on curve Secp256k1 and serialize the `R` and `S` result into a 64-byte array. (both `R` and `S` are encoded into 32-byte big endian integers, and then `R` is put into the first 32 bytes and `S` are put into the last 32 bytes of the byte array. In order to break `S` 's malleability, `S` set to `curve.Order() - S` if `S > curnve.Order()/2`.)

The `signature` would be encoded together with transaction message and sent as `payload` to Binance Chain node via RPC or http REST API, as described in the above section.

## Account and Sequence Number

After `Account` is [created](transfer.md#account_and_balance), besides the balances, `Account` also contains:

- Account Number: an internal identifier for the account
- Sequence Number: an ever-changing integer.

The Sequence Number is the way how Binance Chain prevents `Replay Attack` (the idea is borrowed from Cosmos 
network, but varies a bit in handling). Every transaction should have a new `Sequence Number` increased by 
1 from the current latest sequence number of the `Account`, and after this transaction is recorded on the 
block chain, the `Sequence Number` would be set to the same as the one of latest transaction.

This logic forces the client has to be aware of the current `Sequence Number`, either by reading from the
blockchain via API, or keeping counting locally by themselves. The encouraged way would be to keep 
counting locally and re-synchronized from the blockchain periodically.

## Examples

[SDK](api-reference/sdk.md) in different languages act as examples to use APIs to access Binance Chain.