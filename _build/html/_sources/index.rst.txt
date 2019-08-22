fractal\_rpc
============

Indices
-------

-  `admin <#admin>`__

-  `addPeer <#1-addpeer>`__
-  `removePeer <#2-removepeer>`__
-  `addTrustedPeer <#3-addtrustedpeer>`__
-  `removeTrustedPeer <#4-removetrustedpeer>`__
-  `addBlack <#5-addblack>`__
-  `removeBlack <#6-removeblack>`__
-  `stopMining <#7-stopmining>`__
-  `startMining <#8-startmining>`__
-  `Mining <#9-mining>`__
-  `generateMiningKey <#10-generateminingkey>`__
-  `isPackerEnable <#11-ispackerenable>`__
-  `stopPacking <#12-stoppacking>`__
-  `startPacking <#13-startpacking>`__
-  `isPacking <#14-ispacking>`__

-  `ftl <#ftl>`__

-  `addPeer <#1-addpeer-1>`__
-  `genesis <#2-genesis>`__
-  `getBlock <#3-getblock>`__
-  `getBlockByHeight <#4-getblockbyheight>`__
-  `blockHeight <#5-blockheight>`__
-  `getBackwardBlocks <#6-getbackwardblocks>`__
-  `getAncestorBlocks <#7-getancestorblocks>`__
-  `getDescendantBlocks <#8-getdescendantblocks>`__
-  `getNearbyBlocks <#9-getnearbyblocks>`__
-  `getBalance <#10-getbalance>`__
-  `getStorageAt UNDO <#11-getstorageat-undo>`__
-  `getCode <#12-getcode>`__
-  `getContractOwner <#13-getcontractowner>`__
-  `getLogs UNDO <#14-getlogs-undo>`__
-  `coinbase <#15-coinbase>`__
-  `protocolVersion <#16-protocolversion>`__
-  `chainId <#17-chainid>`__

-  `net <#net>`__

-  `listening <#1-listening>`__
-  `peerCount UNWORK <#2-peercount-unwork>`__
-  `peers UNWORK <#3-peers-unwork>`__
-  `nodeInfo <#4-nodeinfo>`__
-  `nodeInfo Copy <#5-nodeinfo-copy>`__

-  `packer <#packer>`__

-  `getTxPackageByHash <#1-gettxpackagebyhash>`__
-  `sendRawTransaction UNDO <#2-sendrawtransaction-undo>`__

-  `tx\_pool <#tx_pool>`__

-  `getTxPackageByHash UNDO <#1-gettxpackagebyhash-undo>`__
-  `content <#2-content>`__
-  `status <#3-status>`__
-  `inspenct <#4-inspenct>`__
-  `getTransactionNonce <#5-gettransactionnonce>`__
-  `getBlockTransactionCountByHash <#6-getblocktransactioncountbyhash>`__
-  `SendRawTransaction UNDO <#7-sendrawtransaction-undo>`__
-  `encodeAction <#8-encodeaction>`__
-  `pendingTransactions <#9-pendingtransactions>`__
-  `gasPrice <#10-gasprice>`__

--------------

admin
-----

1. addPeer
~~~~~~~~~~

***Endpoint:***

.. code:: bash

    Method: GET
    Type: RAW
    URL: http://{{host}}:8545/rpc

***Headers:***

+----------------+--------------------+---------------+
| Key            | Value              | Description   |
+================+====================+===============+
| Content-Type   | application/json   |               |
+----------------+--------------------+---------------+

***Body:***

.. code:: js

    {
                "jsonrpc": "2.0",
                "id": "1",
                "method": "admin_addPeer",
                "params": ["enode://9fb5d28a4f0d086521bb3824782ad8b3d982190afc839200276e926dd2661b804854e609cd95a7bbc8969f2d513aac6a74c7c839409e786697d01ceb50fb2919@210.22.171.162:30304"]
    }

2. removePeer
~~~~~~~~~~~~~

***Endpoint:***

.. code:: bash

    Method: GET
    Type: RAW
    URL: http://{{host}}:8545/rpc

***Headers:***

+----------------+--------------------+---------------+
| Key            | Value              | Description   |
+================+====================+===============+
| Content-Type   | application/json   |               |
+----------------+--------------------+---------------+

