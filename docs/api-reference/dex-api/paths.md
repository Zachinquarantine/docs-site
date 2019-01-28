HTTP API
========
The Binance Chain HTTP API provides access to a Binance Chain node deployment and market data services.

**Version:** 1.0.0

**Contact information:**  
Binance Support  
https://support.binance.org  
support@binance.org  

**License:** [Apache 2.0](http://www.apache.org/licenses/LICENSE-2.0.html)

### /api/v1/time
---
##### ***GET***
**Summary:** Get the block time.

**Description:** Gets the latest block time and the current time according to the HTTP service.

**Destination:** Validator node.

**Rate Limit:** 1 request per IP per second.

**Test URL:** [https://testnet-dex.binance.org/api/v1/time](https://testnet-dex.binance.org/api/v1/time)


**Responses**

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Success | [Times](#times) |
| 400 | Bad Request | [Error](#error) |
| 404 | Not Found |  |
| default | Generic error response | [Error](#error) |

### /api/v1/node-info
---
##### ***GET***
**Summary:** Get node information.

**Description:** Gets runtime information about the node.

**Destination:** Validator node.

**Rate Limit:** 1 request per IP per second.

**Test URL:** [https://testnet-dex.binance.org/api/v1/node-info](https://testnet-dex.binance.org/api/v1/node-info)


**Responses**

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Success | object |

### /api/v1/validators
---
##### ***GET***
**Summary:** Get validators.

**Description:** Gets the list of validators used in consensus.

**Destination:** Witness node.

**Rate Limit:** 10 requests per IP per second.

**Test URL:** [https://testnet-dex.binance.org/api/v1/validators](https://testnet-dex.binance.org/api/v1/validators)


**Responses**

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Success | [Validators](#validators) |
| 400 | Bad Request | [Error](#error) |
| 404 | Not Found |  |
| default | Generic error response | [Error](#error) |

### /api/v1/peers
---
##### ***GET***
**Summary:** Get network peers.

**Description:** Gets the list of network peers.

**Destination:** Witness node.

**Rate Limit:** 1 request per IP per second.

**Test URL:** [https://testnet-dex.binance.org/api/v1/peers](https://testnet-dex.binance.org/api/v1/peers)


**Responses**

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Success | [Peers](#peers) |
| 400 | Bad Request | [Error](#error) |
| 404 | Not Found |  |
| default | Generic error response | [Error](#error) |

### /api/v1/account/{address}
---
##### ***GET***
**Summary:** Get an account.

**Description:** Gets account metadata for an address.

**Destination:** Witness node.

**Rate Limit:** 5 requests per IP per second.

**Test URL:** [https://testnet-dex.binance.org/api/v1/account/bnc18hy3dz0lfky74shaatswmuhd2dxyl847fwsvkk](https://testnet-dex.binance.org/api/v1/account/bnc18hy3dz0lfky74shaatswmuhd2dxyl847fwsvkk)


**Parameters**

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| address | path | The account address to query | Yes | string |

**Responses**

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Success | [Account](#account) |
| 400 | Bad Request | [Error](#error) |
| 404 | Not Found |  |
| default | Generic error response | [Error](#error) |

### /api/v1/account/{address}/sequence
---
##### ***GET***
**Summary:** Get an account sequence.

**Description:** Gets an account sequence for an address.

**Destination:** Validator node.

**Rate Limit:** 5 requests per IP per second.

**Test URL:** [https://testnet-dex.binance.org/api/v1/account/bnc18hy3dz0lfky74shaatswmuhd2dxyl847fwsvkk/sequence](https://testnet-dex.binance.org/api/v1/account/bnc18hy3dz0lfky74shaatswmuhd2dxyl847fwsvkk/sequence)


**Parameters**

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| address | path | The account address to query | Yes | string |

**Responses**

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Success | [AccountSequence](#accountsequence) |
| 400 | Bad Request | [Error](#error) |
| 404 | Not Found |  |
| default | Generic error response | [Error](#error) |

### /api/v1/tx/{hash}
---
##### ***GET***
**Summary:** Get a transaction.

**Description:** Gets transaction metadata by transaction ID.

**Destination:** Seed node.

**Rate Limit:** 10 requests per IP per second.


**Parameters**

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| hash | path | The transaction hash to query | Yes | string |

**Responses**

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Success | [Transaction](#transaction) |
| 400 | Bad Request | [Error](#error) |
| 404 | Not Found |  |
| default | Generic error response | [Error](#error) |

### /api/v1/tokens
---
##### ***GET***
**Summary:** Get tokens list.

**Description:** Gets a list of tokens that have been issued.

**Destination:** Witness node.

**Rate Limit:** 1 request per IP per second.

**Test URL:** [https://testnet-dex.binance.org/api/v1/tokens](https://testnet-dex.binance.org/api/v1/tokens)


**Responses**

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Success | [Tokens](#tokens) |
| 400 | Bad Request | [Error](#error) |
| 404 | Not Found |  |
| default | Generic error response | [Error](#error) |

### /api/v1/markets
---
##### ***GET***
**Summary:** Get market pairs.

**Description:** Gets the list of market pairs that have been listed.

**Destination:** Witness node.

**Rate Limit:** 1 request per IP per second.

**Test URL:** [https://testnet-dex.binance.org/api/v1/markets](https://testnet-dex.binance.org/api/v1/markets)


**Responses**

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Success | [Markets](#markets) |
| 400 | Bad Request | [Error](#error) |
| 404 | Not Found |  |
| default | Generic error response | [Error](#error) |

### /api/v1/depth
---
##### ***GET***
**Summary:** Get the order book.

**Description:** Gets the order book depth data for a given pair symbol.

The given _limit_ must be one of the allowed limits below.

**Destination:** Validator node.

**Rate Limit:** 10 requests per IP per second.

**Test URL:** [https://testnet-dex.binance.org/api/v1/depth](https://testnet-dex.binance.org/api/v1/depth)


**Parameters**

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| symbol | query | Market pair symbol, e.g. NNB-0AD_BNB | Yes | string |
| limit | query | The limit of results. Allowed limits: [5, 10, 20, 50, 100, 500, 1000] | No | integer |

**Responses**

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Success | [MarketDepth](#marketdepth) |
| 400 | Bad Request | [Error](#error) |
| 404 | Not Found |  |
| default | Generic error response | [Error](#error) |

### /api/v1/broadcast
---
##### ***POST***
**Summary:** Broadcast a transaction.

**Description:** Broadcasts a signed transaction. A single transaction must be sent in hex format in plain text.

**Destination:** Witness node.

**Rate Limit:** 5 requests per IP per second.

**Test URL:** [https://testnet-dex.binance.org/api/v1/broadcast](https://testnet-dex.binance.org/api/v1/broadcast)


**Parameters**

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| sync | query | Synchronous broadcast (wait for DeliverTx) | No | boolean |
| body | body |  | Yes | binary |

**Responses**

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Success | [ [Transaction](#transaction) ] |
| 400 | Bad Request | [Error](#error) |
| 404 | Not Found |  |
| default | Generic error response | [Error](#error) |

### /api/v1/klines
---
##### ***GET***
**Summary:** Get candlestick bars.

**Description:** Gets candlestick/kline bars for a symbol. Bars are uniquely identified by their open time.

**Test URL:** [https://testnet-dex.binance.org/api/v1/klines?symbol=NNB-338_BNB&interval=5m](https://testnet-dex.binance.org/api/v1/klines?symbol=NNB-338_BNB&interval=5m)

**Example**

```
[
  1499040000000,      // Open time
  "0.01634790",       // Open
  "0.80000000",       // High
  "0.01575800",       // Low
  "0.01577100",       // Close
  "148976.11427815",  // Volume
  1499644799999,      // Close time
  "2434.19055334",    // Quote asset volume
  308                // Number of trades
]
```


**Parameters**

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| symbol | query | symbol | Yes | string |
| interval | query | interval. Allowed value: [1m, 3m, 5m, 15m, 30m, 1h, 2h, 4h, 6h, 8h, 12h, 1d, 3d, 1w, 1M] | Yes | string |
| limit | query | default 300; max 1000. | No | integer |
| startTime | query | start time | No | long |
| endTime | query | end time | No | long |

**Responses**

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | OK | [ [Candlestick](#candlestick) ] |

### /api/v1/orders/closed
---
##### ***GET***
**Summary:** Get closed orders.

**Description:** Gets closed (filled and cancelled) orders for a given address.

**Parameters**

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| address | query | the owner address | Yes | string |
| end | query | end time | No | long |
| limit | query | default 500; max 1000. | No | integer |
| offset | query | start with 0; default 0. | No | integer |
| side | query | order side. 1 for buy and 2 for sell. | No | integer |
| start | query | start time; The maximum start - end query window is 3 months; Default query window is latest 7 days. | No | long |
| status | query | order status list. Allowed value: [ACK, PARTIALLY_FILLED, IOC_NO_FILL, FULLY_FILLED, CANCELED, EXPIRED, FAIL_BLOCKING, FAIL_MATCH] | No | [ string ] |
| symbol | query | symbol | No | string |
| total | query | total number required, 0 for not required and 1 for required; default not required, return total=-1 in response | No | integer |

**Responses**

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | OK | [OrderList](#orderlist) |

### /api/v1/orders/open
---
##### ***GET***
**Summary:** Get open orders.

**Description:** Gets open orders for a given address.

**Parameters**

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| address | query | the owner address | Yes | string |
| limit | query | default 500; max 1000. | No | integer |
| offset | query | start with 0; default 0. | No | integer |
| symbol | query | symbol | No | string |

**Responses**

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | OK | [OrderList](#orderlist) |
| 400 | Bad Request | [Error](#error) |
| 404 | Not Found |  |
| default | Generic error response | [Error](#error) |

### /api/v1/orders/{id}
---
##### ***GET***
**Summary:** Get an order.

**Description:** Gets metadata for an individual order by its ID.

**Parameters**

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| id | path | order id | Yes | string |

**Responses**

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | OK | [Order](#order) |
| 400 | Bad Request | [Error](#error) |
| 404 | Not Found |  |
| default | Generic error response | [Error](#error) |

### /api/v1/ticker/24hr
---
##### ***GET***
**Summary:** Get a market ticker.

**Description:** Gets 24 hour price change statistics for a market pair symbol.

**Parameters**

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| symbol | query | symbol | No | string |

**Responses**

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | OK | [ [TickerStatistics](#tickerstatistics) ] |
| 400 | Bad Request | [Error](#error) |
| 404 | Not Found |  |
| default | Generic error response | [Error](#error) |

### /api/v1/trades
---
##### ***GET***
**Summary:** Get market trades.

**Description:** Gets a list of historical trades.

**Parameters**

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| address | query | the buyer/seller address | No | string |
| baseAsset | query | base asset | No | string |
| buyerOrderId | query | buyer order id | No | string |
| end | query | end time | No | long |
| height | query | block height | No | long |
| limit | query | default 500; max 1000. | No | integer |
| offset | query | start with 0; default 0. | No | integer |
| quoteAsset | query | quote asset | No | string |
| sellerOrderId | query | seller order id | No | string |
| side | query | order side. 1 for buy and 2 for sell. | No | integer |
| start | query | start time; The maximum start - end query window is 3 months; Default query window is latest 7 days. | No | long |
| symbol | query | symbol | No | string |
| total | query | total number required, 0 for not required and 1 for required; default not required, return total=-1 in response | No | integer |

**Responses**

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | OK | [TradePage](#tradepage) |
| 400 | Bad Request | [Error](#error) |
| 404 | Not Found |  |
| default | Generic error response | [Error](#error) |

### /api/v1/transactions
---
##### ***GET***
**Summary:** Get transactions.

**Description:** Gets a list of transactions.

**Parameters**

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| address | query | address | Yes | string |
| blockHeight | query | blockHeight | No | long |
| endTime | query | endTime | No | long |
| limit | query | limit | No | integer |
| offset | query | offset | No | integer |
| side | query | transaction side. Allowed value: [ RECEIVE, SEND] | No | string |
| startTime | query | start time; The maximum start - end query window is 3 months; Default query window is latest 7 days. | No | long |
| txAsset | query | txAsset | No | string |
| txType | query | transaction type. Allowed value: [ NEW_ORDER,ISSUE_TOKEN,BURN_TOKEN,LIST_TOKEN,CANCEL_ORDER,FREEZE_TOKEN,UN_FREEZE_TOKEN,TRANSFER,PROPOSAL,VOTE] | No | string |

**Responses**

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | OK | [TxPage](#txpage) |
| 400 | Bad Request | [Error](#error) |
| 404 | Not Found |  |
| default | Generic error response | [Error](#error) |

### Models
---

### Error  

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| code | long |  | No |
| message | string |  | Yes |

### Times  

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| ap_time | string | e.g. 2019-01-21T10:30:00Z | No |
| block_time | string | format as above | No |

### Validators  

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| block_height | long | Current block height | No |
| validators | [  ] |  | No |

### Peers  

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| Peers | array |  |  |

### Transaction  

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| code | integer |  | No |
| log | string |  | No |
| data | string |  | No |
| hash | string |  | No |
| ok | boolean |  | No |

### Account  

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| account_number | integer |  | No |
| address | string (address) |  | No |
| balances | [ [Balance](#balance) ] |  | No |
| public_key | [ integer ] | Public key bytes | No |
| sequence | long |  | No |

### AccountSequence  

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| sequence | long |  | No |

### Balance  

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| symbol | string (currency) |  | No |
| free | string (fixed8) | In decimal form, e.g. 0.00000000 | No |
| locked | string (fixed8) | In decimal form, e.g. 0.00000000 | No |
| frozen | string (fixed8) | In decimal form, e.g. 0.00000000 | No |

### Tokens  

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| Tokens | array |  |  |

### Markets  

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| Markets | array |  |  |

### MarketDepth  

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| asks | [ string (fixed8) ] | Price and qty in decimal form, e.g. 1.00000000 | No |
| bids | [ string (fixed8) ] | Price and qty in decimal form, e.g. 1.00000000 | No |

### BlockTradePage  

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| blockTrade | [ [BlockTrade](#blocktrade) ] |  | No |
| total | long |  | No |

### BlockTrade  

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| blockTime | long |  | No |
| fee | string |  | No |
| height | long |  | No |
| trade | [ [Trade](#trade) ] |  | No |

### Candlestick  

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| close | number |  | No |
| closeTime | long |  | No |
| high | number |  | No |
| low | number |  | No |
| numberOfTrades | integer |  | No |
| open | number |  | No |
| openTime | long |  | No |
| quoteAssetVolume | number |  | No |
| volume | number |  | No |

### OrderList  

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| order | [ [Order](#order) ] |  | No |
| total | long |  | No |

### Order  

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| cumulateQuantity | string |  | No |
| fee | string |  | No |
| lastExecutedPrice | string |  | No |
| lastExecutedQuantity | string |  | No |
| orderCreateTime | dateTime |  | No |
| orderId | string |  | No |
| owner | string |  | No |
| price | string |  | No |
| quantity | string |  | No |
| side | integer | 1 for buy and 2 for sell | No |
| status | string | enum [ACK, PARTIALLY_FILLED, IOC_NO_FILL, FULLY_FILLED, CANCELED, EXPIRED, FAIL_BLOCKING, FAIL_MATCH] | No |
| symbol | string |  | No |
| timeInForce | integer | 1 for Good Till Expire(GTE) order and 3 for Immediate Or Cancel (IOC) | No |
| tradeId | string |  | No |
| transactionHash | string |  | No |
| transactionTime | dateTime |  | No |
| type | integer | only 2 is available for now, meaning limit order | No |

### TickerStatistics  

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| askPrice | string |  | No |
| askQuantity | string |  | No |
| bidPrice | string |  | No |
| bidQuantity | string |  | No |
| closeTime | long |  | No |
| count | long |  | No |
| firstId | string |  | No |
| highPrice | string |  | No |
| lastId | string |  | No |
| lastPrice | string |  | No |
| lastQuantity | string |  | No |
| lowPrice | string |  | No |
| openPrice | string |  | No |
| openTime | long |  | No |
| prevClosePrice | string |  | No |
| priceChange | string |  | No |
| priceChangePercent | string |  | No |
| quoteVolume | string |  | No |
| symbol | string |  | No |
| volume | string |  | No |
| weightedAvgPrice | string |  | No |

### TradePage  

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| total | long |  | No |
| trade | [ [Trade](#trade) ] |  | No |

### Trade  

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| baseAsset | string |  | No |
| blockHeight | long |  | No |
| buyFee | string |  | No |
| buyerId | string |  | No |
| buyerOrderId | string |  | No |
| price | string |  | No |
| quantity | string |  | No |
| quoteAsset | string |  | No |
| sellFee | string |  | No |
| sellerId | string |  | No |
| sellerOrderId | string |  | No |
| symbol | string |  | No |
| time | long |  | No |
| tradeId | string |  | No |

### TxPage  

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| total | long |  | No |
| tx | [ [Tx](#tx) ] |  | No |

### Tx  

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| blockHeight | long |  | No |
| code | integer |  | No |
| confirmBlocks | long |  | No |
| data | string |  | No |
| fromAddr | string |  | No |
| orderId | string |  | No |
| timeStamp | dateTime |  | No |
| toAddr | string |  | No |
| txAge | long |  | No |
| txAsset | string |  | No |
| txFee | string |  | No |
| txHash | string |  | No |
| txType | string |  | No |
| value | string |  | No |

### ExchangeRate  

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| ExchangeRate | object |  |  |