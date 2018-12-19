---
title: Zilliqa JSON-RPC API Documentation

language_tabs: # must be one of https://git.io/vQNgJ
  - shell

toc_footers:
  - <a href='https://github.com/Zilliqa/Zilliqa-Javascript-Library'>Javascript SDK</a>
  - <a href='http://scilla.readthedocs.io/'>Scilla Docs</a>

includes:

search: true
---

# Introduction

[JSON-RPC](https://en.wikipedia.org/wiki/JSON-RPC) is a remote procedure call protocol encoded in JSON. You can use this API to access data in Zilliqa nodes.
The JSON-RPC API server runs on:

+ `https://api.zilliqa.com/` when running on Zilliqa _**Maoshanwang**_ testnet.
+ `http://localhost:4201/` when running Zilliqa locally.

All API calls are POST requests made to machine running the Zilliqa lookup node.

All requests follow the standard JSON-RPC format and include 4 variables in the data object:

| Data object |      Example      |
|----------|:-------------|
| `id` |  e.g. "1" |
| `jsonrpc` |    e.g. "2.0"   |
| `method` | e.g. "GetBalance" |
| `params` | e.g. ["1"] |

Code examples using curl can be viewed in the dark area to the right.

# Blockchain-related methods

## GetNetworkId

```shell
curl -d '{
    "id": "1",
    "jsonrpc": "2.0",
    "method": "GetNetworkId",
    "params": [""]
}' -H "Content-Type: application/json" -X POST "https://api.zilliqa.com/"
```

> The above command returns JSON structured like this:

```json
{
  "id": "1",
  "jsonrpc": "2.0",
  "result": "TestNet"
}
```

Get the network ID from the specified lookup node.

### HTTP Request

+ **_Maoshanwang_ Testnet:** `POST "https://api.zilliqa.com/"`
+ **Local:** `POST http://localhost:4201/`

### Data Parameters

Parameter | Description
--------- | -------------
id | 1
jsonrpc | "2.0"
method | "GetNetworkId"
params | ""

## GetBlockchainInfo

```shell
curl -d '{
    "id": "1",
    "jsonrpc": "2.0",
    "method": "GetBlockchainInfo",
    "params": [""]
}' -H "Content-Type: application/json" -X POST "https://api.zilliqa.com/"
```

> The above command returns JSON structured like this:

```json
{
    "id":"1",
    "jsonrpc":"2.0",
    "result":{
        "CurrentDSEpoch":"26",
        "CurrentMiniEpoch":"1250",
        "DSBlockRate":1.9217623126238637e-08,
        "NumDSBlocks":"27",
        "NumPeers":40,
        "NumTransactions":"16038",
        "NumTxBlocks":"1250",
        "NumTxnsDSEpoch":"8970",
        "NumTxnsTxEpoch":0,
        "ShardingStructure":{
            "NumPeers":[10,10,10]
        },
        "TransactionRate":0,
        "TxBlockRate":8.0917876984482132e-07
    }
}
```

Get the current network statistics from the specified lookup node.

### HTTP Request

+ **_Maoshanwang_ Testnet:** `POST "https://api.zilliqa.com/"`
+ **Local:** `POST http://localhost:4201/`

### Data Parameters

Parameter | Description
--------- | -------------
id | 1
jsonrpc | "2.0"
method | "GetBlockchainInfo"
params | ""

## GetShardingStructure

```shell
curl -d '{
    "id": "1",
    "jsonrpc": "2.0",
    "method": "GetShardingStructure",
    "params": [""]
}' -H "Content-Type: application/json" -X POST "https://api.zilliqa.com/"
```

> The above command returns JSON structured like this:

```json
{
    "id":"1",
    "jsonrpc":"2.0",
    "result":{
        "NumPeers":[10,10,10]
    }
}
```

Get the current sharding structure of the network from the specified lookup node.

### HTTP Request

+ **_Maoshanwang_ Testnet:** `POST "https://api.zilliqa.com/"`
+ **Local:** `POST http://localhost:4201/`

### Data Parameters

Parameter | Description
--------- | -------------
id | 1
jsonrpc | "2.0"
method | "GetShardingStructure"
params | ""

## GetDsBlock

```shell
curl -d '{
    "id": "1",
    "jsonrpc": "2.0",
    "method": "GetDsBlock",
    "params": ["1"]
}' -H "Content-Type: application/json" -X POST "https://api.zilliqa.com/"
```

> The above command returns JSON structured like this:

```json
{
    "id":"1",
    "jsonrpc":"2.0",
    "result":{
        "header":{
            "BlockNum":"1",
            "Difficulty":3,
            "DifficultyDS":5,
            "GasPrice":"100",
            "LeaderPubKey":"0x0208EA17FE78DE1D4A17B921B7ADB2B3FEE4C795FC5FD54BEA80FCE926F09F79F3",
            "PoWWinners":[
                "0x0307BA09F607D36C6D3B2AC7541592DB8674A889690A14B816FACF67B4F9221CEC",
                "0x0342081E95907022E1E5A525F2D7CE51EB5AF56B7EB13C29C6EC194FB93DF2E752"
            ],
            "PrevHash":"ba127538d2c63eec121629011ae8173210589689dca54d1e11904dd82c68e9da",
            "Timestamp":"1544755380363821"
        },
        "signature":"E2EC67C64323D73D8CCBCC79FEEE04826702751D599995B997AFF7452A7CB7D11CEA8DC5275E9CEAAF7C623F2FEEE132A5F2EF5B9EB63D8C4C5CDD97D64B6CC3"
    }
}
```

Get the details of a specified Directory Service block number.

### HTTP Request

+ **_Maoshanwang_ Testnet:** `POST "https://api.zilliqa.com/"`
+ **Local:** `POST http://localhost:4201/`

### Data Parameters

Parameter | Description
--------- | -------------
id | 1
jsonrpc | "2.0"
method | "GetDsBlock"
params | A specified DS block number.

## GetLatestDsBlock

```shell
curl -d '{
    "id": "1",
    "jsonrpc": "2.0",
    "method": "GetLatestDsBlock",
    "params": [""]
}' -H "Content-Type: application/json" -X POST "https://api.zilliqa.com/"
```

> The above command returns JSON structured like this:

```json
{
    "id":"1",
    "jsonrpc":"2.0",
    "result":{
        "header":{
            "BlockNum":"26",
            "Difficulty":3,
            "DifficultyDS":16,
            "GasPrice":"100",
            "LeaderPubKey":"0x020C11D6B9CA45B56EC80705F1070D9928CFA4BA99212BEF934307C228ECC309FC",
            "PoWWinners":[
                "0x02CB5328E79387F337EC671ECFF0CF2501CCD4DDFCA3565640F94792DE0A7EA0F9",
                "0x0320D26B67A1C701377AA391F2572B66D72F5D0E1A23C44E5B1DA7BF2D53C653E1"
            ],
            "PrevHash":"449a67f3cb160f598ac279f95e6583868a2052c846123558866f56dd6d70cd6c",
            "Timestamp":"1544776175498144"
        },
        "signature":"D096A9F6FB4DAFCFE7112D1C9684CAC2338CDBF0FC17E2B9DF814751BEA8E1F84A889DBC0CEBF903BFD06B1E0C0165F29347EED51B86A613F3C5A18F1CA11EEA"
    }
}
```

Get the details of the most recent Directory Service block.

### HTTP Request

+ **_Maoshanwang_ Testnet:** `POST "https://api.zilliqa.com/"`
+ **Local:** `POST http://localhost:4201/`

### Data Parameters

Parameter | Description
--------- | -------------
id | 1
jsonrpc | "2.0"
method | "GetLatestDsBlock"
params | ""

## GetNumDSBlocks

```shell
curl -d '{
    "id": "1",
    "jsonrpc": "2.0",
    "method": "GetNumDSBlocks",
    "params": [""]
}' -H "Content-Type: application/json" -X POST "https://api.zilliqa.com/"
```

> The above command returns JSON structured like this:

```json
{
    "id":"1",
    "jsonrpc":"2.0",
    "result":"27"
}
```

Get the number of Directory Service blocks in the network so far.

### HTTP Request

+ **_Maoshanwang_ Testnet:** `POST "https://api.zilliqa.com/"`
+ **Local:** `POST http://localhost:4201/`

### Data Parameters

Parameter | Description
--------- | -------------
id | 1
jsonrpc | "2.0"
method | "GetNumDSBlocks"
params | ""

## GetDSBlockRate

```shell
curl -d '{
    "id": "1",
    "jsonrpc": "2.0",
    "method": "GetDSBlockRate",
    "params": [""]
}' -H "Content-Type: application/json" -X POST "https://api.zilliqa.com/"
```

> The above command returns JSON structured like this:

```json
{
    "id":"1",
    "jsonrpc":"2.0",
    "result":1.9217623126238637e-08
}
```

Get the current Directory Service blockrate per second.

### HTTP Request

+ **_Maoshanwang_ Testnet:** `POST "https://api.zilliqa.com/"`
+ **Local:** `POST http://localhost:4201/`

### Data Parameters

Parameter | Description
--------- | -------------
id | 1
jsonrpc | "2.0"
method | "GetDSBlockRate"
params | ""

## DSBlockListing

```shell
curl -d '{
    "id": "1",
    "jsonrpc": "2.0",
    "method": "DSBlockListing",
    "params": [1]
}' -H "Content-Type: application/json" -X POST "https://api.zilliqa.com/"
```

> The above command returns JSON structured like this:

```json
{
  "id": "1",
  "jsonrpc": "2.0",
  "result": {
    "data": [
      {
        "BlockNum": 208,
        "Hash": "D5D8D80034EA93409B0F2DA493533EAA4B5BE5301E705C82A30FB521000CCBD3"
      },
      {
        "BlockNum": 207,
        "Hash": "4FB82808E837F4A2E7C9818CAE4968861F4CF66CB835509EE02ADD08D82F77A8"
      },
      {
        "BlockNum": 206,
        "Hash": "1E21DFFD46147A14C3A2155D588BEF969133A7315E015814D67C38685715A116"
      },
      {
        "BlockNum": 205,
        "Hash": "23D514E64F4F1C7F878EACC239FD7D3E78C1860BCB89CA3E2798BA80B5F62CFB"
      },
      {
        "BlockNum": 204,
        "Hash": "01230FFBC0DA3EBD4DE7C3B4C8438CDD8215171F773731DCA06937754A943868"
      },
      {
        "BlockNum": 203,
        "Hash": "AFFF5FCAABD67639CAD1954836818093AD323F7874D2C7A0850B8ACB2A130100"
      },
      {
        "BlockNum": 202,
        "Hash": "1499C28EF49D534741A988007715376DF437120994DD5999BF15A9168C5414E9"
      },
      {
        "BlockNum": 201,
        "Hash": "A3C62538289B094FBAC4641172E8EA46EE7440733DF497465EB68FB1D26E82E6"
      },
      {
        "BlockNum": 200,
        "Hash": "A200CB54AE5B1D2BB6E8A7E4B3BF930E8DA1081188F6F96DD59FD6D483FEB3E6"
      },
      {
        "BlockNum": 199,
        "Hash": "A4DC7549D3D2A7EA24AA373FDDEB0A5DF06BB8B77C7918015DFB489587BD1C07"
      }
    ],
    "maxPages": 21
  }
}
```

Get a paginated list of Directory Service blocks. Pass in page number as parameter. Returns a `maxPages` variable that specifies the max number of pages. `1` being latest block.

### HTTP Request

+ **_Maoshanwang_ Testnet:** `POST "https://api.zilliqa.com/"`
+ **Local:** `POST http://localhost:4201/`

### Data Parameters

Parameter | Description
--------- | -------------
id | 1
jsonrpc | "2.0"
method | "DSBlockListing"
params | Page number (of type `Int`) of the listings (`1` being the latest block).

## GetTxBlock

```shell
curl -d '{
    "id": "1",
    "jsonrpc": "2.0",
    "method": "GetTxBlock",
    "params": ["40"]
}' -H "Content-Type: application/json" -X POST "https://api.zilliqa.com/"
```

> The above command returns JSON structured like this:

```json
{
    "id":"1",
    "jsonrpc":"2.0",
    "result":{
        "body":{
            "HeaderSign":"DE979D13EC26CEF71A3D1439D9C6E33E3410DB45CA2123CA40AAB3FEC894CFB0843B0423287AF58705B1755E7A486E563B4E1C0F09BDD3B2FDFBE7086CB2FF0D",
            "MicroBlockInfos":[
                {
                    "MicroBlockHash":"e5c88a1ef511b93f6256e881fdb3e5a2c7bee78f03e42664a34c6df9ea5b2a0d",
                    "MicroBlockShardId":0,
                    "MicroBlockTxnRootHash":"0000000000000000000000000000000000000000000000000000000000000000"
                },
                {
                    "MicroBlockHash":"45140cc0e45aeb15256152ecaffd6282d7310b4b0c6f64838a8993467c3bea64",
                    "MicroBlockShardId":1,
                    "MicroBlockTxnRootHash":"0000000000000000000000000000000000000000000000000000000000000000"
                },
                {
                    "MicroBlockHash":"6cff53e230ee1c94b926e67911845694a75a42f86153fbcd09fac18b51c9430b",
                    "MicroBlockShardId":2,
                    "MicroBlockTxnRootHash":"0000000000000000000000000000000000000000000000000000000000000000"
                },
                {
                    "MicroBlockHash":"a277d9b7cc5c680faed13914be8101fed6cdaa5363a0bfe2c913220cc6ea76e1",
                    "MicroBlockShardId":3,
                    "MicroBlockTxnRootHash":"0000000000000000000000000000000000000000000000000000000000000000"
                }
            ]
        },
        "header":{
            "BlockNum":"40",
            "DSBlockNum":"9",
            "GasLimit":"2000000",
            "GasUsed":"0",
            "MbInfoHash":"4f2ce32eef3485037f543ebe5fb781f8d3f3c7c2c700df293205f639787e4f85",
            "MinerPubKey":"0x021C44420BD6086AB8C8CEA8E6932AC58E797002E1DC5B7A4B4BD910651DCFC4DA",
            "NumMicroBlocks":4,
            "NumTxns":0,
            "PrevBlockHash":"369d69f65430710da42a36062c6bcadfd5fc30b277c826e121c373c0727ed8c1",
            "Rewards":"0",
            "StateDeltaHash":"0000000000000000000000000000000000000000000000000000000000000000",
            "StateRootHash":"de7b303987489aa341eb845bf7b3c1d0e4b90709af0d08a9cae2513eaeb0da6d",
            "Timestamp":"1545208765463460",
            "Type":1,
            "Version":0
        }
    }
}
```

Get the details of a specified Transaction block number.

### HTTP Request

+ **_Maoshanwang_ Testnet:** `POST "https://api.zilliqa.com/"`
+ **Local:** `POST http://localhost:4201/`

### Data Parameters

Parameter | Description
--------- | -------------
id | 1
jsonrpc | "2.0"
method | "GetTxBlock"
params | A specified Transaction block number.

## GetLatestTxBlock

```shell
curl -d '{
    "id": "1",
    "jsonrpc": "2.0",
    "method": "GetLatestTxBlock",
    "params": [""]
}' -H "Content-Type: application/json" -X POST "https://api.zilliqa.com/"
```

> The above command returns JSON structured like this:

```json
{
    "id":"1",
    "jsonrpc":"2.0",
    "result":{
        "body":{
            "HeaderSign":"951379481ED79E1006AD38357F3B60EBD21B9FF86984B45E2326C47C3EA965770D65D95ABFAFC41809CD01E7B8C09319DAB1993FEDFED64556679B4034216058",
            "MicroBlockInfos":[
                {
                    "MicroBlockHash":"2b13ea2863a477152eb951878739979071354953e368d7b83233c4414d7c12e8",
                    "MicroBlockShardId":0,
                    "MicroBlockTxnRootHash":"0000000000000000000000000000000000000000000000000000000000000000"
                },
                {
                    "MicroBlockHash":"2d3dec5e435daa4d5cb839fdd92f28c956d403a08c0ef032d67495cc9b094164",
                    "MicroBlockShardId":1,
                    "MicroBlockTxnRootHash":"0000000000000000000000000000000000000000000000000000000000000000"
                },
                {
                    "MicroBlockHash":"5c99d616a52d552c2b23cca001fba88f2afd6b1bcc1d028837e95b0f72b9fbf6",
                    "MicroBlockShardId":2,
                    "MicroBlockTxnRootHash":"0000000000000000000000000000000000000000000000000000000000000000"
                },
                {
                    "MicroBlockHash":"40420e5a8d95b789462cb03e2c02483507b4bfb2d1836a658b6745440bb3e633",
                    "MicroBlockShardId":3,
                    "MicroBlockTxnRootHash":"0000000000000000000000000000000000000000000000000000000000000000"
                }
            ]
        },
        "header":{
            "BlockNum":"49",
            "DSBlockNum":"10",
            "GasLimit":"2000000",
            "GasUsed":"0",
            "MbInfoHash":"9d7ed24a158f2671f274631db6fb47d6a9ed3f505439ffadc0f76e2d81154b91",
            "MinerPubKey":"0x023A3C45D844A48816D32A5C6EA219FE11A25C7EFC090F780DE0117ED0218F6636",
            "NumMicroBlocks":4,
            "NumTxns":0,
            "PrevBlockHash":"6a6038aff1211baebb0256054c961af40c6d9ab19b0dcbd5a2b65b47d4ec9276",
            "Rewards":"191780820000000000",
            "StateDeltaHash":"6b0ac054d4296d329e2c997ec30061549a6f809f9cadc361151079d8799777f4",
            "StateRootHash":"de7b303987489aa341eb845bf7b3c1d0e4b90709af0d08a9cae2513eaeb0da6d",
            "Timestamp":"1545209495904025",
            "Type":1,
            "Version":0
        }
    }
}
```

Get the details of the most recent Transaction block.

### HTTP Request

+ **_Maoshanwang_ Testnet:** `POST "https://api.zilliqa.com/"`
+ **Local:** `POST http://localhost:4201/`

### Data Parameters

Parameter | Description
--------- | -------------
id | 1
jsonrpc | "2.0"
method | "GetLatestTxBlock"
params | ""

## GetNumTxBlocks

```shell
curl -d '{
    "id": "1",
    "jsonrpc": "2.0",
    "method": "GetNumTxBlocks",
    "params": [""]
}' -H "Content-Type: application/json" -X POST "https://api.zilliqa.com/"
```

> The above command returns JSON structured like this:

```json
{
    "id":"1",
    "jsonrpc":"2.0",
    "result":"1000"
}
```

Get the number of Transaction blocks in the network so far.

### HTTP Request

+ **_Maoshanwang_ Testnet:** `POST "https://api.zilliqa.com/"`
+ **Local:** `POST http://localhost:4201/`

### Data Parameters

Parameter | Description
--------- | -------------
id | 1
jsonrpc | "2.0"
method | "GetNumTxBlocks"
params | ""

## GetTxBlockRate

```shell
curl -d '{
    "id": "1",
    "jsonrpc": "2.0",
    "method": "GetTxBlockRate",
    "params": [""]
}' -H "Content-Type: application/json" -X POST "https://api.zilliqa.com/"
```

> The above command returns JSON structured like this:

```json
{
    "id":"1",
    "jsonrpc":"2.0",
    "result":6.5499873692751224e-07
}
```

Get the current Transaction blockrate per second.

### HTTP Request

+ **_Maoshanwang_ Testnet:** `POST "https://api.zilliqa.com/"`
+ **Local:** `POST http://localhost:4201/`

### Data Parameters

Parameter | Description
--------- | -------------
id | 1
jsonrpc | "2.0"
method | "GetTxBlockRate"
params | ""

## TxBlockListing

```shell
curl -d '{
    "id": "1",
    "jsonrpc": "2.0",
    "method": "TxBlockListing",
    "params": [1]
}' -H "Content-Type: application/json" -X POST "https://api.zilliqa.com/"
```

> The above command returns JSON structured like this:

```json
{
    "id":"1",
    "jsonrpc":"2.0",
    "result":{
        "data":[
            {
                "BlockNum":1016,
                "Hash":"BBA0C358B0A578CFD5230E501B76A0D8C3E27D5E82524D8B3028B4D8D68AFD3A"
            },
            {
                "BlockNum":1015,
                "Hash":"F90074A2A50973C80DB358DEF8F6D39157ADAEF1C1634E88B66FD55230212FA7"
            },
            {
                "BlockNum":1014,
                "Hash":"C71C95A4AD784251F3BDBC157CAF87B941F0866A40C5AA2409B724AE55CC25BC"
            },
            {
                "BlockNum":1013,
                "Hash":"9A432A3BD743A1B31B839F1C0E61C4B1D7C3A983D767B8DB9833D7B9537BCCD7"
            },
            {
                "BlockNum":1012,
                "Hash":"141772BB18777685F55D2E8BEB1682357C0D4CD0E28680B8993C2D6B1CE685AE"
            },
            {
                "BlockNum":1011,
                "Hash":"092209AD966FFC928180C3A14F1CD4DBC1D065F167441FC2D31B471C612AE77D"
            },
            {
                "BlockNum":1010,
                "Hash":"7A1A580FEFD45947A4F5DDA1D75CAB96B8DCE15D9E6644DF3BF072F45C52D0F3"
            },
            {
                "BlockNum":1009,
                "Hash":"BDB10D71FF35EB607DC45FF283FD477568903D295B80F9380FCB39D11BE55336"
            },
            {
                "BlockNum":1008,
                "Hash":"E64E2E716D89410B06DF5E32846C4743A755836A35EF449C7955602DF4E60DD0"
            },
            {
                "BlockNum":1007,
                "Hash":"1FD23789E64D1645B7D03058AFCFEB7118A92578A59DA6604568B9B5987F9458"
            }
        ],
        "maxPages":102
    }
}
```

Get a paginated list of Transaction blocks. Pass in page number as parameter. Returns a `maxPages` variable that specifies the max number of pages. `1` being latest block.

### HTTP Request

+ **_Maoshanwang_ Testnet:** `POST "https://api.zilliqa.com/"`
+ **Local:** `POST http://localhost:4201/`

### Data Parameters

Parameter | Description
--------- | -------------
id | 1
jsonrpc | "2.0"
method | "TxBlockListing"
params | Page number (of type `Int`) of the listings (`1` being the latest block).

## GetNumTransactions

```shell
curl -d '{
    "id": "1",
    "jsonrpc": "2.0",
    "method": "GetNumTransactions",
    "params": [""]
}' -H "Content-Type: application/json" -X POST "https://api.zilliqa.com/"
```

> The above command returns JSON structured like this:

```json
{
    "id":"1",
    "jsonrpc":"2.0",
    "result":"19"
}
```

Get the number of Transactions in the network so far.

### HTTP Request

+ **_Maoshanwang_ Testnet:** `POST "https://api.zilliqa.com/"`
+ **Local:** `POST http://localhost:4201/`

### Data Parameters

Parameter | Description
--------- | -------------
id | 1
jsonrpc | "2.0"
method | "GetNumTransactions"
params | ""

## GetTransactionRate

```shell
curl -d '{
    "id": "1",
    "jsonrpc": "2.0",
    "method": "GetTransactionRate",
    "params": [""]
}' -H "Content-Type: application/json" -X POST "https://api.zilliqa.com/"
```

> The above command returns JSON structured like this:

```json
{
    "id":"1",
    "jsonrpc":"2.0",
    "result":0
}
```

Get the current Transaction rate of the network.

### HTTP Request

+ **_Maoshanwang_ Testnet:** `POST "https://api.zilliqa.com/"`
+ **Local:** `POST http://localhost:4201/`

### Data Parameters

Parameter | Description
--------- | -------------
id | 1
jsonrpc | "2.0"
method | "GetTransactionRate"
params | ""

## GetCurrentMiniEpoch

```shell
curl -d '{
    "id": "1",
    "jsonrpc": "2.0",
    "method": "GetCurrentMiniEpoch",
    "params": [""]
}' -H "Content-Type: application/json" -X POST "https://api.zilliqa.com/"
```

> The above command returns JSON structured like this:

```json
{
    "id":"1",
    "jsonrpc":"2.0",
    "result":"1068"
}
```

Get the number of Transaction epochs in the network so far.

### HTTP Request

+ **_Maoshanwang_ Testnet:** `POST "https://api.zilliqa.com/"`
+ **Local:** `POST http://localhost:4201/`

### Data Parameters

Parameter | Description
--------- | -------------
id | 1
jsonrpc | "2.0"
method | "GetCurrentMiniEpoch"
params | ""

## GetCurrentDSEpoch

```shell
curl -d '{
    "id": "1",
    "jsonrpc": "2.0",
    "method": "GetCurrentDSEpoch",
    "params": [""]
}' -H "Content-Type: application/json" -X POST "https://api.zilliqa.com/"
```

> The above command returns JSON structured like this:

```json
{
    "id":"1",
    "jsonrpc":"2.0",
    "result":"22"
}
```

Get the number of DS epochs in the network so far.

### HTTP Request

+ **_Maoshanwang_ Testnet:** `POST "https://api.zilliqa.com/"`
+ **Local:** `POST http://localhost:4201/`

### Data Parameters

Parameter | Description
--------- | -------------
id | 1
jsonrpc | "2.0"
method | "GetCurrentDSEpoch"
params | ""

## GetPrevDifficulty

```shell
curl -d '{
    "id": "1",
    "jsonrpc": "2.0",
    "method": "GetPrevDifficulty",
    "params": [""]
}' -H "Content-Type: application/json" -X POST "https://api.zilliqa.com/"
```

> The above command returns JSON structured like this:

```json
{
    "id":"1",
    "jsonrpc":"2.0",
    "result":3
}
```

Get the minimum shard difficulty of the previous block.

### HTTP Request

+ **_Maoshanwang_ Testnet:** `POST "https://api.zilliqa.com/"`
+ **Local:** `POST http://localhost:4201/`

### Data Parameters

Parameter | Description
--------- | -------------
id | 1
jsonrpc | "2.0"
method | "GetPrevDifficulty"
params | ""

## GetPrevDSDifficulty

```shell
curl -d '{
    "id": "1",
    "jsonrpc": "2.0",
    "method": "GetPrevDSDifficulty",
    "params": [""]
}' -H "Content-Type: application/json" -X POST "https://api.zilliqa.com/"
```

> The above command returns JSON structured like this:

```json
{
    "id":"1",
    "jsonrpc":"2.0",
    "result":16
}
```

Get the minimum shard difficulty of the previous block.

### HTTP Request

+ **_Maoshanwang_ Testnet:** `POST "https://api.zilliqa.com/"`
+ **Local:** `POST http://localhost:4201/`

### Data Parameters

Parameter | Description
--------- | -------------
id | 1
jsonrpc | "2.0"
method | "GetPrevDSDifficulty"
params | ""

# Transaction-related methods

## CreateTransaction

```shell
curl -d '{
    "id": "1",
    "jsonrpc": "2.0",
    "method": "CreateTransaction",
    "params": [{
      "version": 1,
      "nonce": 1,
      "toAddr": "8AD0357EBB5515F694DE597EDA6F3F6BDBAD0FD9",
      "amount": "10000",
      "pubKey": "0205273e54f262f8717a687250591dcfb5755b8ce4e3bd340c7abefd0de1276574",
      "gasPrice": "1",
      "gasLimit": "10",
      "code": "",
      "data": "",
      "signature": "29ad673848dcd7f5168f205f7a9fcd1e8109408e6c4d7d03e4e869317b9067e636b216a32314dd37176c35d51f9d4c24e0e519ba80e66206457c83c9029a490d"
    }]
}' -H "Content-Type: application/json" -X POST "https://api.zilliqa.com/"
```

> The above command returns JSON structured like this:

```json
{
    "id":"1",
    "jsonrpc":"2.0",
    "result":{
        "Info":"Non-contract txn, sent to shard",
        "TranID":"2d1eea871d8845472e98dbe9b7a7d788fbcce226f52e4216612592167b89042c"
    }
}
```

Create a new Transaction. See [Quick Start](https://github.com/Zilliqa/Zilliqa-JavaScript-Library#quick-start) in javascript for an example of how to construct a transaction object.

### HTTP Request

+ **_Maoshanwang_ Testnet:** `POST "https://api.zilliqa.com/"`
+ **Local:** `POST http://localhost:4201/`

### Data Parameters

Parameter | Description
--------- | -------------
id | 1
jsonrpc | "2.0"
method | "CreateTransaction"
params | An object containing the following properties:
------ | -----------------------------------------------
version | The current version of Zilliqa.
nonce | Counter equal to the number of transactions sent by the sender's account, including this one. It's value is = `current account nonce + 1`.
toAddr | Recipient's account address. For deploying new contracts, set this as `0000000000000000000000000000000000000000`.
amount | Transaction amount to be transferred to the destination address
pubKey | Public key of the sender.
gasPrice | An amount that the sender is willing to pay per unit of gas for computations incurred in transaction processing.
gasLimit | The maximum amount of gas that should be used while processing this transaction (For regular transaction, please use `1`. For smart contract transactions, please check out the [gas documentation](https://drive.google.com/file/d/1c0EJXELVe_MxhULPuJgwGvxFGenG7fmK/view?usp=sharing)).
code | **(optional)** String specifying the contract code. Present only when deploying a new contract.
data | **(optional)** Stringified JSON object specifying parameters to be passed to a contract for execution. Present when creating or calling a smart contract.
signature | an EC-Schnorr signature of the entire object

## GetTransaction

```shell
curl -d '{
    "id": "1",
    "jsonrpc": "2.0",
    "method": "GetTransaction",
    "params": ["AAF3089596437A7C6984FA2627B6F38B5F5B80FAEAAC6993C2E82C6A8EE2615E"]
}' -H "Content-Type: application/json" -X POST "https://api.zilliqa.com/"
```

> The above command returns JSON structured like this:

```json
{
    "id":"1",
    "jsonrpc":"2.0",
    "result":{
        "ID":"aaf3089596437a7c6984fa2627b6f38b5f5b80faeaac6993c2e82c6a8ee2615e",
        "amount":"0",
        "gasLimit":"50000",
        "gasPrice":"100",
        "nonce":"4",
        "receipt":{
            "cumulative_gas":"50",
            "success":false
        },
        "senderPubKey":"0x0237AECBF98D57A10DABB66A710B10844765A355645223AA2A2F77AA484228C03A","signature":"0xE44E0DDC6A968233C177FB27D6E326C69EB79A23DDEBBC5A70183039D34CCA39665B2C0526F164F9ADBB1810C8BE028EA17D5357F6BC4A7BCE676B6A96B8987B",
        "toAddr":"0000000000000000000000000000000000000000",
        "version":"0"
    }
}
```

Get details of a Transaction by its hash.

### HTTP Request

+ **_Maoshanwang_ Testnet:** `POST "https://api.zilliqa.com/"`
+ **Local:** `POST http://localhost:4201/`

### Data Parameters

Parameter | Description
--------- | -------------
id | 1
jsonrpc | "2.0"
method | "GetTransaction"
params | Hash of the transaction to retrieve.

## GetRecentTransactions

```shell
curl -d '{
    "id": "1",
    "jsonrpc": "2.0",
    "method": "GetRecentTransactions",
    "params": [""]
}' -H "Content-Type: application/json" -X POST "https://api.zilliqa.com/"
```

> The above command returns JSON structured like this:

```json
{
  "id": "1",
  "jsonrpc": "2.0",
  "result": {
    "TxnHashes": [
      "0e73effb72ddf7a164c69b559970f82e0ae846187a9223af7ced2a741c03f347",
      "43104643e5f35455b71f3cfcb471ce4a4c8b96e00f8e8b77733075662e5fc905",
      "271ac49c852f14fc286409811838840cde3febbeef96eb10cabf1b67fc5cd248",
      "c60ba6f3d374362e140edbfc0110304236d22bbac1a2e31fe62350a0305ed72d",
      "1b551314c9d0f911607e5fccf1115f858c246a12b505375c4a1df44183cac695",
      "36c932b0dc96618021ca778686572b8772a89ffdbbbe672b6df47dfb6dd6daa0",
      "c2f9cf7ae47b996c4fa9c137a8bfa905dce07f6a822f9b869159906a879e2e0e",
      "016b844b473d3a1296e6898036f8edfb1a722811ac8f476adad9320576764453",
      "dbb67c0c77e710e94ce16e91884dedbc127ccec5ec66068471a2da1ff8e4fded",
      "eb594f17752029887245acc3e6a534e565f8873778ab6513aba649b23c2a8e44",
      "6a6097826d05e5f71bec37bddaa8a40a5e35980b5839f84d3a99078ed6b029e4",
      "2ed27839f061e3e7fc0d4c33e7e24c5a706ddf33c805189845cc1101903398a7",
      "d517cd27523d6d51e6c7eedb0f8637ba7cdd1b5814b7ab5dfa7ab9e3f2314a38",
      "675daa74a79797b4d3c94e27149591b8cba5d97ccaa27a9962d560ef845dc42b",
      "6947ea29f71187d12a1968d25a221d62d113f5361ed9ae8378ece85014b77e80",
      "27a016dec19d3a126b75cf466f48d57548279ebb031917ed0d6727c473560bb5",
      "9532127876bd7761ec1ac40c62e1d23160cb0da42777591195091c8b5fd5367f",
      "4e946891a97c2aa6eed67ac7ab4738658db8cef13e7f66f0c2aa1572d7a30b7e",
      "962da9dd3b7e394b6ed79fb7b278c13202c34d4f2e167bb7bdd6f5b85ad802ae",
      "ace1376174f12adda4dcaa2ed01a48cf9e8c02419bdeab4477cd6d60f7239223",
    ],
    "number": 20
  }
}
```

Get the most recent transactions (default: `20`, up to `100`) accepted by the specified zilliqa node.

### HTTP Request

+ **_Maoshanwang_ Testnet:** `POST "https://api.zilliqa.com/"`
+ **Local:** `POST http://localhost:4201/`

### Data Parameters

Parameter | Description
--------- | -------------
id | 1
jsonrpc | "2.0"
method | "GetRecentTransactions"
params | Specified amount of recent transactions to return.

## GetNumTxnsTxEpoch

```shell
curl -d '{
    "id": "1",
    "jsonrpc": "2.0",
    "method": "GetNumTxnsTxEpoch",
    "params": [""]
}' -H "Content-Type: application/json" -X POST "https://api.zilliqa.com/"
```

> The above command returns JSON structured like this:

```json
{
    "id":"1",
    "jsonrpc":"2.0",
    "result":"0"
}
```

Get the number of transactions in this Transaction epoch.

### HTTP Request

+ **_Maoshanwang_ Testnet:** `POST "https://api.zilliqa.com/"`
+ **Local:** `POST http://localhost:4201/`

### Data Parameters

Parameter | Description
--------- | -------------
id | 1
jsonrpc | "2.0"
method | "GetNumTxnsTxEpoch"
params | ""

## GetNumTxnsDSEpoch

```shell
curl -d '{
    "id": "1",
    "jsonrpc": "2.0",
    "method": "GetNumTxnsDSEpoch",
    "params": [""]
}' -H "Content-Type: application/json" -X POST "https://api.zilliqa.com/"
```

> The above command returns JSON structured like this:

```json
{
    "id":"1",
    "jsonrpc":"2.0",
    "result":"0"
}
```

Get the number of transactions in this Directory Service epoch.

### HTTP Request

+ **_Maoshanwang_ Testnet:** `POST "https://api.zilliqa.com/"`
+ **Local:** `POST http://localhost:4201/`

### Data Parameters

Parameter | Description
--------- | -------------
id | 1
jsonrpc | "2.0"
method | "GetNumTxnsDSEpoch"
params | ""

## GetMinimumGasPrice

```shell
curl -d '{
    "id": "1",
    "jsonrpc": "2.0",
    "method": "GetMinimumGasPrice",
    "params": [""]
}' -H "Content-Type: application/json" -X POST "https://api.zilliqa.com/"
```

> The above command returns JSON structured like this:

```json
{
    "id":"1",
    "jsonrpc":"2.0",
    "result":"100"
}
```

Get the minimum gas price of the last DS epoch.

### HTTP Request

+ **_Maoshanwang_ Testnet:** `POST "https://api.zilliqa.com/"`
+ **Local:** `POST http://localhost:4201/`

### Data Parameters

Parameter | Description
--------- | -------------
id | 1
jsonrpc | "2.0"
method | "GetMinimumGasPrice"
params | ""

# Contract-related methods

## GetSmartContractCode

```shell
curl -d '{
    "id": "1",
    "jsonrpc": "2.0",
    "method": "GetSmartContractCode",
    "params": ["fe001824823b12b58708bf24edd94d8b5e1cfcf7"]
}' -H "Content-Type: application/json" -X POST "https://api.zilliqa.com/"
```

> The above command returns JSON structured like this:

```json
{
    "id":"1",
    "jsonrpc":"2.0",
    "result":{
        "code":"scilla_version 0\n\n    (* HelloWorld contract *)\n    \n    import ListUtils\n    \n    (***************************************************)\n    (*               Associated library                *)\n    (***************************************************)\n    library HelloWorld\n    \n    let one_msg = \n      fun (msg : Message) => \n      let nil_msg = Nil {Message} in\n      Cons {Message} msg nil_msg\n    \n    let not_owner_code = Int32 1\n    let set_hello_code = Int32 2\n    \n    (***************************************************)\n    (*             The contract definition             *)\n    (***************************************************)\n    \n    contract HelloWorld\n    (owner: ByStr20)\n    \n    field welcome_msg : String = \"\"\n    \n    transition setHello (msg : String)\n      is_owner = builtin eq owner _sender;\n      match is_owner with\n      | False =>\n        msg = {_tag : \"Main\"; _recipient : _sender; _amount : Uint128 0; code : not_owner_code};\n        msgs = one_msg msg;\n        send msgs\n      | True =>\n        welcome_msg := msg;\n        msg = {_tag : \"Main\"; _recipient : _sender; _amount : Uint128 0; code : set_hello_code};\n        msgs = one_msg msg;\n        send msgs\n      end\n    end\n    \n    \n    transition getHello ()\n        r <- welcome_msg;\n        e = {_eventname: \"getHello()\"; msg: r};\n        event e\n    end"
    }
}
```

Get the Scilla code of a smart contract address.

### HTTP Request

+ **_Maoshanwang_ Testnet:** `POST "https://api.zilliqa.com/"`
+ **Local:** `POST http://localhost:4201/`

### Data Parameters

Parameter | Description
--------- | -------------
id | 1
jsonrpc | "2.0"
method | "GetSmartContractCode"
params | A smart contract address.

## GetSmartContractInit

```shell
curl -d '{
    "id": "1",
    "jsonrpc": "2.0",
    "method": "GetSmartContractInit",
    "params": ["fe001824823b12b58708bf24edd94d8b5e1cfcf7"]
}' -H "Content-Type: application/json" -X POST "https://api.zilliqa.com/"
```

> The above command returns JSON structured like this:

```json
{
    "id":"1",
    "jsonrpc":"2.0",
    "result":[
        {
            "type":"Uint32",
            "value":"0",
            "vname":"_scilla_version"
        },
        {
            "type":"ByStr20",
            "value":"0x1eefc4f453539e5ee732b49eb4792b268c2f3908",
            "vname":"owner"
        },
        {
            "type":"BNum",
            "value":"1583",
            "vname":"_creation_block"
        }
    ]
}
```

Get the initialization parameters (immutable) of a given smart contract address.

### HTTP Request

+ **_Maoshanwang_ Testnet:** `POST "https://api.zilliqa.com/"`
+ **Local:** `POST http://localhost:4201/`

### Data Parameters

Parameter | Description
--------- | -------------
id | 1
jsonrpc | "2.0"
method | "GetSmartContractInit"
params | A smart contract address.

## GetSmartContractState

```shell
curl -d '{
    "id": "1",
    "jsonrpc": "2.0",
    "method": "GetSmartContractState",
    "params": ["fe001824823b12b58708bf24edd94d8b5e1cfcf7"]
}' -H "Content-Type: application/json" -X POST "https://api.zilliqa.com/"
```

> The above command returns JSON structured like this:

```json
{
    "id":"1",
    "jsonrpc":"2.0",
    "result":[
        {
            "type":"String",
            "value":"Hello World",
            "vname":"welcome_msg"
        },
        {
            "type":"Uint128",
            "value":"0",
            "vname":"_balance"
        }
    ]
}
```

Get the state variables (mutable) of a smart contract address.

### HTTP Request

+ **_Maoshanwang_ Testnet:** `POST "https://api.zilliqa.com/"`
+ **Local:** `POST http://localhost:4201/`

### Data Parameters

Parameter | Description
--------- | -------------
id | 1
jsonrpc | "2.0"
method | "GetSmartContractState"
params | A smart contract address.

## GetSmartContracts

```shell
curl -d '{
    "id": "1",
    "jsonrpc": "2.0",
    "method": "GetSmartContracts",
    "params": ["1eefc4f453539e5ee732b49eb4792b268c2f3908"]
}' -H "Content-Type: application/json" -X POST "https://api.zilliqa.com/"
```

> The above command returns JSON structured like this:

```json
{
    "id":"1",
    "jsonrpc":"2.0",
    "result":[
        {
            "address":"6b3070b0abf4371b2b3b26e23f11f4c073b636e5",
            "state":[
                {
                    "type":"String",
                    "value":"Hello World",
                    "vname":"welcome_msg"
                },
                {
                    "type":"Uint128",
                    "value":"0",
                    "vname":"_balance"
                }
            ]
        },
        {
            "address":"13cf0f8c1ea003779df0b7fa08a97903bc760e80",
            "state":[
                {
                    "type":"String",
                    "value":"Hello World",
                    "vname":"welcome_msg"
                },
                {
                    "type":"Uint128",
                    "value":"0",
                    "vname":"_balance"
                }
            ]
        }
    ]
}
```

Get the list of smart contracts created by an address.

### HTTP Request

+ **_Maoshanwang_ Testnet:** `POST "https://api.zilliqa.com/"`
+ **Local:** `POST http://localhost:4201/`

### Data Parameters

Parameter | Description
--------- | -------------
id | 1
jsonrpc | "2.0"
method | "GetSmartContracts"
params | An User's account address.

## GetContractAddressFromTransactionID

```shell
curl -d '{
    "id": "1",
    "jsonrpc": "2.0",
    "method": "GetContractAddressFromTransactionID",
    "params": ["AAF3089596437A7C6984FA2627B6F38B5F5B80FAEAAC6993C2E82C6A8EE2615E"]
}' -H "Content-Type: application/json" -X POST "https://api.zilliqa.com/"
```

> The above command returns JSON structured like this:

```json
{
    "id":"1",
    "jsonrpc":"2.0",
    "result":"c458f39c106582c1a49bac6bc76ec603e2ae0497"
}
```

Get a smart contract address from a transaction ID.

### HTTP Request

+ **_Maoshanwang_ Testnet:** `POST "https://api.zilliqa.com/"`
+ **Local:** `POST http://localhost:4201/`

### Data Parameters

Parameter | Description
--------- | -------------
id | 1
jsonrpc | "2.0"
method | "GetContractAddressFromTransactionID"
params | A Transaction ID.

# Account-related methods

## GetBalance

```shell
curl -d '{
    "id": "1",
    "jsonrpc": "2.0",
    "method": "GetBalance",
    "params": ["1eefc4f453539e5ee732b49eb4792b268c2f3908"]
}' -H "Content-Type: application/json" -X POST "https://api.zilliqa.com/"
```

> The above command returns JSON structured like this:

```json
{
    "id":"1",
    "jsonrpc":"2.0",
    "result":{
        "balance":"18446744073637511711",
        "nonce":16
    }
}
```

Get the balance of an account address.

### HTTP Request

+ **_Maoshanwang_ Testnet:** `POST "https://api.zilliqa.com/"`
+ **Local:** `POST http://localhost:4201/`

### Data Parameters

Parameter | Description
--------- | -------------
id | 1
jsonrpc | "2.0"
method | "GetBalance"
params | ""