***Body:***

.. code:: js

    {
                "jsonrpc": "2.0",
                "id": "1",
                "method": "admin_removePeer",
                "params": ["enode://9fb5d28a4f0d086521bb3824782ad8b3d982190afc839200276e926dd2661b804854e609cd95a7bbc8969f2d513aac6a74c7c839409e786697d01ceb50fb2919@210.22.171.162:30304"]
    }

3. addTrustedPeer
~~~~~~~~~~~~~~~~~

***Endpoint:***

.. code:: bash

    Method: GET
    Type: RAW
    URL: http://{{host}}:8545/rpc

***Headers:***

+----------------+--------------------+---------------+
| Key            | Value              | Description   |
+================+====================+===============+
| Content-Type   | application/json   |               |
+----------------+--------------------+---------------+

***Body:***

.. code:: js

    {
                "jsonrpc": "2.0",
                "id": "1",
                "method": "admin_addTrustedPeer",
                "params": ["enode://9fb5d28a4f0d086521bb3824782ad8b3d982190afc839200276e926dd2661b804854e609cd95a7bbc8969f2d513aac6a74c7c839409e786697d01ceb50fb2919@210.22.171.162:30304"]
    }

4. removeTrustedPeer
~~~~~~~~~~~~~~~~~~~~

***Endpoint:***

.. code:: bash

    Method: GET
    Type: RAW
    URL: http://{{host}}:8545/rpc

***Headers:***

+----------------+--------------------+---------------+
| Key            | Value              | Description   |
+================+====================+===============+
| Content-Type   | application/json   |               |
+----------------+--------------------+---------------+

***Body:***

.. code:: js

    {
                "jsonrpc": "2.0",
                "id": "1",
                "method": "admin_removeTrustedPeer",
                "params": ["enode://9fb5d28a4f0d086521bb3824782ad8b3d982190afc839200276e926dd2661b804854e609cd95a7bbc8969f2d513aac6a74c7c839409e786697d01ceb50fb2919@210.22.171.162:30304"]
    }

5. addBlack
~~~~~~~~~~~

***Endpoint:***

.. code:: bash

    Method: GET
    Type: RAW
    URL: http://{{host}}:8545/rpc

***Headers:***

+----------------+--------------------+---------------+
| Key            | Value              | Description   |
+================+====================+===============+
| Content-Type   | application/json   |               |
+----------------+--------------------+---------------+

***Body:***

.. code:: js

    {
                "jsonrpc": "2.0",
                "id": "1",
                "method": "admin_addBlack",
                "params": ["enode://9fb5d28a4f0d086521bb3824782ad8b3d982190afc839200276e926dd2661b804854e609cd95a7bbc8969f2d513aac6a74c7c839409e786697d01ceb50fb2919@210.22.171.162:30304"]
    }

6. removeBlack
~~~~~~~~~~~~~~

***Endpoint:***

.. code:: bash

    Method: GET
    Type: RAW
    URL: http://{{host}}:8545/rpc

***Headers:***

+----------------+--------------------+---------------+
| Key            | Value              | Description   |
+================+====================+===============+
| Content-Type   | application/json   |               |
+----------------+--------------------+---------------+

***Body:***

.. code:: js

    {
                "jsonrpc": "2.0",
                "id": "1",
                "method": "admin_removeBlack",
                "params": ["enode://9fb5d28a4f0d086521bb3824782ad8b3d982190afc839200276e926dd2661b804854e609cd95a7bbc8969f2d513aac6a74c7c839409e786697d01ceb50fb2919@210.22.171.162:30304"]
    }

7. stopMining
~~~~~~~~~~~~~

***Endpoint:***

.. code:: bash

    Method: GET
    Type: RAW
    URL: http://{{host}}:8545/rpc

***Headers:***

+----------------+--------------------+---------------+
| Key            | Value              | Description   |
+================+====================+===============+
| Content-Type   | application/json   |               |
+----------------+--------------------+---------------+

***Body:***

.. code:: js

    {
                "jsonrpc": "2.0",
                "id": "1",
                "method": "admin_stopMining",
                "params": ["enode://9fb5d28a4f0d086521bb3824782ad8b3d982190afc839200276e926dd2661b804854e609cd95a7bbc8969f2d513aac6a74c7c839409e786697d01ceb50fb2919@210.22.171.162:30304"]
    }

