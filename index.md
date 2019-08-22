
# fractal_rpc



## Indices

* [admin](#admin)

  * [addPeer](#1-addpeer)
  * [removePeer](#2-removepeer)
  * [addTrustedPeer](#3-addtrustedpeer)
  * [removeTrustedPeer](#4-removetrustedpeer)
  * [addBlack](#5-addblack)
  * [removeBlack](#6-removeblack)
  * [stopMining](#7-stopmining)
  * [startMining](#8-startmining)
  * [Mining](#9-mining)
  * [generateMiningKey](#10-generateminingkey)
  * [isPackerEnable](#11-ispackerenable)
  * [stopPacking](#12-stoppacking)
  * [startPacking](#13-startpacking)
  * [isPacking](#14-ispacking)

* [ftl](#ftl)

  * [addPeer](#1-addpeer-1)
  * [genesis](#2-genesis)
  * [getBlock](#3-getblock)
  * [getBlockByHeight](#4-getblockbyheight)
  * [blockHeight](#5-blockheight)
  * [getBackwardBlocks](#6-getbackwardblocks)
  * [getAncestorBlocks](#7-getancestorblocks)
  * [getDescendantBlocks](#8-getdescendantblocks)
  * [getNearbyBlocks](#9-getnearbyblocks)
  * [getBalance](#10-getbalance)
  * [getStorageAt UNDO](#11-getstorageat-undo)
  * [getCode](#12-getcode)
  * [getContractOwner](#13-getcontractowner)
  * [getLogs UNDO](#14-getlogs-undo)
  * [coinbase](#15-coinbase)
  * [protocolVersion](#16-protocolversion)
  * [chainId](#17-chainid)

* [net](#net)

  * [listening](#1-listening)
  * [peerCount UNWORK](#2-peercount-unwork)
  * [peers UNWORK](#3-peers-unwork)
  * [nodeInfo](#4-nodeinfo)
  * [nodeInfo Copy](#5-nodeinfo-copy)

* [packer](#packer)

  * [getTxPackageByHash](#1-gettxpackagebyhash)
  * [sendRawTransaction UNDO](#2-sendrawtransaction-undo)

* [tx_pool](#tx_pool)

  * [getTxPackageByHash UNDO](#1-gettxpackagebyhash-undo)
  * [content](#2-content)
  * [status](#3-status)
  * [inspenct](#4-inspenct)
  * [getTransactionNonce](#5-gettransactionnonce)
  * [getBlockTransactionCountByHash](#6-getblocktransactioncountbyhash)
  * [SendRawTransaction UNDO](#7-sendrawtransaction-undo)
  * [encodeAction](#8-encodeaction)
  * [pendingTransactions](#9-pendingtransactions)
  * [gasPrice](#10-gasprice)


--------


## admin



### 1. addPeer



***Endpoint:***

```bash
Method: GET
Type: RAW
URL: http://{{host}}:8545/rpc
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Content-Type | application/json |  |



***Body:***

```js        
{
            "jsonrpc": "2.0",
            "id": "1",
            "method": "admin_addPeer",
            "params": ["enode://9fb5d28a4f0d086521bb3824782ad8b3d982190afc839200276e926dd2661b804854e609cd95a7bbc8969f2d513aac6a74c7c839409e786697d01ceb50fb2919@210.22.171.162:30304"]
}
```



### 2. removePeer



***Endpoint:***

```bash
Method: GET
Type: RAW
URL: http://{{host}}:8545/rpc
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Content-Type | application/json |  |



***Body:***

```js        
{
            "jsonrpc": "2.0",
            "id": "1",
            "method": "admin_removePeer",
            "params": ["enode://9fb5d28a4f0d086521bb3824782ad8b3d982190afc839200276e926dd2661b804854e609cd95a7bbc8969f2d513aac6a74c7c839409e786697d01ceb50fb2919@210.22.171.162:30304"]
}
```



### 3. addTrustedPeer



***Endpoint:***

```bash
Method: GET
Type: RAW
URL: http://{{host}}:8545/rpc
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Content-Type | application/json |  |



***Body:***

```js        
{
            "jsonrpc": "2.0",
            "id": "1",
            "method": "admin_addTrustedPeer",
            "params": ["enode://9fb5d28a4f0d086521bb3824782ad8b3d982190afc839200276e926dd2661b804854e609cd95a7bbc8969f2d513aac6a74c7c839409e786697d01ceb50fb2919@210.22.171.162:30304"]
}
```



### 4. removeTrustedPeer



***Endpoint:***

```bash
Method: GET
Type: RAW
URL: http://{{host}}:8545/rpc
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Content-Type | application/json |  |



***Body:***

```js        
{
            "jsonrpc": "2.0",
            "id": "1",
            "method": "admin_removeTrustedPeer",
            "params": ["enode://9fb5d28a4f0d086521bb3824782ad8b3d982190afc839200276e926dd2661b804854e609cd95a7bbc8969f2d513aac6a74c7c839409e786697d01ceb50fb2919@210.22.171.162:30304"]
}
```



### 5. addBlack



***Endpoint:***

```bash
Method: GET
Type: RAW
URL: http://{{host}}:8545/rpc
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Content-Type | application/json |  |



***Body:***

```js        
{
            "jsonrpc": "2.0",
            "id": "1",
            "method": "admin_addBlack",
            "params": ["enode://9fb5d28a4f0d086521bb3824782ad8b3d982190afc839200276e926dd2661b804854e609cd95a7bbc8969f2d513aac6a74c7c839409e786697d01ceb50fb2919@210.22.171.162:30304"]
}
```



### 6. removeBlack



***Endpoint:***

```bash
Method: GET
Type: RAW
URL: http://{{host}}:8545/rpc
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Content-Type | application/json |  |



***Body:***

```js        
{
            "jsonrpc": "2.0",
            "id": "1",
            "method": "admin_removeBlack",
            "params": ["enode://9fb5d28a4f0d086521bb3824782ad8b3d982190afc839200276e926dd2661b804854e609cd95a7bbc8969f2d513aac6a74c7c839409e786697d01ceb50fb2919@210.22.171.162:30304"]
}
```



### 7. stopMining



***Endpoint:***

```bash
Method: GET
Type: RAW
URL: http://{{host}}:8545/rpc
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Content-Type | application/json |  |



***Body:***

```js        
{
            "jsonrpc": "2.0",
            "id": "1",
            "method": "admin_stopMining",
            "params": ["enode://9fb5d28a4f0d086521bb3824782ad8b3d982190afc839200276e926dd2661b804854e609cd95a7bbc8969f2d513aac6a74c7c839409e786697d01ceb50fb2919@210.22.171.162:30304"]
}
```



### 8. startMining



***Endpoint:***

```bash
Method: GET
Type: RAW
URL: http://{{host}}:8545/rpc
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Content-Type | application/json |  |



***Body:***

```js        
{
            "jsonrpc": "2.0",
            "id": "1",
            "method": "admin_startMining",
            "params": []
}
```



### 9. Mining



***Endpoint:***

```bash
Method: GET
Type: RAW
URL: http://{{host}}:8545/rpc
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Content-Type | application/json |  |



***Body:***

```js        
{
            "jsonrpc": "2.0",
            "id": "1",
            "method": "admin_mining",
            "params": []
}
```



### 10. generateMiningKey



***Endpoint:***

```bash
Method: GET
Type: RAW
URL: http://{{host}}:8545/rpc
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Content-Type | application/json |  |



***Body:***

```js        
{
            "jsonrpc": "2.0",
            "id": "1",
            "method": "admin_generateMiningKey",
            "params": ["0xa04358d378cf97a933eb09b6014f4f118378e9f4"]
}
```



### 11. isPackerEnable



***Endpoint:***

```bash
Method: GET
Type: RAW
URL: http://{{host}}:8545/rpc
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Content-Type | application/json |  |



***Body:***

```js        
{
            "jsonrpc": "2.0",
            "id": "1",
            "method": "admin_isPackerEnable",
            "params": []
}
```



### 12. stopPacking



***Endpoint:***

```bash
Method: GET
Type: RAW
URL: http://{{host}}:8545/rpc
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Content-Type | application/json |  |



***Body:***

```js        
{
            "jsonrpc": "2.0",
            "id": "1",
            "method": "admin_stopPacking",
            "params": []
}
```



### 13. startPacking



***Endpoint:***

```bash
Method: GET
Type: RAW
URL: http://{{host}}:8545/rpc
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Content-Type | application/json |  |



***Body:***

```js        
{
            "jsonrpc": "2.0",
            "id": "1",
            "method": "admin_startPacking",
            "params": [1]
}
```



### 14. isPacking



***Endpoint:***

```bash
Method: GET
Type: RAW
URL: http://{{host}}:8545/rpc
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Content-Type | application/json |  |



***Body:***

```js        
{
            "jsonrpc": "2.0",
            "id": "1",
            "method": "admin_isPacking",
            "params": []
}
```



## ftl



### 1. addPeer



***Endpoint:***

```bash
Method: GET
Type: RAW
URL: http://{{host}}:8545/rpc
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Content-Type | application/json |  |



***Body:***

```js        
{
            "jsonrpc": "2.0",
            "id": "1",
            "method": "ftl_headBlock",
            "params": []
}
```



### 2. genesis



***Endpoint:***

```bash
Method: GET
Type: RAW
URL: http://{{host}}:8545/rpc
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Content-Type | application/json |  |



***Body:***

```js        
{
            "jsonrpc": "2.0",
            "id": "1",
            "method": "ftl_genesis",
            "params": []
}
```



### 3. getBlock



***Endpoint:***

```bash
Method: GET
Type: RAW
URL: http://{{host}}:8545/rpc
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Content-Type | application/json |  |



***Body:***

```js        
{
            "jsonrpc": "2.0",
            "id": "1",
            "method": "ftl_getBlock",
            "params": ["0xd1c0f4f8e1ef3fb27bc19a3d0641f2e28cc61689340b10f73b3fdc65d0955fdf"]
}
```



### 4. getBlockByHeight



***Endpoint:***

```bash
Method: GET
Type: RAW
URL: http://{{host}}:8545/rpc
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Content-Type | application/json |  |



***Body:***

```js        
{
            "jsonrpc": "2.0",
            "id": "1",
            "method": "ftl_getBlockByHeight",
            "params": ["0x2"]
}
```



### 5. blockHeight



***Endpoint:***

```bash
Method: GET
Type: RAW
URL: http://{{host}}:8545/rpc
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Content-Type | application/json |  |



***Body:***

```js        
{
            "jsonrpc": "2.0",
            "id": "1",
            "method": "ftl_blockHeight",
            "params": []
}
```



### 6. getBackwardBlocks



***Endpoint:***

```bash
Method: GET
Type: RAW
URL: http://{{host}}:8545/rpc
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Content-Type | application/json |  |



***Body:***

```js        
{
            "jsonrpc": "2.0",
            "id": "1",
            "method": "ftl_getBackwardBlocks",
            "params": ["0xd1c0f4f8e1ef3fb27bc19a3d0641f2e28cc61689340b10f73b3fdc65d0955fdf", 2]
}
```



### 7. getAncestorBlocks



***Endpoint:***

```bash
Method: GET
Type: RAW
URL: http://{{host}}:8545/rpc
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Content-Type | application/json |  |



***Body:***

```js        
{
            "jsonrpc": "2.0",
            "id": "1",
            "method": "ftl_getAncestorBlocks",
            "params": ["0xd1c0f4f8e1ef3fb27bc19a3d0641f2e28cc61689340b10f73b3fdc65d0955fdf", 2]
}
```



### 8. getDescendantBlocks



***Endpoint:***

```bash
Method: GET
Type: RAW
URL: http://{{host}}:8545/rpc
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Content-Type | application/json |  |



***Body:***

```js        
{
            "jsonrpc": "2.0",
            "id": "1",
            "method": "ftl_getDescendantBlocks",
            "params": ["0xd1c0f4f8e1ef3fb27bc19a3d0641f2e28cc61689340b10f73b3fdc65d0955fdf", 4]
}
```



### 9. getNearbyBlocks



***Endpoint:***

```bash
Method: GET
Type: RAW
URL: http://{{host}}:8545/rpc
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Content-Type | application/json |  |



***Body:***

```js        
{
            "jsonrpc": "2.0",
            "id": "1",
            "method": "ftl_getNearbyBlocks",
            "params": ["0xd1c0f4f8e1ef3fb27bc19a3d0641f2e28cc61689340b10f73b3fdc65d0955fdf", 4]
}
```



### 10. getBalance



***Endpoint:***

```bash
Method: GET
Type: RAW
URL: http://{{host}}:8545/rpc
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Content-Type | application/json |  |



***Body:***

```js        
{
            "jsonrpc": "2.0",
            "id": "1",
            "method": "ftl_getBalance",
            "params": ["0xa04358d378cf97a933eb09b6014f4f118378e9f4", "0xd1c0f4f8e1ef3fb27bc19a3d0641f2e28cc61689340b10f73b3fdc65d0955fdf"]
}
```



### 11. getStorageAt UNDO



***Endpoint:***

```bash
Method: GET
Type: RAW
URL: http://{{host}}:8545/rpc
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Content-Type | application/json |  |



***Body:***

```js        
{
            "jsonrpc": "2.0",
            "id": "1",
            "method": "ftl_getStorageAt",
            "params": ["0xa04358d378cf97a933eb09b6014f4f118378e9f4", "0xd1c0f4f8e1ef3fb27bc19a3d0641f2e28cc61689340b10f73b3fdc65d0955fdf"]
}
```



### 12. getCode



***Endpoint:***

```bash
Method: GET
Type: RAW
URL: http://{{host}}:8545/rpc
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Content-Type | application/json |  |



***Body:***

```js        
{
            "jsonrpc": "2.0",
            "id": "1",
            "method": "ftl_getCode",
            "params": ["0xa04358d378cf97a933eb09b6014f4f118378e9f4", "0xd1c0f4f8e1ef3fb27bc19a3d0641f2e28cc61689340b10f73b3fdc65d0955fdf"]
}
```



### 13. getContractOwner



***Endpoint:***

```bash
Method: GET
Type: RAW
URL: http://{{host}}:8545/rpc
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Content-Type | application/json |  |



***Body:***

```js        
{
            "jsonrpc": "2.0",
            "id": "1",
            "method": "ftl_getContractOwner",
            "params": ["0xa04358d378cf97a933eb09b6014f4f118378e9f4"]
}
```



### 14. getLogs UNDO



***Endpoint:***

```bash
Method: GET
Type: RAW
URL: http://{{host}}:8545/rpc
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Content-Type | application/json |  |



***Body:***

```js        
{
            "jsonrpc": "2.0",
            "id": "1",
            "method": "ftl_getContractOwner",
            "params": ["0xa04358d378cf97a933eb09b6014f4f118378e9f4"]
}
```



### 15. coinbase



***Endpoint:***

```bash
Method: GET
Type: RAW
URL: http://{{host}}:8545/rpc
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Content-Type | application/json |  |



***Body:***

```js        
{
            "jsonrpc": "2.0",
            "id": "1",
            "method": "ftl_coinbase",
            "params": ["0xa04358d378cf97a933eb09b6014f4f118378e9f4"]
}
```



### 16. protocolVersion



***Endpoint:***

```bash
Method: GET
Type: RAW
URL: http://{{host}}:8545/rpc
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Content-Type | application/json |  |



***Body:***

```js        
{
            "jsonrpc": "2.0",
            "id": "1",
            "method": "ftl_protocolVersion",
            "params": []
}
```



### 17. chainId



***Endpoint:***

```bash
Method: GET
Type: RAW
URL: http://{{host}}:8545/rpc
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Content-Type | application/json |  |



***Body:***

```js        
{
            "jsonrpc": "2.0",
            "id": "1",
            "method": "ftl_chainId",
            "params": []
}
```



## net



### 1. listening



***Endpoint:***

```bash
Method: GET
Type: RAW
URL: http://{{host}}:8545/rpc
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Content-Type | application/json |  |



***Body:***

```js        
{
            "jsonrpc": "2.0",
            "id": "1",
            "method": "net_listening",
            "params": []
}
```



### 2. peerCount UNWORK



***Endpoint:***

```bash
Method: GET
Type: RAW
URL: http://{{host}}:8545/rpc
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Content-Type | application/json |  |



***Body:***

```js        
{
            "jsonrpc": "2.0",
            "id": "1",
            "method": "net_peerCount",
            "params": []
}
```



### 3. peers UNWORK



***Endpoint:***

```bash
Method: GET
Type: RAW
URL: http://{{host}}:8545/rpc
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Content-Type | application/json |  |



***Body:***

```js        
{
            "jsonrpc": "2.0",
            "id": "1",
            "method": "net_peers",
            "params": []
}
```



### 4. nodeInfo



***Endpoint:***

```bash
Method: GET
Type: RAW
URL: http://{{host}}:8545/rpc
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Content-Type | application/json |  |



***Body:***

```js        
{
            "jsonrpc": "2.0",
            "id": "1",
            "method": "net_nodeInfo",
            "params": []
}
```



### 5. nodeInfo Copy



***Endpoint:***

```bash
Method: GET
Type: RAW
URL: http://{{host}}:8545/rpc
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Content-Type | application/json |  |



***Body:***

```js        
{
            "jsonrpc": "2.0",
            "id": "1",
            "method": "net_version",
            "params": []
}
```



## packer



### 1. getTxPackageByHash



***Endpoint:***

```bash
Method: GET
Type: RAW
URL: http://{{host}}:8545/rpc
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Content-Type | application/json |  |



***Body:***

```js        
{
            "jsonrpc": "2.0",
            "id": "1",
            "method": "pack_getTxPackageByHash",
            "params": ["0xfda689596a9a0f1e184b972b3ca2601f03c0d52abf1db7604356d1eec22f54f4"]
}
```



### 2. sendRawTransaction UNDO



***Endpoint:***

```bash
Method: GET
Type: RAW
URL: http://{{host}}:8545/rpc
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Content-Type | application/json |  |



***Body:***

```js        
{
            "jsonrpc": "2.0",
            "id": "1",
            "method": "pack_getTxPackageByHash",
            "params": ["0xfda689596a9a0f1e184b972b3ca2601f03c0d52abf1db7604356d1eec22f54f4"]
}
```



## tx_pool



### 1. getTxPackageByHash UNDO



***Endpoint:***

```bash
Method: GET
Type: RAW
URL: http://{{host}}:8545/rpc
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Content-Type | application/json |  |



***Body:***

```js        
{
            "jsonrpc": "2.0",
            "id": "1",
            "method": "txpool_getTransactionByHash",
            "params": ["0xfda689596a9a0f1e184b972b3ca2601f03c0d52abf1db7604356d1eec22f54f4"]
}
```



### 2. content



***Endpoint:***

```bash
Method: GET
Type: RAW
URL: http://{{host}}:8545/rpc
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Content-Type | application/json |  |



***Body:***

```js        
{
            "jsonrpc": "2.0",
            "id": "1",
            "method": "txpool_content",
            "params": []
}
```



### 3. status



***Endpoint:***

```bash
Method: GET
Type: RAW
URL: http://{{host}}:8545/rpc
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Content-Type | application/json |  |



***Body:***

```js        
{
            "jsonrpc": "2.0",
            "id": "1",
            "method": "txpool_status",
            "params": []
}
```



### 4. inspenct



***Endpoint:***

```bash
Method: GET
Type: RAW
URL: http://{{host}}:8545/rpc
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Content-Type | application/json |  |



***Body:***

```js        
{
            "jsonrpc": "2.0",
            "id": "1",
            "method": "txpool_inspect",
            "params": []
}
```



### 5. getTransactionNonce



***Endpoint:***

```bash
Method: GET
Type: RAW
URL: http://{{host}}:8545/rpc
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Content-Type | application/json |  |



***Body:***

```js        
{
            "jsonrpc": "2.0",
            "id": "1",
            "method": "txpool_getTransactionNonce",
            "params": ["0xf13376df4b6e043d0e3e6d6561272875aa287294"]
}
```



### 6. getBlockTransactionCountByHash



***Endpoint:***

```bash
Method: GET
Type: RAW
URL: http://{{host}}:8545/rpc
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Content-Type | application/json |  |



***Body:***

```js        
{
            "jsonrpc": "2.0",
            "id": "1",
            "method": "txpool_getBlockTransactionCountByHash",
            "params": ["0xd1c0f4f8e1ef3fb27bc19a3d0641f2e28cc61689340b10f73b3fdc65d0955fdf"]
}
```



### 7. SendRawTransaction UNDO



***Endpoint:***

```bash
Method: GET
Type: RAW
URL: http://{{host}}:8545/rpc
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Content-Type | application/json |  |



***Body:***

```js        
{
            "jsonrpc": "2.0",
            "id": "1",
            "method": "txpool_SendRawTransaction",
            "params": ["0xd1c0f4f8e1ef3fb27bc19a3d0641f2e28cc61689340b10f73b3fdc65d0955fdf"]
}
```



### 8. encodeAction



***Endpoint:***

```bash
Method: GET
Type: RAW
URL: http://{{host}}:8545/rpc
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Content-Type | application/json |  |



***Body:***

```js        
{
            "jsonrpc": "2.0",
            "id": "1",
            "method": "txpool_encodeAction",
            "params": ["0xd1c0f4f8e1ef3fb27bc19a3d0641f2e28cc61689340b10f73b3fdc65d0955fdf", "sdada", "sadasd"]
}
```



### 9. pendingTransactions



***Endpoint:***

```bash
Method: GET
Type: RAW
URL: http://{{host}}8545/rpc
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Content-Type | application/json |  |



***Body:***

```js        
{
            "jsonrpc": "2.0",
            "id": "1",
            "method": "txpool_pendingTransactions",
            "params": []
}
```



### 10. gasPrice



***Endpoint:***

```bash
Method: GET
Type: RAW
URL: http://{{host}}:8545/rpc
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Content-Type | application/json |  |



***Body:***

```js        
{
            "jsonrpc": "2.0",
            "id": "1",
            "method": "txpool_gasPrice",
            "params": []
}
```



---
[Back to top](#fractal_rpc)
> Made with &#9829; by [thedevsaddam](https://github.com/thedevsaddam) | Generated at: 2019-08-22 10:50:55 by [docgen](https://github.com/thedevsaddam/docgen)
