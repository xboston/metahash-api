# MetaHash API
- [MetaHash API](#metahash-api)
  * [Sources](#sources)
  * [Get data](#get-data)
    + [fetch-balance](#fetch-balance)
    + [fetch-balances](#fetch-balances)
    + [fetch-history](#fetch-history)
    + [get-tx](#get-tx)
    + [get-block-by-hash](#get-block-by-hash)
    + [get-block-by-number](#get-block-by-number)
    + [get-last-txs](#get-last-txs)
    + [get-blocks](#get-blocks)
    + [get-dump-block-by-number](#get-dump-block-by-number)
    + [get-dump-block-by-hash](#get-dump-block-by-hash)
    + [get-count-blocks](#get-count-blocks)
  * [Send data](#send-data)
    + [mhc_send](#mhc_send)

## Sources

 - https://github.com/metahashorg/metahash-fullnode-client/wiki/Usage
 - https://github.com/metahashorg/metahash-fullnode-client/blob/master/src/task_handlers/task_handlers.cpp#L29



## Get data
POST http://tor.net-main.metahashnetwork.com:5795

### fetch-balance
```JSON
{
    "id": 1,
    "version": "1.0.0",
    "method": "fetch-balance",
    "params":{
      "address":"0x00fa2a5279f8f0fd2f0f9d3280ad70403f01f9d62f52373833"
    }
}
--->
{
  "id": 1,
  "result": {
    "address": "0x00fa2a5279f8f0fd2f0f9d3280ad70403f01f9d62f52373833",
    "received": 51287778416,
    "spent": 43232068457,
    "count_received": 2395,
    "count_spent": 148,
    "count_txs": 2523,
    "block_number": 529862,
    "currentBlock": 529992,
    "hash": "6532614542110822063",
    "countDelegatedOps": 23,
    "delegate": 32312000000,
    "undelegate": 32212000000,
    "delegated": 0,
    "undelegated": 0,
    "reserved": 0,
    "countForgedOps": 40,
    "forged": 449453930
  }
}
```

### fetch-balances
```JSON
{
    "id": 1,
    "jsonrpc": "2.0",
    "method": "fetch-balances",
    "params": {
        "addresses": [
            "0x00fa2a5279f8f0fd2f0f9d3280ad70403f01f9d62f52373833",
            "0x0039f42ad734606d250ea0b0151d4aeab6b4edc6587c4b27ef",
            "0x005b891007c2000fee08e085beb91494f1d3753eb8eee354f0"
        ]
    }
}
--->
{
    "id": 1,
    "result": [
        {
            "address": "0x00fa2a5279f8f0fd2f0f9d3280ad70403f01f9d62f52373833",
            "received": 59762397568,
            "spent": 59713636256,
            "count_received": 2572,
            "count_spent": 270,
            "count_txs": 2813,
            "block_number": 960249,
            "currentBlock": 962496,
            "hash": "7728889007402776173",
            "countDelegatedOps": 39,
            "delegate": 39914674162,
            "undelegate": 34928750583,
            "delegated": 0,
            "undelegated": 0,
            "reserved": 0,
            "countForgedOps": 124,
            "forged": 892444488
        },
        {
            "address": "0x0039f42ad734606d250ea0b0151d4aeab6b4edc6587c4b27ef",
            "received": 116202298002001,
            "spent": 106395002269262,
            "count_received": 96,
            "count_spent": 6327,
            "count_txs": 6423,
            "block_number": 962304,
            "currentBlock": 962496,
            "hash": "401906331725536639"
        },
        {
            "address": "0x005b891007c2000fee08e085beb91494f1d3753eb8eee354f0",
            "received": 11756733334374,
            "spent": 6597005212439,
            "count_received": 413,
            "count_spent": 213,
            "count_txs": 626,
            "block_number": 962347,
            "currentBlock": 962496,
            "hash": "4842209927186827818"
        }
    ]
}
```

### fetch-history
```JSON
{
    "id": 1,
    "version": "1.0.0",
    "method": "fetch-history",
    "params":{
      "address":"0x00fa2a5279f8f0fd2f0f9d3280ad70403f01f9d62f52373833",
      "beginTx": 1,
      "countTxs": 2
    }
}
--->
{
  "id": 1,
  "result": [
    {
      "from": "0x00fa2a5279f8f0fd2f0f9d3280ad70403f01f9d62f52373833",
      "to": "0x00fa2a5279f8f0fd2f0f9d3280ad70403f01f9d62f52373833",
      "value": 0,
      "transaction": "2ece21e8906cc2a7824da47c528e6d07f915417b0aeba17ca8a78b4875e420c5",
      "data": "30820120300d06092a864886f70d01010105000382010d00308201080282010100f9ffed17e442969fb1dad68d7ec537d51bde4ae4692281375d5bf4cd7ae10003127eec436da1580af71c5a2ed7939366af1970e838875f6056713fa8dc6db612013ba97df2ae6091e6951b73b41c974df33421b1156b3fde78c47066452f23d79757283b7cae29e88d81fdac7a62ca3ab700664292d5bb4d9ed61758c6aa96e7ae947c95541c43066832ad691b4c5715dfcd323be0fbf8cbf6982014da78487c2db6dfa2e1ce6a8f51deca17f4b64a01b23486024489851bce00c279af0a2ac8e512af402c36bb953a1dda9371e9a3ff32ef4c63676b936efc65b665d8682ee78c807ecba67f3346fb3dead54ba12cca59027708beb757c9281839fa8a86cca5020111",
      "timestamp": 1557233807,
      "type": "block",
      "blockNumber": 529380,
      "signature": "3045022052484e72d083465a58217cc5effc741c2a423cdb6db5bb19785ec7c4bc8b099002210083215679d55591f548b5431453d0cbd0a865169556801bb884f78ebc0288034d",
      "publickey": "3059301306072a8648ce3d020106082a8648ce3d03010703420004e335bc51937a9e49b45ed3065b2bc9bdd3fd27c360c3a0cffc2a0c32e371cdcd600c97e19f38c224d62832d886f02cc5ed25fa5e7c5e0e10178d25f800ec3685",
      "fee": 350,
      "realFee": 235,
      "nonce": 147,
      "intStatus": 20,
      "status": "ok"
    },
    {
      "from": "0x004f9dde31dd62efd565491fa0fc5cfe0846a8f6f806771a37",
      "to": "0x00fa2a5279f8f0fd2f0f9d3280ad70403f01f9d62f52373833",
      "value": 100000,
      "transaction": "9f3aea97caeba859632a4dbb8288f76e6f9b21b7f9ab96e7ad3ba04a448142a0",
      "data": "3332",
      "timestamp": 1557217125,
      "type": "block",
      "blockNumber": 527449,
      "signature": "304502207924ea9ff9173720923f1dbbdc0924931001b8071ae5ede8dc5ce7e1fade45a9022100e05b6b6ba5289212fab11431125e8b73426a9b2a0023cd8b561e797672b95a4f",
      "publickey": "3059301306072a8648ce3d020106082a8648ce3d03010703420004ee935478aad3f55cb673e1ea1feb865f7a0e2ba18cf3d89e45493f853126bae5e4b25362a1a8c90d10ce04bd774235c5dd972bd08c17a8e7af00f59bcbd446c7",
      "fee": 4,
      "realFee": 0,
      "nonce": 85,
      "intStatus": 20,
      "status": "ok"
    }
  ]
}
```

### get-tx
```JSON
{
    "id": 1,
    "version": "1.0.0",
    "method": "get-tx",
    "params":{
      "hash":"4be8202c2ae33d9541b36691f0d9d26b4c7560128e160867a13d7404f28cfa4b"
    }
}
--->
{
  "id": 1,
  "result": {
    "transaction": {
      "from": "0x0000496c628660f91a19f04d41c497353d749fda793f86a844",
      "to": "0x00fa2a5279f8f0fd2f0f9d3280ad70403f01f9d62f52373833",
      "value": 11959389,
      "transaction": "4be8202c2ae33d9541b36691f0d9d26b4c7560128e160867a13d7404f28cfa4b",
      "data": "2333206765746d657461686173682e636f6d20626f6e757320726577617264",
      "timestamp": 1557189914,
      "type": "block",
      "blockNumber": 522786,
      "signature": "3045022100bdb41e082c088f1e0985c745b2555604765ad994a844a59600ac16ccdcfb2ddf02206fde3d477db615f9dd6ee49eba76a5de50b6c6a37670e7fc453b24a3789111d8",
      "publickey": "3059301306072a8648ce3d020106082a8648ce3d030107034200045f54abaebe038e4aba608a730a0df3b11ef13062add93fc119f85283076f247a9e8a468b3e9afcbb3a8b60b18a8435fe2728329cab3ce7ca37a9fad78e2c43df",
      "fee": 31,
      "realFee": 0,
      "nonce": 6567,
      "intStatus": 20,
      "status": "ok"
    },
    "countBlocks": 530005,
    "knownBlocks": 530005
  }
}
```


### get-block-by-hash
```JSON
{
    "id": 1,
    "version": "1.0.0",
    "method": "get-block-by-hash",
    "params":{
      "hash":"49a840968be1a3c0449a6d7946fd021ce2746006ff5b855fdc0623669833f5e7",
      "type": 1, // 0-4
      "beginTx": 1,
      "countTxs": 5
    }
}
--->
{
  "id": 1,
  "result": {
    "type": "block",
    "hash": "49a840968be1a3c0449a6d7946fd021ce2746006ff5b855fdc0623669833f5e7",
    "prev_hash": "c89b1d6d72692cb2af52df78261818b4472ad34ee103696e02c636f2f4750314",
    "tx_hash": "bbab4aeeb515b5e5962a2a292070f6ae5e247d8e5314a32b43ade30101881748",
    "number": 475345,
    "timestamp": 1556837036,
    "count_txs": 29,
    "sign": "c89b1d6d72692cb2af52df78261818b4472ad34ee103696e02c636f2f4750314",
    "size": 5989,
    "fileName": "/data/metahash/20190503.blk",
    "signatures": [
      {
        "from": "0x0028dd1ca2951fe554ef526d60ff55a64776ee5e033120ca91",
        "to": "0x0028dd1ca2951fe554ef526d60ff55a64776ee5e033120ca91",
        "value": 0,
        "transaction": "8b82217fca311097a1bf32fce7506a991fe0b1ce73cf4a22dfb9279289d104e3",
        "data": "49a840968be1a3c0449a6d7946fd021ce2746006ff5b855fdc0623669833f5e7",
        "timestamp": 1556837036,
        "type": "block",
        "blockNumber": 0,
        "signature": "3045022100eb64fc60aee22bd95b4f393a95d225239015646e63e9d454b40a610227fa31df022059a2d6e999cc8c7ad1feb46b95164cd8c07ba7b86bad5625b62d6602a9b627dc",
        "publickey": "3059301306072a8648ce3d020106082a8648ce3d0301070342000444f13813e9688c4c41b1583b3241eb1efe9139de592b387ea27b5259e054db2acd2a3b72843876bd1b60f67ea73df14943ba3cc2cbf4b48d5a133e7a1233cccc",
        "fee": 0,
        "realFee": 0,
        "nonce": 462266,
        "intStatus": 1,
        "status": "ok"
      },
      // ... 7 signatures
    ],
    "txs": [
      "9510a3aafba0f0671c396b8925678b4a43a98ef67b77e0b300f50d9a6439ec01",
      "8d592d0c68f6a8e09636b00c896c8be537045247fb2ee193e9c32eeac7cbf243",
      "687ebd3c23d0af4fd905900aa0e580c4b33a1f6af30f01a6c3bd3ca54ed701c2",
      "63f26e09508a7c194f38f7a4340a40954a672f660b9098bfcebb31deb7101736",
      "b17cbcf0b23c77eca484f6883254e6a24d21e6da4cc5a2ee72a3dd0a3824ba6e"
    ]
  }
}
```


### get-block-by-number
```JSON
{
    "id": 1,
    "version": "1.0.0",
    "method": "get-block-by-number",
    "params":{
      "number": 475345,
      "type": 1, // 0-4
      "beginTx": 1,
      "countTxs": 5
    }
}
--->
{
  "id": 1,
  "result": {
    "type": "block",
    "hash": "49a840968be1a3c0449a6d7946fd021ce2746006ff5b855fdc0623669833f5e7",
    "prev_hash": "c89b1d6d72692cb2af52df78261818b4472ad34ee103696e02c636f2f4750314",
    "tx_hash": "bbab4aeeb515b5e5962a2a292070f6ae5e247d8e5314a32b43ade30101881748",
    "number": 475345,
    "timestamp": 1556837036,
    "count_txs": 29,
    "sign": "c89b1d6d72692cb2af52df78261818b4472ad34ee103696e02c636f2f4750314",
    "size": 5989,
    "fileName": "/data/metahash/20190503.blk",
    "signatures": [
      {
        "from": "0x0028dd1ca2951fe554ef526d60ff55a64776ee5e033120ca91",
        "to": "0x0028dd1ca2951fe554ef526d60ff55a64776ee5e033120ca91",
        "value": 0,
        "transaction": "8b82217fca311097a1bf32fce7506a991fe0b1ce73cf4a22dfb9279289d104e3",
        "data": "49a840968be1a3c0449a6d7946fd021ce2746006ff5b855fdc0623669833f5e7",
        "timestamp": 1556837036,
        "type": "block",
        "blockNumber": 0,
        "signature": "3045022100eb64fc60aee22bd95b4f393a95d225239015646e63e9d454b40a610227fa31df022059a2d6e999cc8c7ad1feb46b95164cd8c07ba7b86bad5625b62d6602a9b627dc",
        "publickey": "3059301306072a8648ce3d020106082a8648ce3d0301070342000444f13813e9688c4c41b1583b3241eb1efe9139de592b387ea27b5259e054db2acd2a3b72843876bd1b60f67ea73df14943ba3cc2cbf4b48d5a133e7a1233cccc",
        "fee": 0,
        "realFee": 0,
        "nonce": 462266,
        "intStatus": 1,
        "status": "ok"
      },
      // ... 7 signatures
    ],
    "txs": [
      "9510a3aafba0f0671c396b8925678b4a43a98ef67b77e0b300f50d9a6439ec01",
      "8d592d0c68f6a8e09636b00c896c8be537045247fb2ee193e9c32eeac7cbf243",
      "687ebd3c23d0af4fd905900aa0e580c4b33a1f6af30f01a6c3bd3ca54ed701c2",
      "63f26e09508a7c194f38f7a4340a40954a672f660b9098bfcebb31deb7101736",
      "b17cbcf0b23c77eca484f6883254e6a24d21e6da4cc5a2ee72a3dd0a3824ba6e"
    ]
  }
}
```

### get-last-txs
```JSON
{
    "id": 1,
    "version": "1.0.0",
    "method": "get-last-txs"
}
--->
{
  "id": 1,
  "result": [
    {
      "from": "0x0028dd1ca2951fe554ef526d60ff55a64776ee5e033120ca91",
      "to": "0x0028dd1ca2951fe554ef526d60ff55a64776ee5e033120ca91",
      "value": 0,
      "transaction": "954a20c4e56096e0c63f04624276cc5c669bc50799d3d9eee6b634d8ead5e88a",
      "data": "8302512ec452e6bf018135ef19c5ba07881b8bf38f5c791d6dabe4e9a37a4e6a",
      "timestamp": 1557246215,
      "type": "block",
      "blockNumber": 530059,
      "signature": "3045022007fc1e53b372e834138b1d69029667bba9e7ae58624a2d22bd2ddfc9fd78651b022100a7bd6d864cc78daf22c08315f816f2f932976fda93ee6a2edaa89c8c2cc7c2d3",
      "publickey": "3059301306072a8648ce3d020106082a8648ce3d0301070342000444f13813e9688c4c41b1583b3241eb1efe9139de592b387ea27b5259e054db2acd2a3b72843876bd1b60f67ea73df14943ba3cc2cbf4b48d5a133e7a1233cccc",
      "fee": 0,
      "realFee": 0,
      "nonce": 516968,
      "intStatus": 1,
      "status": "ok"
    },
    //... 100 items
    {
      "from": "0x0069fce976a40fbd2c894f1fe635255fc16c80bfe17ce65f5e",
      "to": "0x0069fce976a40fbd2c894f1fe635255fc16c80bfe17ce65f5e",
      "value": 0,
      "transaction": "6be97197a6ce7a369dd87f574c568d0bf6727d2baab8226d7ef5186d4a2b6753",
      "data": "2476db45006e251dd9572e596d3b2dbfd2485deeee64a53a5fc2747f60cdbfb4",
      "timestamp": 1557246069,
      "type": "block",
      "blockNumber": 530047,
      "signature": "304502207c9c353f73e97552a8efc8956a20008a6aacd833e958a9998ee71b3be19768e2022100e51670591bcba07b281bb334cfe35091b57c8b56c0bd6028752189c468769381",
      "publickey": "3059301306072a8648ce3d020106082a8648ce3d03010703420004edd10457be891611b3905408284c527d3743217aed719cf9fe4b3337b74b8556376a0ad2bb2a997a4f681dcfca42bbfbfc4874aac7c8fff851f1f693e0986319",
      "fee": 0,
      "realFee": 0,
      "nonce": 516956,
      "intStatus": 1,
      "status": "ok"
    }
  ]
}
```

### get-blocks
```JSON
{
    "id": 1,
    "version": "1.0.0",
    "method": "get-blocks",
    "params":{
      "beginBlock":1,
      "countBlocks":5
    }
}
--->
{
  "id": 1,
  "result": [
    {
      "type": "block",
      "hash": "6bbc8ddfa25e0f5cf37f42b36720768f034369ce0ab671acba8a15401d9cd093",
      "prev_hash": "8302512ec452e6bf018135ef19c5ba07881b8bf38f5c791d6dabe4e9a37a4e6a",
      "tx_hash": "8cb0436f85825ab16e26c7fdef4aade77330f889d3273562aa334e44a79b9d57",
      "number": 530059,
      "timestamp": 1557246215,
      "count_txs": 8,
      "sign": "8302512ec452e6bf018135ef19c5ba07881b8bf38f5c791d6dabe4e9a37a4e6a",
      "size": 1912,
      "fileName": "/data/metahash/20190507.blk",
      "signatures": [
        {
          "from": "0x0028dd1ca2951fe554ef526d60ff55a64776ee5e033120ca91",
          "to": "0x0028dd1ca2951fe554ef526d60ff55a64776ee5e033120ca91",
          "value": 0,
          "transaction": "ee5ebe7b5e701c0ad06d498c333cd067e46a21a88bba959e3ce49690077293c6",
          "data": "ca932387efea77c8a9faa0a7e66b495e897196da8a735369853737630c9834b6",
          "timestamp": 1557246215,
          "type": "block",
          "blockNumber": 0,
          "signature": "3046022100da717ef7f832eb3f39c56309192ea59fd8ef672fa7dd16ab0f89859922e07410022100ad4847b067f50d0ffd5f9fad0162f0edd6c34b042b28b7f13a5274d477ede55d",
          "publickey": "3059301306072a8648ce3d020106082a8648ce3d0301070342000444f13813e9688c4c41b1583b3241eb1efe9139de592b387ea27b5259e054db2acd2a3b72843876bd1b60f67ea73df14943ba3cc2cbf4b48d5a133e7a1233cccc",
          "fee": 0,
          "realFee": 0,
          "nonce": 516967,
          "intStatus": 1,
          "status": "ok"
        },
        // ... 7 signatures
      ]
    },
    {
      "type": "block",
      "hash": "8302512ec452e6bf018135ef19c5ba07881b8bf38f5c791d6dabe4e9a37a4e6a",
      "prev_hash": "ca932387efea77c8a9faa0a7e66b495e897196da8a735369853737630c9834b6",
      "tx_hash": "615d527c08282984d4d5ce923a2b7451a2f6d0ee360e594801e2cbf7077832c8",
      "number": 530058,
      "timestamp": 1557246186,
      "count_txs": 8,
      "sign": "ca932387efea77c8a9faa0a7e66b495e897196da8a735369853737630c9834b6",
      "size": 1912,
      "fileName": "/data/metahash/20190507.blk",
      "signatures": [
        {
          "from": "0x0028dd1ca2951fe554ef526d60ff55a64776ee5e033120ca91",
          "to": "0x0028dd1ca2951fe554ef526d60ff55a64776ee5e033120ca91",
          "value": 0,
          "transaction": "dae2b65efc8cb4c62a00e9e207ea3030cb53b0e874532868c23cdcd77e757bf9",
          "data": "ecdf334cf2439b8913105be172dde30e2011dfdbb53bb79449c90e8e952471a1",
          "timestamp": 1557246186,
          "type": "block",
          "blockNumber": 0,
          "signature": "3045022100ddd068b97854ce7ee6db72ab33980c8dd52f35d704dd61aad8fa96d75ae1b935022078aeba2d2841558f54c7cf8c5149f243bee7f91b34bb12d87b64b45b10034042",
          "publickey": "3059301306072a8648ce3d020106082a8648ce3d0301070342000444f13813e9688c4c41b1583b3241eb1efe9139de592b387ea27b5259e054db2acd2a3b72843876bd1b60f67ea73df14943ba3cc2cbf4b48d5a133e7a1233cccc",
          "fee": 0,
          "realFee": 0,
          "nonce": 516966,
          "intStatus": 1,
          "status": "ok"
        },
        // ... 7 signatures
      ]
    },
    {
      "type": "block",
      "hash": "ca932387efea77c8a9faa0a7e66b495e897196da8a735369853737630c9834b6",
      "prev_hash": "ecdf334cf2439b8913105be172dde30e2011dfdbb53bb79449c90e8e952471a1",
      "tx_hash": "70c7961352abecc3301da59600968cf5abdfeb0d0aa8778a3e6231bf717c5236",
      "number": 530057,
      "timestamp": 1557246177,
      "count_txs": 8,
      "sign": "ecdf334cf2439b8913105be172dde30e2011dfdbb53bb79449c90e8e952471a1",
      "size": 1911,
      "fileName": "/data/metahash/20190507.blk",
      "signatures": [
        {
          "from": "0x0028dd1ca2951fe554ef526d60ff55a64776ee5e033120ca91",
          "to": "0x0028dd1ca2951fe554ef526d60ff55a64776ee5e033120ca91",
          "value": 0,
          "transaction": "c98bc63b6f5922b5bb1c369406e6d8c885be3e09fa61ed1ccc12197aa2791791",
          "data": "12c6d76cf9456c12728093f0f1ac278d1ee040c7b5ee2fd169539047d2284f30",
          "timestamp": 1557246177,
          "type": "block",
          "blockNumber": 0,
          "signature": "3045022100fd770099023a76ca4931df618d3055231415ea9b0047fee98268081003518f9502200af3507ccefcfa155cb83521a15a93b0f516efd7635d736f82f179de33811dca",
          "publickey": "3059301306072a8648ce3d020106082a8648ce3d0301070342000444f13813e9688c4c41b1583b3241eb1efe9139de592b387ea27b5259e054db2acd2a3b72843876bd1b60f67ea73df14943ba3cc2cbf4b48d5a133e7a1233cccc",
          "fee": 0,
          "realFee": 0,
          "nonce": 516965,
          "intStatus": 1,
          "status": "ok"
        },
        // ... 7 signatures
      ]
    },
    {
      "type": "block",
      "hash": "ecdf334cf2439b8913105be172dde30e2011dfdbb53bb79449c90e8e952471a1",
      "prev_hash": "12c6d76cf9456c12728093f0f1ac278d1ee040c7b5ee2fd169539047d2284f30",
      "tx_hash": "25ec8f6d4a7d3246d778404af9d1f2010032ff03b5a2ef4bda165a1fa263643c",
      "number": 530056,
      "timestamp": 1557246164,
      "count_txs": 8,
      "sign": "12c6d76cf9456c12728093f0f1ac278d1ee040c7b5ee2fd169539047d2284f30",
      "size": 1915,
      "fileName": "/data/metahash/20190507.blk",
      "signatures": [
        {
          "from": "0x0028dd1ca2951fe554ef526d60ff55a64776ee5e033120ca91",
          "to": "0x0028dd1ca2951fe554ef526d60ff55a64776ee5e033120ca91",
          "value": 0,
          "transaction": "ed260907dfb9eea1d55b029800c0da7f7bb8619267780e5fa807b542cf121209",
          "data": "8a389612269b6a1da36e97de4ca46587b0c1b75b07664552dc5a2e48dca1b437",
          "timestamp": 1557246164,
          "type": "block",
          "blockNumber": 0,
          "signature": "3046022100976020f193fd513805e9809ab34b5d5332c57acd1a08ea9ae140e26c5d10afe6022100f23b202b6c9109c7c4bacf2d53121755cc59237303cb041e009fad8114ed588e",
          "publickey": "3059301306072a8648ce3d020106082a8648ce3d0301070342000444f13813e9688c4c41b1583b3241eb1efe9139de592b387ea27b5259e054db2acd2a3b72843876bd1b60f67ea73df14943ba3cc2cbf4b48d5a133e7a1233cccc",
          "fee": 0,
          "realFee": 0,
          "nonce": 516964,
          "intStatus": 1,
          "status": "ok"
        },
        // ... 7 signatures
      ]
    },
    {
      "type": "block",
      "hash": "12c6d76cf9456c12728093f0f1ac278d1ee040c7b5ee2fd169539047d2284f30",
      "prev_hash": "8a389612269b6a1da36e97de4ca46587b0c1b75b07664552dc5a2e48dca1b437",
      "tx_hash": "25db1b6cd5bbb6b989993ec92af470b1bd0a973d60b3c5e9b373da1b9eb3c7ad",
      "number": 530055,
      "timestamp": 1557246139,
      "count_txs": 8,
      "sign": "8a389612269b6a1da36e97de4ca46587b0c1b75b07664552dc5a2e48dca1b437",
      "size": 1895,
      "fileName": "/data/metahash/20190507.blk",
      "signatures": [] // latest signatures is always empty
    }
  ]
}
```

### get-dump-block-by-number
```JSON
{
    "id": 1,
    "version": "1.0.0",
    "method": "get-dump-block-by-number",
    "params":{
      "number":1,
      "isHex": true // bool
    }
}
--->
{
  "id": 1,
  "result": {
    "dump": "0123456789abcdeffc04365b000000000000000000000000000000000000000000000000000000000000000000000000e20f1473085c21ad88e9c7edc8fc0f0a009cde423bac9e008d6c31600bea2cf22700288a4e5e7b7ef1cf5d63553906605c8b4ec437653604cd9bfc0080949334ce0900000100000000"
  }
}
```

### get-dump-block-by-hash
```JSON
{
    "id": 1,
    "version": "1.0.0",
    "method": "get-dump-block-by-hash",
    "params":{
      "hash": "85e6c78616632e4fba97efb1dfb403834fe909bc34e3c7efa836ff2ea974ba9b",
      "isHex": true // bool
    }
}
--->
{
  "id": 1,
  "result": {
    "dump": "0123456789abcdeffc04365b000000000000000000000000000000000000000000000000000000000000000000000000e20f1473085c21ad88e9c7edc8fc0f0a009cde423bac9e008d6c31600bea2cf22700288a4e5e7b7ef1cf5d63553906605c8b4ec437653604cd9bfc0080949334ce0900000100000000"
  }
}
```

### get-count-blocks
```JSON
{
    "id": 1,
    "version": "1.0.0",
    "method": "get-count-blocks"
}
--->
{
  "id": 1,
  "result": {
    "count_blocks": 530079
  }
}
```


## Send data
POST http://proxy.net-main.metahashnetwork.com:9999


### mhc_send
```JSON
{
  "id":1,
  "jsonrpc":"2.0",
  "method":"mhc_send",
  "params":
  {
    "transaction":"0004cd0ecb06e091efd2fc486d13c94eafd422486d0d3fc80c01000100",
    "to":"0x0004cd0ecb06e091efd2fc486d13c94eafd422486d0d3fc80c",
    "value":"1",
    "fee":"",
    "nonce":"1",
    "data":"",
    "pubkey":"30563...1ed0af",
    "sign":"304502...adf804"
  }
}
--->
{
    "id": 1,
    "jsonrpc": "2.0",
    "result": "27857e9bf3e00c35cbfb0d09870250af7585dfdf7b946265e97c8c5f244beaa5"
}
```