8. startMining
~~~~~~~~~~~~~~

***Endpoint:***

.. code:: bash

    Method: GET
    Type: RAW
    URL: http://{{host}}:8545/rpc

***Headers:***

+----------------+--------------------+---------------+
| Key            | Value              | Description   |
+================+====================+===============+
| Content-Type   | application/json   |               |
+----------------+--------------------+---------------+

***Body:***

.. code:: js

    {
                "jsonrpc": "2.0",
                "id": "1",
                "method": "admin_startMining",
                "params": []
    }

9. Mining
~~~~~~~~~

***Endpoint:***

.. code:: bash

    Method: GET
    Type: RAW
    URL: http://{{host}}:8545/rpc

***Headers:***

+----------------+--------------------+---------------+
| Key            | Value              | Description   |
+================+====================+===============+
| Content-Type   | application/json   |               |
+----------------+--------------------+---------------+

***Body:***

.. code:: js

    {
                "jsonrpc": "2.0",
                "id": "1",
                "method": "admin_mining",
                "params": []
    }

10. generateMiningKey
~~~~~~~~~~~~~~~~~~~~~

***Endpoint:***

.. code:: bash

    Method: GET
    Type: RAW
    URL: http://{{host}}:8545/rpc

***Headers:***

+----------------+--------------------+---------------+
| Key            | Value              | Description   |
+================+====================+===============+
| Content-Type   | application/json   |               |
+----------------+--------------------+---------------+

***Body:***

.. code:: js

    {
                "jsonrpc": "2.0",
                "id": "1",
                "method": "admin_generateMiningKey",
                "params": ["0xa04358d378cf97a933eb09b6014f4f118378e9f4"]
    }

11. isPackerEnable
~~~~~~~~~~~~~~~~~~

***Endpoint:***

.. code:: bash

    Method: GET
    Type: RAW
    URL: http://{{host}}:8545/rpc

***Headers:***

+----------------+--------------------+---------------+
| Key            | Value              | Description   |
+================+====================+===============+
| Content-Type   | application/json   |               |
+----------------+--------------------+---------------+

***Body:***

.. code:: js

    {
                "jsonrpc": "2.0",
                "id": "1",
                "method": "admin_isPackerEnable",
                "params": []
    }

12. stopPacking
~~~~~~~~~~~~~~~

***Endpoint:***

.. code:: bash

    Method: GET
    Type: RAW
    URL: http://{{host}}:8545/rpc

***Headers:***

+----------------+--------------------+---------------+
| Key            | Value              | Description   |
+================+====================+===============+
| Content-Type   | application/json   |               |
+----------------+--------------------+---------------+

***Body:***

.. code:: js

    {
                "jsonrpc": "2.0",
                "id": "1",
                "method": "admin_stopPacking",
                "params": []
    }

13. startPacking
~~~~~~~~~~~~~~~~

***Endpoint:***

.. code:: bash

    Method: GET
    Type: RAW
    URL: http://{{host}}:8545/rpc

***Headers:***

+----------------+--------------------+---------------+
| Key            | Value              | Description   |
+================+====================+===============+
| Content-Type   | application/json   |               |
+----------------+--------------------+---------------+

***Body:***

.. code:: js

    {
                "jsonrpc": "2.0",
                "id": "1",
                "method": "admin_startPacking",
                "params": [1]
    }

14. isPacking
~~~~~~~~~~~~~

***Endpoint:***

.. code:: bash

    Method: GET
    Type: RAW
    URL: http://{{host}}:8545/rpc

***Headers:***

+----------------+--------------------+---------------+
| Key            | Value              | Description   |
+================+====================+===============+
| Content-Type   | application/json   |               |
+----------------+--------------------+---------------+

***Body:***

.. code:: js

    {
                "jsonrpc": "2.0",
                "id": "1",
                "method": "admin_isPacking",
                "params": []
    }

ftl
---

1. addPeer
~~~~~~~~~~

***Endpoint:***

.. code:: bash

    Method: GET
    Type: RAW
    URL: http://{{host}}:8545/rpc

***Headers:***

+----------------+--------------------+---------------+
| Key            | Value              | Description   |
+================+====================+===============+
| Content-Type   | application/json   |               |
+----------------+--------------------+---------------+

***Body:***

.. code:: js

    {
                "jsonrpc": "2.0",
                "id": "1",
                "method": "ftl_headBlock",
                "params": []
    }

2. genesis
~~~~~~~~~~

***Endpoint:***

.. code:: bash

    Method: GET
    Type: RAW
    URL: http://{{host}}:8545/rpc

***Headers:***

+----------------+--------------------+---------------+
| Key            | Value              | Description   |
+================+====================+===============+
| Content-Type   | application/json   |               |
+----------------+--------------------+---------------+

***Body:***

.. code:: js

    {
                "jsonrpc": "2.0",
                "id": "1",
                "method": "ftl_genesis",
                "params": []
    }

3. getBlock
~~~~~~~~~~~

***Endpoint:***

.. code:: bash

    Method: GET
    Type: RAW
    URL: http://{{host}}:8545/rpc

***Headers:***

+----------------+--------------------+---------------+
| Key            | Value              | Description   |
+================+====================+===============+
| Content-Type   | application/json   |               |
+----------------+--------------------+---------------+

***Body:***

.. code:: js

    {
                "jsonrpc": "2.0",
                "id": "1",
                "method": "ftl_getBlock",
                "params": ["0xd1c0f4f8e1ef3fb27bc19a3d0641f2e28cc61689340b10f73b3fdc65d0955fdf"]
    }

4. getBlockByHeight
~~~~~~~~~~~~~~~~~~~

***Endpoint:***

.. code:: bash

    Method: GET
    Type: RAW
    URL: http://{{host}}:8545/rpc

***Headers:***

+----------------+--------------------+---------------+
| Key            | Value              | Description   |
+================+====================+===============+
| Content-Type   | application/json   |               |
+----------------+--------------------+---------------+

***Body:***

.. code:: js

    {
                "jsonrpc": "2.0",
                "id": "1",
                "method": "ftl_getBlockByHeight",
                "params": ["0x2"]
    }

5. blockHeight
~~~~~~~~~~~~~~

***Endpoint:***

.. code:: bash

    Method: GET
    Type: RAW
    URL: http://{{host}}:8545/rpc

***Headers:***

+----------------+--------------------+---------------+
| Key            | Value              | Description   |
+================+====================+===============+
| Content-Type   | application/json   |               |
+----------------+--------------------+---------------+

***Body:***

.. code:: js

    {
                "jsonrpc": "2.0",
                "id": "1",
                "method": "ftl_blockHeight",
                "params": []
    }

6. getBackwardBlocks
~~~~~~~~~~~~~~~~~~~~

***Endpoint:***

.. code:: bash

    Method: GET
    Type: RAW
    URL: http://{{host}}:8545/rpc

***Headers:***

+----------------+--------------------+---------------+
| Key            | Value              | Description   |
+================+====================+===============+
| Content-Type   | application/json   |               |
+----------------+--------------------+---------------+

***Body:***

.. code:: js

    {
                "jsonrpc": "2.0",
                "id": "1",
                "method": "ftl_getBackwardBlocks",
                "params": ["0xd1c0f4f8e1ef3fb27bc19a3d0641f2e28cc61689340b10f73b3fdc65d0955fdf", 2]
    }

7. getAncestorBlocks
~~~~~~~~~~~~~~~~~~~~

***Endpoint:***

.. code:: bash

    Method: GET
    Type: RAW
    URL: http://{{host}}:8545/rpc

***Headers:***

+----------------+--------------------+---------------+
| Key            | Value              | Description   |
+================+====================+===============+
| Content-Type   | application/json   |               |
+----------------+--------------------+---------------+

***Body:***

.. code:: js

    {
                "jsonrpc": "2.0",
                "id": "1",
                "method": "ftl_getAncestorBlocks",
                "params": ["0xd1c0f4f8e1ef3fb27bc19a3d0641f2e28cc61689340b10f73b3fdc65d0955fdf", 2]
    }

8. getDescendantBlocks
~~~~~~~~~~~~~~~~~~~~~~

***Endpoint:***

.. code:: bash

    Method: GET
    Type: RAW
    URL: http://{{host}}:8545/rpc

***Headers:***

+----------------+--------------------+---------------+
| Key            | Value              | Description   |
+================+====================+===============+
| Content-Type   | application/json   |               |
+----------------+--------------------+---------------+

***Body:***

.. code:: js

    {
                "jsonrpc": "2.0",
                "id": "1",
                "method": "ftl_getDescendantBlocks",
                "params": ["0xd1c0f4f8e1ef3fb27bc19a3d0641f2e28cc61689340b10f73b3fdc65d0955fdf", 4]
    }

9. getNearbyBlocks
~~~~~~~~~~~~~~~~~~

***Endpoint:***

.. code:: bash

    Method: GET
    Type: RAW
    URL: http://{{host}}:8545/rpc

***Headers:***

+----------------+--------------------+---------------+
| Key            | Value              | Description   |
+================+====================+===============+
| Content-Type   | application/json   |               |
+----------------+--------------------+---------------+

***Body:***

.. code:: js

    {
                "jsonrpc": "2.0",
                "id": "1",
                "method": "ftl_getNearbyBlocks",
                "params": ["0xd1c0f4f8e1ef3fb27bc19a3d0641f2e28cc61689340b10f73b3fdc65d0955fdf", 4]
    }

10. getBalance
~~~~~~~~~~~~~~

***Endpoint:***

.. code:: bash

    Method: GET
    Type: RAW
    URL: http://{{host}}:8545/rpc

***Headers:***

+----------------+--------------------+---------------+
| Key            | Value              | Description   |
+================+====================+===============+
| Content-Type   | application/json   |               |
+----------------+--------------------+---------------+

***Body:***

.. code:: js

    {
                "jsonrpc": "2.0",
                "id": "1",
                "method": "ftl_getBalance",
                "params": ["0xa04358d378cf97a933eb09b6014f4f118378e9f4", "0xd1c0f4f8e1ef3fb27bc19a3d0641f2e28cc61689340b10f73b3fdc65d0955fdf"]
    }

11. getStorageAt UNDO
~~~~~~~~~~~~~~~~~~~~~

***Endpoint:***

.. code:: bash

    Method: GET
    Type: RAW
    URL: http://{{host}}:8545/rpc

***Headers:***

+----------------+--------------------+---------------+
| Key            | Value              | Description   |
+================+====================+===============+
| Content-Type   | application/json   |               |
+----------------+--------------------+---------------+

***Body:***

.. code:: js

    {
                "jsonrpc": "2.0",
                "id": "1",
                "method": "ftl_getStorageAt",
                "params": ["0xa04358d378cf97a933eb09b6014f4f118378e9f4", "0xd1c0f4f8e1ef3fb27bc19a3d0641f2e28cc61689340b10f73b3fdc65d0955fdf"]
    }

12. getCode
~~~~~~~~~~~

***Endpoint:***

.. code:: bash

    Method: GET
    Type: RAW
    URL: http://{{host}}:8545/rpc

***Headers:***

+----------------+--------------------+---------------+
| Key            | Value              | Description   |
+================+====================+===============+
| Content-Type   | application/json   |               |
+----------------+--------------------+---------------+

***Body:***

.. code:: js

    {
                "jsonrpc": "2.0",
                "id": "1",
                "method": "ftl_getCode",
                "params": ["0xa04358d378cf97a933eb09b6014f4f118378e9f4", "0xd1c0f4f8e1ef3fb27bc19a3d0641f2e28cc61689340b10f73b3fdc65d0955fdf"]
    }

13. getContractOwner
~~~~~~~~~~~~~~~~~~~~

***Endpoint:***

.. code:: bash

    Method: GET
    Type: RAW
    URL: http://{{host}}:8545/rpc

***Headers:***

+----------------+--------------------+---------------+
| Key            | Value              | Description   |
+================+====================+===============+
| Content-Type   | application/json   |               |
+----------------+--------------------+---------------+

***Body:***

.. code:: js

    {
                "jsonrpc": "2.0",
                "id": "1",
                "method": "ftl_getContractOwner",
                "params": ["0xa04358d378cf97a933eb09b6014f4f118378e9f4"]
    }

14. getLogs UNDO
~~~~~~~~~~~~~~~~

***Endpoint:***

.. code:: bash

    Method: GET
    Type: RAW
    URL: http://{{host}}:8545/rpc

***Headers:***

+----------------+--------------------+---------------+
| Key            | Value              | Description   |
+================+====================+===============+
| Content-Type   | application/json   |               |
+----------------+--------------------+---------------+

***Body:***

.. code:: js

    {
                "jsonrpc": "2.0",
                "id": "1",
                "method": "ftl_getContractOwner",
                "params": ["0xa04358d378cf97a933eb09b6014f4f118378e9f4"]
    }

15. coinbase
~~~~~~~~~~~~

***Endpoint:***

.. code:: bash

    Method: GET
    Type: RAW
    URL: http://{{host}}:8545/rpc

***Headers:***

+----------------+--------------------+---------------+
| Key            | Value              | Description   |
+================+====================+===============+
| Content-Type   | application/json   |               |
+----------------+--------------------+---------------+

***Body:***

.. code:: js

    {
                "jsonrpc": "2.0",
                "id": "1",
                "method": "ftl_coinbase",
                "params": ["0xa04358d378cf97a933eb09b6014f4f118378e9f4"]
    }

16. protocolVersion
~~~~~~~~~~~~~~~~~~~

***Endpoint:***

.. code:: bash

    Method: GET
    Type: RAW
    URL: http://{{host}}:8545/rpc

***Headers:***

+----------------+--------------------+---------------+
| Key            | Value              | Description   |
+================+====================+===============+
| Content-Type   | application/json   |               |
+----------------+--------------------+---------------+

***Body:***

.. code:: js

    {
                "jsonrpc": "2.0",
                "id": "1",
                "method": "ftl_protocolVersion",
                "params": []
    }

17. chainId
~~~~~~~~~~~

***Endpoint:***

.. code:: bash

    Method: GET
    Type: RAW
    URL: http://{{host}}:8545/rpc

***Headers:***

+----------------+--------------------+---------------+
| Key            | Value              | Description   |
+================+====================+===============+
| Content-Type   | application/json   |               |
+----------------+--------------------+---------------+

***Body:***

.. code:: js

    {
                "jsonrpc": "2.0",
                "id": "1",
                "method": "ftl_chainId",
                "params": []
    }

net
---

1. listening
~~~~~~~~~~~~

***Endpoint:***

.. code:: bash

    Method: GET
    Type: RAW
    URL: http://{{host}}:8545/rpc

***Headers:***

+----------------+--------------------+---------------+
| Key            | Value              | Description   |
+================+====================+===============+
| Content-Type   | application/json   |               |
+----------------+--------------------+---------------+

***Body:***

.. code:: js

    {
                "jsonrpc": "2.0",
                "id": "1",
                "method": "net_listening",
                "params": []
    }

2. peerCount UNWORK
~~~~~~~~~~~~~~~~~~~

***Endpoint:***

.. code:: bash

    Method: GET
    Type: RAW
    URL: http://{{host}}:8545/rpc

***Headers:***

+----------------+--------------------+---------------+
| Key            | Value              | Description   |
+================+====================+===============+
| Content-Type   | application/json   |               |
+----------------+--------------------+---------------+

***Body:***

.. code:: js

    {
                "jsonrpc": "2.0",
                "id": "1",
                "method": "net_peerCount",
                "params": []
    }

3. peers UNWORK
~~~~~~~~~~~~~~~

***Endpoint:***

.. code:: bash

    Method: GET
    Type: RAW
    URL: http://{{host}}:8545/rpc

***Headers:***

+----------------+--------------------+---------------+
| Key            | Value              | Description   |
+================+====================+===============+
| Content-Type   | application/json   |               |
+----------------+--------------------+---------------+

***Body:***

.. code:: js

    {
                "jsonrpc": "2.0",
                "id": "1",
                "method": "net_peers",
                "params": []
    }

4. nodeInfo
~~~~~~~~~~~

***Endpoint:***

.. code:: bash

    Method: GET
    Type: RAW
    URL: http://{{host}}:8545/rpc

***Headers:***

+----------------+--------------------+---------------+
| Key            | Value              | Description   |
+================+====================+===============+
| Content-Type   | application/json   |               |
+----------------+--------------------+---------------+

***Body:***

.. code:: js

    {
                "jsonrpc": "2.0",
                "id": "1",
                "method": "net_nodeInfo",
                "params": []
    }

5. nodeInfo Copy
~~~~~~~~~~~~~~~~

***Endpoint:***

.. code:: bash

    Method: GET
    Type: RAW
    URL: http://{{host}}:8545/rpc

***Headers:***

+----------------+--------------------+---------------+
| Key            | Value              | Description   |
+================+====================+===============+
| Content-Type   | application/json   |               |
+----------------+--------------------+---------------+

***Body:***

.. code:: js

    {
                "jsonrpc": "2.0",
                "id": "1",
                "method": "net_version",
                "params": []
    }

packer
------

1. getTxPackageByHash
~~~~~~~~~~~~~~~~~~~~~

***Endpoint:***

.. code:: bash

    Method: GET
    Type: RAW
    URL: http://{{host}}:8545/rpc

***Headers:***

+----------------+--------------------+---------------+
| Key            | Value              | Description   |
+================+====================+===============+
| Content-Type   | application/json   |               |
+----------------+--------------------+---------------+

***Body:***

.. code:: js

    {
                "jsonrpc": "2.0",
                "id": "1",
                "method": "pack_getTxPackageByHash",
                "params": ["0xfda689596a9a0f1e184b972b3ca2601f03c0d52abf1db7604356d1eec22f54f4"]
    }

2. sendRawTransaction UNDO
~~~~~~~~~~~~~~~~~~~~~~~~~~

***Endpoint:***

.. code:: bash

    Method: GET
    Type: RAW
    URL: http://{{host}}:8545/rpc

***Headers:***

+----------------+--------------------+---------------+
| Key            | Value              | Description   |
+================+====================+===============+
| Content-Type   | application/json   |               |
+----------------+--------------------+---------------+

***Body:***

.. code:: js

    {
                "jsonrpc": "2.0",
                "id": "1",
                "method": "pack_getTxPackageByHash",
                "params": ["0xfda689596a9a0f1e184b972b3ca2601f03c0d52abf1db7604356d1eec22f54f4"]
    }

tx\_pool
--------

1. getTxPackageByHash UNDO
~~~~~~~~~~~~~~~~~~~~~~~~~~

***Endpoint:***

.. code:: bash

    Method: GET
    Type: RAW
    URL: http://{{host}}:8545/rpc

***Headers:***

+----------------+--------------------+---------------+
| Key            | Value              | Description   |
+================+====================+===============+
| Content-Type   | application/json   |               |
+----------------+--------------------+---------------+

***Body:***

.. code:: js

    {
                "jsonrpc": "2.0",
                "id": "1",
                "method": "txpool_getTransactionByHash",
                "params": ["0xfda689596a9a0f1e184b972b3ca2601f03c0d52abf1db7604356d1eec22f54f4"]
    }

2. content
~~~~~~~~~~

***Endpoint:***

.. code:: bash

    Method: GET
    Type: RAW
    URL: http://{{host}}:8545/rpc

***Headers:***

+----------------+--------------------+---------------+
| Key            | Value              | Description   |
+================+====================+===============+
| Content-Type   | application/json   |               |
+----------------+--------------------+---------------+

***Body:***

.. code:: js

    {
                "jsonrpc": "2.0",
                "id": "1",
                "method": "txpool_content",
                "params": []
    }

3. status
~~~~~~~~~

***Endpoint:***

.. code:: bash

    Method: GET
    Type: RAW
    URL: http://{{host}}:8545/rpc

***Headers:***

+----------------+--------------------+---------------+
| Key            | Value              | Description   |
+================+====================+===============+
| Content-Type   | application/json   |               |
+----------------+--------------------+---------------+

***Body:***

.. code:: js

    {
                "jsonrpc": "2.0",
                "id": "1",
                "method": "txpool_status",
                "params": []
    }

4. inspenct
~~~~~~~~~~~

***Endpoint:***

.. code:: bash

    Method: GET
    Type: RAW
    URL: http://{{host}}:8545/rpc

***Headers:***

+----------------+--------------------+---------------+
| Key            | Value              | Description   |
+================+====================+===============+
| Content-Type   | application/json   |               |
+----------------+--------------------+---------------+

***Body:***

.. code:: js

    {
                "jsonrpc": "2.0",
                "id": "1",
                "method": "txpool_inspect",
                "params": []
    }

5. getTransactionNonce
~~~~~~~~~~~~~~~~~~~~~~

***Endpoint:***

.. code:: bash

    Method: GET
    Type: RAW
    URL: http://{{host}}:8545/rpc

***Headers:***

+----------------+--------------------+---------------+
| Key            | Value              | Description   |
+================+====================+===============+
| Content-Type   | application/json   |               |
+----------------+--------------------+---------------+

***Body:***

.. code:: js

    {
                "jsonrpc": "2.0",
                "id": "1",
                "method": "txpool_getTransactionNonce",
                "params": ["0xf13376df4b6e043d0e3e6d6561272875aa287294"]
    }

6. getBlockTransactionCountByHash
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

***Endpoint:***

.. code:: bash

    Method: GET
    Type: RAW
    URL: http://{{host}}:8545/rpc

***Headers:***

+----------------+--------------------+---------------+
| Key            | Value              | Description   |
+================+====================+===============+
| Content-Type   | application/json   |               |
+----------------+--------------------+---------------+

***Body:***

.. code:: js

    {
                "jsonrpc": "2.0",
                "id": "1",
                "method": "txpool_getBlockTransactionCountByHash",
                "params": ["0xd1c0f4f8e1ef3fb27bc19a3d0641f2e28cc61689340b10f73b3fdc65d0955fdf"]
    }

7. SendRawTransaction UNDO
~~~~~~~~~~~~~~~~~~~~~~~~~~

***Endpoint:***

.. code:: bash

    Method: GET
    Type: RAW
    URL: http://{{host}}:8545/rpc

***Headers:***

+----------------+--------------------+---------------+
| Key            | Value              | Description   |
+================+====================+===============+
| Content-Type   | application/json   |               |
+----------------+--------------------+---------------+

***Body:***

.. code:: js

    {
                "jsonrpc": "2.0",
                "id": "1",
                "method": "txpool_SendRawTransaction",
                "params": ["0xd1c0f4f8e1ef3fb27bc19a3d0641f2e28cc61689340b10f73b3fdc65d0955fdf"]
    }

8. encodeAction
~~~~~~~~~~~~~~~

***Endpoint:***

.. code:: bash

    Method: GET
    Type: RAW
    URL: http://{{host}}:8545/rpc

***Headers:***

+----------------+--------------------+---------------+
| Key            | Value              | Description   |
+================+====================+===============+
| Content-Type   | application/json   |               |
+----------------+--------------------+---------------+

***Body:***

.. code:: js

    {
                "jsonrpc": "2.0",
                "id": "1",
                "method": "txpool_encodeAction",
                "params": ["0xd1c0f4f8e1ef3fb27bc19a3d0641f2e28cc61689340b10f73b3fdc65d0955fdf", "sdada", "sadasd"]
    }

9. pendingTransactions
~~~~~~~~~~~~~~~~~~~~~~

***Endpoint:***

.. code:: bash

    Method: GET
    Type: RAW
    URL: http://{{host}}8545/rpc

***Headers:***

+----------------+--------------------+---------------+
| Key            | Value              | Description   |
+================+====================+===============+
| Content-Type   | application/json   |               |
+----------------+--------------------+---------------+

***Body:***

.. code:: js

    {
                "jsonrpc": "2.0",
                "id": "1",
                "method": "txpool_pendingTransactions",
                "params": []
    }

10. gasPrice
~~~~~~~~~~~~

***Endpoint:***

.. code:: bash

    Method: GET
    Type: RAW
    URL: http://{{host}}:8545/rpc

***Headers:***

+----------------+--------------------+---------------+
| Key            | Value              | Description   |
+================+====================+===============+
| Content-Type   | application/json   |               |
+----------------+--------------------+---------------+

***Body:***

.. code:: js

    {
                "jsonrpc": "2.0",
                "id": "1",
                "method": "txpool_gasPrice",
                "params": []
    }

--------------

`Back to top <#fractal_rpc>`__ > Made with ♥ by
`thedevsaddam <https://github.com/thedevsaddam>`__ \| Generated at:
2019-08-22 10:50:55 by
`docgen <https://github.com/thedevsaddam/docgen>`__
