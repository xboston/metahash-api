# MetaHash API (document version 0.0.5)
- [MetaHash API](#metahash-api)
  * [Sources](#sources)
  * Torrent nodes - [Get data](#get-data)
    + [fetch-balance](#fetch-balance)
    + [fetch-balances](#fetch-balances)
    + [fetch-history](#fetch-history)
    + [fetch-history-filter](#fetch-history-filter)
    + [get-address-delegations](#get-address-delegations)
    + [get-tx](#get-tx)
    + [get-block-by-hash](#get-block-by-hash)
    + [get-block-by-number](#get-block-by-number)
    + [get-last-txs](#get-last-txs)
    + [get-blocks](#get-blocks)
    + [get-dump-block-by-number](#get-dump-block-by-number)
    + [get-dump-block-by-hash](#get-dump-block-by-hash)
    + [get-count-blocks](#get-count-blocks)
    + [get-forging-sum](#get-forging-sum)
    + [get-last-node-stat-result](#get-last-node-stat-result)
    + [get-last-node-stat-trust](#get-last-node-stat-trust)
    + [get-last-node-stat-count](#get-last-node-stat-count)
    + [get-last-nodes-stats-count](#get-last-nodes-stats-count)
    + [get-all-last-nodes-count](#get-all-last-nodes-count)
    + [get-nodes-raiting](#get-nodes-raiting)
    + [get-common-balance](#get-common-balance)
    + [status](#status)
  * Proxy node - [Send data](#send-data)
    + [mhc_send](#mhc_send)
    + [getinfo](#getinfo)

## Sources

 - https://github.com/metahashorg/metahash-fullnode-client/wiki/Usage
 - https://github.com/metahashorg/metahash-fullnode-client/blob/master/src/task_handlers/task_handlers.cpp#L29


## Get data
POST http://tor.net-main.metahashnetwork.com:5795

### fetch-balance
```JSON
{
    "id": 1,
    "jsonrpc": "2.0",
    "method": "fetch-balance",
    "params": {
        "address": "0x00fa2a5279f8f0fd2f0f9d3280ad70403f01f9d62f52373833"
    }
}
// RESPONSE --->
{
    "id": 1,
    "result": {
        "address": "0x00fa2a5279f8f0fd2f0f9d3280ad70403f01f9d62f52373833",
        "received": 207548681723,
        "spent": 207461981695,
        "count_received": 2820,
        "count_spent": 308,
        "count_txs": 3088,
        "block_number": 1335147,
        "currentBlock": 1340487,
        "hash": "1166961037275381262",
        "countDelegatedOps": 56,
        "delegate": 139817450885,
        "undelegate": 138817450885,
        "delegated": 0,
        "undelegated": 0,
        "reserved": 0,
        "countForgedOps": 189,
        "forged": 1558919302
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
// RESPONSE --->
{
    "id": 1,
    "result": [
        {
            "address": "0x00fa2a5279f8f0fd2f0f9d3280ad70403f01f9d62f52373833",
            "received": 207548681723,
            "spent": 207461981695,
            "count_received": 2820,
            "count_spent": 308,
            "count_txs": 3088,
            "block_number": 1335147,
            "currentBlock": 1340488,
            "hash": "1166961037275381262",
            "countDelegatedOps": 56,
            "delegate": 139817450885,
            "undelegate": 138817450885,
            "delegated": 0,
            "undelegated": 0,
            "reserved": 0,
            "countForgedOps": 189,
            "forged": 1558919302
        },
        {
            "address": "0x0039f42ad734606d250ea0b0151d4aeab6b4edc6587c4b27ef",
            "received": 140619065800517,
            "spent": 138100183418762,
            "count_received": 112,
            "count_spent": 7164,
            "count_txs": 7276,
            "block_number": 1340356,
            "currentBlock": 1340488,
            "hash": "13337710186950535657"
        },
        {
            "address": "0x005b891007c2000fee08e085beb91494f1d3753eb8eee354f0",
            "received": 19756194194557,
            "spent": 19487894058228,
            "count_received": 890,
            "count_spent": 412,
            "count_txs": 1302,
            "block_number": 1340047,
            "currentBlock": 1340488,
            "hash": "10270016351660974727"
        }
    ]
}
```

### fetch-history
```JSON
{
    "id": 1,
    "jsonrpc": "2.0",
    "method": "fetch-history",
    "params": {
        "address": "0x00fa2a5279f8f0fd2f0f9d3280ad70403f01f9d62f52373833",
        "beginTx": 1,
        "countTxs": 2
    }
}
// RESPONSE --->
{
    "id": 1,
    "result": [
        {
            "from": "InitialWalletTransaction",
            "to": "0x00fa2a5279f8f0fd2f0f9d3280ad70403f01f9d62f52373833",
            "value": 619328,
            "transaction": "d1f69192f26db7a1abdc2a0931d1a891e6967db1bd207c54c8af04e8ffd25fd5",
            "data": "",
            "timestamp": 1565049600,
            "type": "forging",
            "blockNumber": 1328547,
            "blockIndex": 24403,
            "signature": "",
            "publickey": "",
            "fee": 0,
            "realFee": 0,
            "nonce": 0,
            "intStatus": 101,
            "status": "ok"
        },
        {
            "from": "0x002a3e8f2714b25df4cab166a611834ebf4158daf5c2855886",
            "to": "0x00fa2a5279f8f0fd2f0f9d3280ad70403f01f9d62f52373833",
            "value": 1000000,
            "transaction": "592e362bd16e11efe576f1cdcdc04fee7f0180f7e999678a1d858a98e558f42a",
            "data": "",
            "timestamp": 1565045672,
            "type": "block",
            "blockNumber": 1328526,
            "blockIndex": 7,
            "signature": "3046022100e97406cc8527a0d88d5e80928d6e0da9aa2e442c7a5844370fb130dfc210678e022100bb8459d4ae56b980666049df910fb8ac1032286f83757470fb53d633e4150e92",
            "publickey": "3059301306072a8648ce3d020106082a8648ce3d0301070342000458f1c1b9c923cb1c52e35c35b647f80518e738eb69fe06cb2af77d7c2f0ab28cd0b8cab4231ac3b1aa61ec2d0c4ed8bd9714fac83513a170c5fe8bd3d970db7c",
            "fee": 0,
            "realFee": 0,
            "nonce": 14,
            "intStatus": 20,
            "status": "ok"
        }
    ]
}
```

### fetch-history-filter
```JSON
{
    "id": 1,
    "jsonrpc": "2.0",
    "method": "fetch-history-filter",
    "params": {
        "address": "0x00fa2a5279f8f0fd2f0f9d3280ad70403f01f9d62f52373833",
        "countTxs": 2,
        "beginTx": 0,
        "filters": {
            "isInput": true
            // isInput - Display only isInput transactions
            // isOutput - Display only isOutput transactions
            // isSuccess - Display only success transactions
            // isForging - Display only forging transactions
            // isTest - Display only test transactions
            // isDelegate - Display only delegation transactions
        }
    }
}
// RESPONSE --->
{
    "id": 1,
    "result": {
        "txs": [
            {
                "from": "0x008eedae48667e94b654e4a18514fd38c728625099f7a83f55",
                "to": "0x00fa2a5279f8f0fd2f0f9d3280ad70403f01f9d62f52373833",
                "value": 547782,
                "transaction": "735e50cfde6d77551770266e44e9275f49c03c0222eae6308f1741e4ad0fda33",
                "data": "",
                "timestamp": 1565829601,
                "type": "block",
                "blockNumber": 1393895,
                "blockIndex": 7,
                "signature": "304502203b1de28ad6c6efbc8659a3ce1719129d1af7221ebbda591562f7d247d60967f70221009b6d10484d2e4846635be39717ff650e155256ec717922dc39ab0ea8321ab303",
                "publickey": "3059301306072a8648ce3d020106082a8648ce3d0301070342000444e89f3e6af36fad4b178c531c3ae33c0986b6e75f6a8f1e2fa31d92a12a1dd3dcec5d92a8a7d4311c2764f0f2d294736744d2d4e278d3062b59b3e7f5ccc946",
                "fee": 0,
                "realFee": 0,
                "nonce": 528,
                "intStatus": 20,
                "status": "ok"
            },
            {
                "from": "InitialWalletTransaction",
                "to": "0x00fa2a5279f8f0fd2f0f9d3280ad70403f01f9d62f52373833",
                "value": 621048,
                "transaction": "672efd88b50970fedcceb7379e0724bb763d65861081f328e9dfb729dd30d4f3",
                "data": "",
                "timestamp": 1565827200,
                "type": "forging",
                "blockNumber": 1392955,
                "blockIndex": 24604,
                "signature": "",
                "publickey": "",
                "fee": 0,
                "realFee": 0,
                "nonce": 0,
                "intStatus": 101,
                "status": "ok"
            }
        ],
        "nextFrom": 3
    }
}
```

### get-tx
```JSON
{
    "id": 1,
    "jsonrpc": "2.0",
    "method": "get-tx",
    "params": {
        "hash": "4be8202c2ae33d9541b36691f0d9d26b4c7560128e160867a13d7404f28cfa4b"
    }
}
// RESPONSE --->
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
            "blockIndex": 17,
            "signature": "3045022100bdb41e082c088f1e0985c745b2555604765ad994a844a59600ac16ccdcfb2ddf02206fde3d477db615f9dd6ee49eba76a5de50b6c6a37670e7fc453b24a3789111d8",
            "publickey": "3059301306072a8648ce3d020106082a8648ce3d030107034200045f54abaebe038e4aba608a730a0df3b11ef13062add93fc119f85283076f247a9e8a468b3e9afcbb3a8b60b18a8435fe2728329cab3ce7ca37a9fad78e2c43df",
            "fee": 31,
            "realFee": 0,
            "nonce": 6567,
            "intStatus": 20,
            "status": "ok"
        },
        "countBlocks": 1340488,
        "knownBlocks": 1340488
    }
}
```


### get-address-delegations
```JSON
{
    "id": 1,
    "jsonrpc": "2.0",
    "method": "get-address-delegations",
    "params": {
        "address": "0x00f0bec7a7b832d4400455229103c6cec3abd6736f60152b6d",
        "beginTx": 0,
        "countTxs": 2
    }
}
// RESPONSE --->
{
    "id": 1,
    "result": {
        "address": "0x00f0bec7a7b832d4400455229103c6cec3abd6736f60152b6d",
        "states": [
            {
                "to": "0x00f0bec7a7b832d4400455229103c6cec3abd6736f60152b6d",
                "value": 100000000000,
                "tx": "c9763e92973b7edab4ace434ce70af68b38166a4fdbfdb0b8af9442e1f9f0264"
            },
            {
                "to": "0x666174686572206f662073657276657220666f7267696e6720",
                "value": 1000000000,
                "tx": "fc6fce5c1a7d7f3ea2be716c9c68c0adb73ec2ef6622324022eb3de9f513a003"
            }
        ]
    }
}
```

### get-block-by-hash
```JSON
{
    "id": 1,
    "jsonrpc": "2.0",
    "method": "get-block-by-hash",
    "params": {
        "hash": "49a840968be1a3c0449a6d7946fd021ce2746006ff5b855fdc0623669833f5e7",
        "type": 1, // 0-4
        "beginTx": 1,
        "countTxs": 2
    }
}
// RESPONSE --->
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
        "fileName": "20190503.blk",
        "signatures": [
            {
                "from": "0x0028dd1ca2951fe554ef526d60ff55a64776ee5e033120ca91",
                "to": "0x0028dd1ca2951fe554ef526d60ff55a64776ee5e033120ca91",
                "value": 0,
                "transaction": "8b82217fca311097a1bf32fce7506a991fe0b1ce73cf4a22dfb9279289d104e3",
                "data": "49a840968be1a3c0449a6d7946fd021ce2746006ff5b855fdc0623669833f5e7",
                "timestamp": 1556837036,
                "type": "block",
                "blockNumber": 475346,
                "blockIndex": 0,
                "signature": "3045022100eb64fc60aee22bd95b4f393a95d225239015646e63e9d454b40a610227fa31df022059a2d6e999cc8c7ad1feb46b95164cd8c07ba7b86bad5625b62d6602a9b627dc",
                "publickey": "3059301306072a8648ce3d020106082a8648ce3d0301070342000444f13813e9688c4c41b1583b3241eb1efe9139de592b387ea27b5259e054db2acd2a3b72843876bd1b60f67ea73df14943ba3cc2cbf4b48d5a133e7a1233cccc",
                "fee": 0,
                "realFee": 0,
                "nonce": 462266,
                "intStatus": 1,
                "status": "ok"
            },
            {
                "from": "0x005140a0ae997aeae77c09d7d4ccf97aa65695a9a1e28812bd",
                "to": "0x005140a0ae997aeae77c09d7d4ccf97aa65695a9a1e28812bd",
                "value": 0,
                "transaction": "3720ba63ed19dcace510ea98b061d564ec7ff6dad3683be7bae609da1780d4fb",
                "data": "49a840968be1a3c0449a6d7946fd021ce2746006ff5b855fdc0623669833f5e7",
                "timestamp": 1556837036,
                "type": "block",
                "blockNumber": 475346,
                "blockIndex": 1,
                "signature": "304502200624fe7ad6f7f00088f1dd08f20c6fb01e0eaa6989d70ec4a4b3e159bc88ccbc0221008245c3afe6ff38f822a09cb45fd87dd5e2f144610355f11a142f69d89a180018",
                "publickey": "3059301306072a8648ce3d020106082a8648ce3d03010703420004a4f4c0050ba6f7b07d78307f1d4ad9961f4f4a34d2f3407e9d58f80b360e8ace0d0e16bae71488e0fc5284b31ef960e4bfa1d7da548dd43c625875aee868dfce",
                "fee": 0,
                "realFee": 0,
                "nonce": 462266,
                "intStatus": 1,
                "status": "ok"
            },
            {
                "from": "0x0057b301028c5e0c234bb35b611fc8d3d15c797fb39ef768a4",
                "to": "0x0057b301028c5e0c234bb35b611fc8d3d15c797fb39ef768a4",
                "value": 0,
                "transaction": "99702b9dd099f7f3712ddba43509ddf84337d4c186fb39387f5fbf8ec46258b9",
                "data": "49a840968be1a3c0449a6d7946fd021ce2746006ff5b855fdc0623669833f5e7",
                "timestamp": 1556837036,
                "type": "block",
                "blockNumber": 475346,
                "blockIndex": 2,
                "signature": "3045022048132abb0208bff3bc9fa45996178f74d19291f97dcc6338b87ed2ce7520e738022100ea9893097367c2222b7b1e068cc68baaca1fe175f80207dc9941dfd7eb8db396",
                "publickey": "3059301306072a8648ce3d020106082a8648ce3d0301070342000426abf3781bd6de97e59bf247aff0cd60ddb0053932b35c18215da637398837f9f22fddada7dd16c568bfa0ed5fdf81801e54035105ea958d2cd9d2627af52df4",
                "fee": 0,
                "realFee": 0,
                "nonce": 462266,
                "intStatus": 1,
                "status": "ok"
            },
            {
                "from": "0x0069fce976a40fbd2c894f1fe635255fc16c80bfe17ce65f5e",
                "to": "0x0069fce976a40fbd2c894f1fe635255fc16c80bfe17ce65f5e",
                "value": 0,
                "transaction": "cb985ceb43eff3f341cb93f4512877abe4af5431ad790828e6438ef5b121ecb3",
                "data": "49a840968be1a3c0449a6d7946fd021ce2746006ff5b855fdc0623669833f5e7",
                "timestamp": 1556837036,
                "type": "block",
                "blockNumber": 475346,
                "blockIndex": 3,
                "signature": "3046022100c875b572054a9afcca597dae2eaa7ece03da9eac988e8eb3dcbe55febd88d503022100843f535104a8dfd94d66a2b3fd88bcc70d898d8c904147410730893dd17cfa2c",
                "publickey": "3059301306072a8648ce3d020106082a8648ce3d03010703420004edd10457be891611b3905408284c527d3743217aed719cf9fe4b3337b74b8556376a0ad2bb2a997a4f681dcfca42bbfbfc4874aac7c8fff851f1f693e0986319",
                "fee": 0,
                "realFee": 0,
                "nonce": 462266,
                "intStatus": 1,
                "status": "ok"
            },
            {
                "from": "0x007fce3c1e56c67f963428b3dcdfc4400408918b843d1652ec",
                "to": "0x007fce3c1e56c67f963428b3dcdfc4400408918b843d1652ec",
                "value": 0,
                "transaction": "4a0933d12b1240f1d20f5579262a334e72cb7a9fffc7b47d6a628a525a4239f6",
                "data": "49a840968be1a3c0449a6d7946fd021ce2746006ff5b855fdc0623669833f5e7",
                "timestamp": 1556837036,
                "type": "block",
                "blockNumber": 475346,
                "blockIndex": 4,
                "signature": "304402201846db8e5e7a62790afae14a2e3ce936ece6d40aa3856e40c2bbf254af833ffb0220073fb56faa79d833bd4d9f40bac2aee71c4be9f529cb00d3be24ff79ae441071",
                "publickey": "3059301306072a8648ce3d020106082a8648ce3d03010703420004d42e2c2f44bdc90cf0ef1b6c04d6c72890230e3fc71962ed1cf8846697976b323b2ac5b077e86d4379919b7072ab4d8605b0db1d7e59c97c445697e2df09b766",
                "fee": 0,
                "realFee": 0,
                "nonce": 462266,
                "intStatus": 1,
                "status": "ok"
            },
            {
                "from": "0x00a88a888d16a23991e73b4081b745eec0f56cdc7063baa360",
                "to": "0x00a88a888d16a23991e73b4081b745eec0f56cdc7063baa360",
                "value": 0,
                "transaction": "b7316fea95f776e9035b67583aae9a28d7d17e3c4e9a1fb291acf91d3142d56c",
                "data": "49a840968be1a3c0449a6d7946fd021ce2746006ff5b855fdc0623669833f5e7",
                "timestamp": 1556837036,
                "type": "block",
                "blockNumber": 475346,
                "blockIndex": 5,
                "signature": "3044022024aec7dd52255f629a6d420b7e84e9db4eb425b797e468b41266e4e28d07858e02205e582a49ff900e082bc40af4e1ca67592de10c4acd7fe5b75dea08621dccd268",
                "publickey": "3059301306072a8648ce3d020106082a8648ce3d03010703420004886d9fe32423473984eb0c6782c69e64d08e33c1c89c74d3925dab93c73aff72b670f482e2f753f9f7811198f37abe8fa873d8afc665a5801a183246cc997dcb",
                "fee": 0,
                "realFee": 0,
                "nonce": 462266,
                "intStatus": 1,
                "status": "ok"
            },
            {
                "from": "0x00f3dc22cbe3519ce94e9bf12145d61789da0bfd26bbdf7999",
                "to": "0x00f3dc22cbe3519ce94e9bf12145d61789da0bfd26bbdf7999",
                "value": 0,
                "transaction": "11b8cf898acbbcb60fbad70f164165774531291478796b0985b73110efe695db",
                "data": "49a840968be1a3c0449a6d7946fd021ce2746006ff5b855fdc0623669833f5e7",
                "timestamp": 1556837036,
                "type": "block",
                "blockNumber": 475346,
                "blockIndex": 6,
                "signature": "3044022019c2070fd61d9c7500f6732be03097add152288358f67d3fced74e35a72b7e9702201f87d4f0a6ac70358844f1a8dd2f5c19392e4138884516449ff771474477bff2",
                "publickey": "3059301306072a8648ce3d020106082a8648ce3d03010703420004a8dc0b349c7bbff11ee6d3106de19c13fddda24ddda3bbc0961f17d389e2f4426fd6ca8feaa8773bf316056906f2c0d9bc16e5f341e3ed389379329be039b0eb",
                "fee": 0,
                "realFee": 0,
                "nonce": 462266,
                "intStatus": 1,
                "status": "ok"
            }
        ],
        "txs": [
            "9510a3aafba0f0671c396b8925678b4a43a98ef67b77e0b300f50d9a6439ec01",
            "8d592d0c68f6a8e09636b00c896c8be537045247fb2ee193e9c32eeac7cbf243"
        ]
    }
}
```


### get-block-by-number
```JSON
{
    "id": 1,
    "jsonrpc": "2.0",
    "method": "get-block-by-number",
    "params": {
        "number": 475345,
        "type": 1, // 0-4
        "beginTx": 1,
        "countTxs": 2
    }
}
// RESPONSE --->
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
        "fileName": "20190503.blk",
        "signatures": [
            {
                "from": "0x0028dd1ca2951fe554ef526d60ff55a64776ee5e033120ca91",
                "to": "0x0028dd1ca2951fe554ef526d60ff55a64776ee5e033120ca91",
                "value": 0,
                "transaction": "8b82217fca311097a1bf32fce7506a991fe0b1ce73cf4a22dfb9279289d104e3",
                "data": "49a840968be1a3c0449a6d7946fd021ce2746006ff5b855fdc0623669833f5e7",
                "timestamp": 1556837036,
                "type": "block",
                "blockNumber": 475346,
                "blockIndex": 0,
                "signature": "3045022100eb64fc60aee22bd95b4f393a95d225239015646e63e9d454b40a610227fa31df022059a2d6e999cc8c7ad1feb46b95164cd8c07ba7b86bad5625b62d6602a9b627dc",
                "publickey": "3059301306072a8648ce3d020106082a8648ce3d0301070342000444f13813e9688c4c41b1583b3241eb1efe9139de592b387ea27b5259e054db2acd2a3b72843876bd1b60f67ea73df14943ba3cc2cbf4b48d5a133e7a1233cccc",
                "fee": 0,
                "realFee": 0,
                "nonce": 462266,
                "intStatus": 1,
                "status": "ok"
            },
            {
                "from": "0x005140a0ae997aeae77c09d7d4ccf97aa65695a9a1e28812bd",
                "to": "0x005140a0ae997aeae77c09d7d4ccf97aa65695a9a1e28812bd",
                "value": 0,
                "transaction": "3720ba63ed19dcace510ea98b061d564ec7ff6dad3683be7bae609da1780d4fb",
                "data": "49a840968be1a3c0449a6d7946fd021ce2746006ff5b855fdc0623669833f5e7",
                "timestamp": 1556837036,
                "type": "block",
                "blockNumber": 475346,
                "blockIndex": 1,
                "signature": "304502200624fe7ad6f7f00088f1dd08f20c6fb01e0eaa6989d70ec4a4b3e159bc88ccbc0221008245c3afe6ff38f822a09cb45fd87dd5e2f144610355f11a142f69d89a180018",
                "publickey": "3059301306072a8648ce3d020106082a8648ce3d03010703420004a4f4c0050ba6f7b07d78307f1d4ad9961f4f4a34d2f3407e9d58f80b360e8ace0d0e16bae71488e0fc5284b31ef960e4bfa1d7da548dd43c625875aee868dfce",
                "fee": 0,
                "realFee": 0,
                "nonce": 462266,
                "intStatus": 1,
                "status": "ok"
            },
            {
                "from": "0x0057b301028c5e0c234bb35b611fc8d3d15c797fb39ef768a4",
                "to": "0x0057b301028c5e0c234bb35b611fc8d3d15c797fb39ef768a4",
                "value": 0,
                "transaction": "99702b9dd099f7f3712ddba43509ddf84337d4c186fb39387f5fbf8ec46258b9",
                "data": "49a840968be1a3c0449a6d7946fd021ce2746006ff5b855fdc0623669833f5e7",
                "timestamp": 1556837036,
                "type": "block",
                "blockNumber": 475346,
                "blockIndex": 2,
                "signature": "3045022048132abb0208bff3bc9fa45996178f74d19291f97dcc6338b87ed2ce7520e738022100ea9893097367c2222b7b1e068cc68baaca1fe175f80207dc9941dfd7eb8db396",
                "publickey": "3059301306072a8648ce3d020106082a8648ce3d0301070342000426abf3781bd6de97e59bf247aff0cd60ddb0053932b35c18215da637398837f9f22fddada7dd16c568bfa0ed5fdf81801e54035105ea958d2cd9d2627af52df4",
                "fee": 0,
                "realFee": 0,
                "nonce": 462266,
                "intStatus": 1,
                "status": "ok"
            },
            {
                "from": "0x0069fce976a40fbd2c894f1fe635255fc16c80bfe17ce65f5e",
                "to": "0x0069fce976a40fbd2c894f1fe635255fc16c80bfe17ce65f5e",
                "value": 0,
                "transaction": "cb985ceb43eff3f341cb93f4512877abe4af5431ad790828e6438ef5b121ecb3",
                "data": "49a840968be1a3c0449a6d7946fd021ce2746006ff5b855fdc0623669833f5e7",
                "timestamp": 1556837036,
                "type": "block",
                "blockNumber": 475346,
                "blockIndex": 3,
                "signature": "3046022100c875b572054a9afcca597dae2eaa7ece03da9eac988e8eb3dcbe55febd88d503022100843f535104a8dfd94d66a2b3fd88bcc70d898d8c904147410730893dd17cfa2c",
                "publickey": "3059301306072a8648ce3d020106082a8648ce3d03010703420004edd10457be891611b3905408284c527d3743217aed719cf9fe4b3337b74b8556376a0ad2bb2a997a4f681dcfca42bbfbfc4874aac7c8fff851f1f693e0986319",
                "fee": 0,
                "realFee": 0,
                "nonce": 462266,
                "intStatus": 1,
                "status": "ok"
            },
            {
                "from": "0x007fce3c1e56c67f963428b3dcdfc4400408918b843d1652ec",
                "to": "0x007fce3c1e56c67f963428b3dcdfc4400408918b843d1652ec",
                "value": 0,
                "transaction": "4a0933d12b1240f1d20f5579262a334e72cb7a9fffc7b47d6a628a525a4239f6",
                "data": "49a840968be1a3c0449a6d7946fd021ce2746006ff5b855fdc0623669833f5e7",
                "timestamp": 1556837036,
                "type": "block",
                "blockNumber": 475346,
                "blockIndex": 4,
                "signature": "304402201846db8e5e7a62790afae14a2e3ce936ece6d40aa3856e40c2bbf254af833ffb0220073fb56faa79d833bd4d9f40bac2aee71c4be9f529cb00d3be24ff79ae441071",
                "publickey": "3059301306072a8648ce3d020106082a8648ce3d03010703420004d42e2c2f44bdc90cf0ef1b6c04d6c72890230e3fc71962ed1cf8846697976b323b2ac5b077e86d4379919b7072ab4d8605b0db1d7e59c97c445697e2df09b766",
                "fee": 0,
                "realFee": 0,
                "nonce": 462266,
                "intStatus": 1,
                "status": "ok"
            },
            {
                "from": "0x00a88a888d16a23991e73b4081b745eec0f56cdc7063baa360",
                "to": "0x00a88a888d16a23991e73b4081b745eec0f56cdc7063baa360",
                "value": 0,
                "transaction": "b7316fea95f776e9035b67583aae9a28d7d17e3c4e9a1fb291acf91d3142d56c",
                "data": "49a840968be1a3c0449a6d7946fd021ce2746006ff5b855fdc0623669833f5e7",
                "timestamp": 1556837036,
                "type": "block",
                "blockNumber": 475346,
                "blockIndex": 5,
                "signature": "3044022024aec7dd52255f629a6d420b7e84e9db4eb425b797e468b41266e4e28d07858e02205e582a49ff900e082bc40af4e1ca67592de10c4acd7fe5b75dea08621dccd268",
                "publickey": "3059301306072a8648ce3d020106082a8648ce3d03010703420004886d9fe32423473984eb0c6782c69e64d08e33c1c89c74d3925dab93c73aff72b670f482e2f753f9f7811198f37abe8fa873d8afc665a5801a183246cc997dcb",
                "fee": 0,
                "realFee": 0,
                "nonce": 462266,
                "intStatus": 1,
                "status": "ok"
            },
            {
                "from": "0x00f3dc22cbe3519ce94e9bf12145d61789da0bfd26bbdf7999",
                "to": "0x00f3dc22cbe3519ce94e9bf12145d61789da0bfd26bbdf7999",
                "value": 0,
                "transaction": "11b8cf898acbbcb60fbad70f164165774531291478796b0985b73110efe695db",
                "data": "49a840968be1a3c0449a6d7946fd021ce2746006ff5b855fdc0623669833f5e7",
                "timestamp": 1556837036,
                "type": "block",
                "blockNumber": 475346,
                "blockIndex": 6,
                "signature": "3044022019c2070fd61d9c7500f6732be03097add152288358f67d3fced74e35a72b7e9702201f87d4f0a6ac70358844f1a8dd2f5c19392e4138884516449ff771474477bff2",
                "publickey": "3059301306072a8648ce3d020106082a8648ce3d03010703420004a8dc0b349c7bbff11ee6d3106de19c13fddda24ddda3bbc0961f17d389e2f4426fd6ca8feaa8773bf316056906f2c0d9bc16e5f341e3ed389379329be039b0eb",
                "fee": 0,
                "realFee": 0,
                "nonce": 462266,
                "intStatus": 1,
                "status": "ok"
            }
        ],
        "txs": [
            "9510a3aafba0f0671c396b8925678b4a43a98ef67b77e0b300f50d9a6439ec01",
            "8d592d0c68f6a8e09636b00c896c8be537045247fb2ee193e9c32eeac7cbf243"
        ]
    }
}
```

### get-last-txs
```JSON
{
    "id": 1,
    "jsonrpc": "2.0",
    "method": "get-last-txs"
}
// RESPONSE --->
{
    "id": 1,
    "result": [
        {
            "from": "0x0028dd1ca2951fe554ef526d60ff55a64776ee5e033120ca91",
            "to": "0x0028dd1ca2951fe554ef526d60ff55a64776ee5e033120ca91",
            "value": 0,
            "transaction": "93c2a406373d10d67d85d619ec99c314c3b17dab67da9592b95d1d8cd68c6a12",
            "data": "64afb36db97eeaa9c0472405805a6791a7f700df7baa84d6a3dae6569361f515",
            "timestamp": 1565204160,
            "type": "block",
            "blockNumber": 1340489,
            "blockIndex": 0,
            "signature": "3045022100d0c29d8989b810f579ddc9d1141b0ea39489cea9ec80a368cd945372f8ea8395022071d0e3835ee716f4dd7c7007d85ac812bdad7d85dfddd56232403880052bf7b3",
            "publickey": "3059301306072a8648ce3d020106082a8648ce3d0301070342000444f13813e9688c4c41b1583b3241eb1efe9139de592b387ea27b5259e054db2acd2a3b72843876bd1b60f67ea73df14943ba3cc2cbf4b48d5a133e7a1233cccc",
            "fee": 0,
            "realFee": 0,
            "nonce": 1327203,
            "intStatus": 1,
            "status": "ok"
        },
        // ... 100 items
        {
            "from": "0x00b888869e8d4a193e80c59f923fe9f93fd6552875c857edbe",
            "to": "0x008847ec858a18d20245ec0c4e2fd77a05727e4bebde23898a",
            "value": 0,
            "transaction": "fc131c718b2c626b95d9338189bd353b6071dddf29317d870bfbcfc136529eab",
            "data": "7b226d6574686f64223a2270726f78795f6c6f61645f726573756c7473222c22706172616d73223a7b22766572223a22222c226d6861646472223a2230783030383834376563383538613138643230323435656330633465326664373761303537323765346265626465323338393861222c226970223a2232332e3233382e3131352e3234323a39393939222c22717073223a2230222c22727073223a2230222c22636c6f736564223a2230222c2274696d656f757473223a2230222c2267656f223a227573222c2273756363657373223a2266616c7365227d7d",
            "timestamp": 1565203800,
            "type": "block",
            "blockNumber": 1340488,
            "blockIndex": 91,
            "signature": "304402200d01cc9403eaf274bdf0e2c99c4f68d165ddd69d59ecd49890a1dc739e79f9b4022015dc8bee6de5ba8ce6ad96a21ea658bf481e0de14c3b57e6bdbea2ad88c11a16",
            "publickey": "3059301306072a8648ce3d020106082a8648ce3d0301070342000452f197a3b40a57782d8e4659ceafea42890962c75d815eec24a01a02f4bd512f9297fb688b67dc9f56929882a786057255fdf79b2d2ac2ed2bde4e5f9e74d105",
            "fee": 0,
            "realFee": 0,
            "nonce": 1565202488,
            "intStatus": 4353,
            "status": "ok"
        }
    ]
}
```

### get-blocks
```JSON
{
    "id": 1,
    "jsonrpc": "2.0",
    "method": "get-blocks",
    "params": {
        "beginBlock": 1,
        "countBlocks": 2
    }
}
// RESPONSE --->
{
    "id": 1,
    "result": [
        {
            "type": "block",
            "hash": "64afb36db97eeaa9c0472405805a6791a7f700df7baa84d6a3dae6569361f515",
            "prev_hash": "5d424ae60b31f8f570536114500e86ecd2e1776eed0e049d9b5a6826d13cd5e0",
            "tx_hash": "68eb866079793d002f58191074e5b0d5382e0469c8aeb3fc6e6b1f596c75a1fc",
            "number": 1340488,
            "timestamp": 1565203800,
            "count_txs": 768,
            "sign": "5d424ae60b31f8f570536114500e86ecd2e1776eed0e049d9b5a6826d13cd5e0",
            "size": 337789,
            "fileName": "20190807.blk",
            "signatures": [
                {
                    "from": "0x0028dd1ca2951fe554ef526d60ff55a64776ee5e033120ca91",
                    "to": "0x0028dd1ca2951fe554ef526d60ff55a64776ee5e033120ca91",
                    "value": 0,
                    "transaction": "088623922cf8985891d8db0f1bd7cae335110381deab314ede56e3fd21e73f5b",
                    "data": "726bfd0aaddd4f6757ff7449d726c5f95295e4c2cd12f88797174a67703e2ea1",
                    "timestamp": 1565203800,
                    "type": "block",
                    "blockNumber": 1340487,
                    "blockIndex": 0,
                    "signature": "3045022017adaae4b784906184e8d67d9a77dadd26e298d3a6d08c95045777a6e326cdfb0221009193e239c3a1a76a10c3296ff51b92fc1e926449417a5fb000b5341996126545",
                    "publickey": "3059301306072a8648ce3d020106082a8648ce3d0301070342000444f13813e9688c4c41b1583b3241eb1efe9139de592b387ea27b5259e054db2acd2a3b72843876bd1b60f67ea73df14943ba3cc2cbf4b48d5a133e7a1233cccc",
                    "fee": 0,
                    "realFee": 0,
                    "nonce": 1327201,
                    "intStatus": 1,
                    "status": "ok"
                },
                {
                    "from": "0x005140a0ae997aeae77c09d7d4ccf97aa65695a9a1e28812bd",
                    "to": "0x005140a0ae997aeae77c09d7d4ccf97aa65695a9a1e28812bd",
                    "value": 0,
                    "transaction": "f72c7856d7d639e90711343c63207557320bf0adcd3ef8cc39a57c5ab9dfdd8b",
                    "data": "726bfd0aaddd4f6757ff7449d726c5f95295e4c2cd12f88797174a67703e2ea1",
                    "timestamp": 1565203800,
                    "type": "block",
                    "blockNumber": 1340487,
                    "blockIndex": 1,
                    "signature": "304502207f203c12496083a981166ded43a8f2a9c8cdb7a660324df8c91192a6c29ddd0c022100919c87ef9c1a0294092fa7a9c99f1b944b9c61ce6658fae6bae804e595058708",
                    "publickey": "3059301306072a8648ce3d020106082a8648ce3d03010703420004a4f4c0050ba6f7b07d78307f1d4ad9961f4f4a34d2f3407e9d58f80b360e8ace0d0e16bae71488e0fc5284b31ef960e4bfa1d7da548dd43c625875aee868dfce",
                    "fee": 0,
                    "realFee": 0,
                    "nonce": 1327201,
                    "intStatus": 1,
                    "status": "ok"
                },
                {
                    "from": "0x0057b301028c5e0c234bb35b611fc8d3d15c797fb39ef768a4",
                    "to": "0x0057b301028c5e0c234bb35b611fc8d3d15c797fb39ef768a4",
                    "value": 0,
                    "transaction": "4230cf4b55a2c188db875b89d59194abdfe57b7a45e72da6440ab6f8982bf5c9",
                    "data": "726bfd0aaddd4f6757ff7449d726c5f95295e4c2cd12f88797174a67703e2ea1",
                    "timestamp": 1565203800,
                    "type": "block",
                    "blockNumber": 1340487,
                    "blockIndex": 2,
                    "signature": "3045022062a25fd3e36d2fa9ca1028b64ef9b892ccf58a801785ae1af6668d2f743b0c98022100ff734837e340dd45daca480c4bf89bdffb3adbbfb504a67106e110eb55bf8580",
                    "publickey": "3059301306072a8648ce3d020106082a8648ce3d0301070342000426abf3781bd6de97e59bf247aff0cd60ddb0053932b35c18215da637398837f9f22fddada7dd16c568bfa0ed5fdf81801e54035105ea958d2cd9d2627af52df4",
                    "fee": 0,
                    "realFee": 0,
                    "nonce": 1327201,
                    "intStatus": 1,
                    "status": "ok"
                },
                {
                    "from": "0x0069fce976a40fbd2c894f1fe635255fc16c80bfe17ce65f5e",
                    "to": "0x0069fce976a40fbd2c894f1fe635255fc16c80bfe17ce65f5e",
                    "value": 0,
                    "transaction": "49d78ef297898eaf192a6df396d14cc28b0ca19fc398c4eeef5fe0b210f0318b",
                    "data": "726bfd0aaddd4f6757ff7449d726c5f95295e4c2cd12f88797174a67703e2ea1",
                    "timestamp": 1565203800,
                    "type": "block",
                    "blockNumber": 1340487,
                    "blockIndex": 3,
                    "signature": "3045022100e6b69bd106eed2b0af026925e5eb378be2f508db07c984544f97e3f70d47155f0220383addb252f9a07d430c19a49b0005116b1d9442d839805702df4f41d957c3ed",
                    "publickey": "3059301306072a8648ce3d020106082a8648ce3d03010703420004edd10457be891611b3905408284c527d3743217aed719cf9fe4b3337b74b8556376a0ad2bb2a997a4f681dcfca42bbfbfc4874aac7c8fff851f1f693e0986319",
                    "fee": 0,
                    "realFee": 0,
                    "nonce": 1327201,
                    "intStatus": 1,
                    "status": "ok"
                },
                {
                    "from": "0x007fce3c1e56c67f963428b3dcdfc4400408918b843d1652ec",
                    "to": "0x007fce3c1e56c67f963428b3dcdfc4400408918b843d1652ec",
                    "value": 0,
                    "transaction": "46bb9c19862fbf1b995c6e9641b4569553123bb6514f3b934094cabef0a2ce00",
                    "data": "726bfd0aaddd4f6757ff7449d726c5f95295e4c2cd12f88797174a67703e2ea1",
                    "timestamp": 1565203800,
                    "type": "block",
                    "blockNumber": 1340487,
                    "blockIndex": 4,
                    "signature": "3045022017fa12f9353506c64dc30018fa5df98ea6b3a6c405a836293b352e7e45e39b6d022100b87e0b813b5e320dab02ee5040fdb764f53192bdef1b1cca6aa80e334f734e0a",
                    "publickey": "3059301306072a8648ce3d020106082a8648ce3d03010703420004d42e2c2f44bdc90cf0ef1b6c04d6c72890230e3fc71962ed1cf8846697976b323b2ac5b077e86d4379919b7072ab4d8605b0db1d7e59c97c445697e2df09b766",
                    "fee": 0,
                    "realFee": 0,
                    "nonce": 1327201,
                    "intStatus": 1,
                    "status": "ok"
                },
                {
                    "from": "0x00a88a888d16a23991e73b4081b745eec0f56cdc7063baa360",
                    "to": "0x00a88a888d16a23991e73b4081b745eec0f56cdc7063baa360",
                    "value": 0,
                    "transaction": "bbae8202451bcb4188ff599be3e40405802109823504f1b7ba85d8287a02356e",
                    "data": "726bfd0aaddd4f6757ff7449d726c5f95295e4c2cd12f88797174a67703e2ea1",
                    "timestamp": 1565203800,
                    "type": "block",
                    "blockNumber": 1340487,
                    "blockIndex": 5,
                    "signature": "3045022100cc78a61ce3107e71b1efa5d61c118f3f5fdd44e43935b10198f679696b9fa47902205a6d60034627d2b1a41083eced3bbd10e7621dc382428a1d09c8a6e1b62014ff",
                    "publickey": "3059301306072a8648ce3d020106082a8648ce3d03010703420004886d9fe32423473984eb0c6782c69e64d08e33c1c89c74d3925dab93c73aff72b670f482e2f753f9f7811198f37abe8fa873d8afc665a5801a183246cc997dcb",
                    "fee": 0,
                    "realFee": 0,
                    "nonce": 1327201,
                    "intStatus": 1,
                    "status": "ok"
                },
                {
                    "from": "0x00f3dc22cbe3519ce94e9bf12145d61789da0bfd26bbdf7999",
                    "to": "0x00f3dc22cbe3519ce94e9bf12145d61789da0bfd26bbdf7999",
                    "value": 0,
                    "transaction": "83f51b27af5e75d25b6343e96761efe7e077ad1aae03e803cba4c075a4bb69e1",
                    "data": "726bfd0aaddd4f6757ff7449d726c5f95295e4c2cd12f88797174a67703e2ea1",
                    "timestamp": 1565203800,
                    "type": "block",
                    "blockNumber": 1340487,
                    "blockIndex": 6,
                    "signature": "304502206320946b4373d7357ef7f1e20977da5f5389eae1cf3df0c343688b3ddc199303022100e7e7e5c1f55f9f4c383f4f6141d856bd0a3148fccb013242cd07f8429e6218fd",
                    "publickey": "3059301306072a8648ce3d020106082a8648ce3d03010703420004a8dc0b349c7bbff11ee6d3106de19c13fddda24ddda3bbc0961f17d389e2f4426fd6ca8feaa8773bf316056906f2c0d9bc16e5f341e3ed389379329be039b0eb",
                    "fee": 0,
                    "realFee": 0,
                    "nonce": 1327201,
                    "intStatus": 1,
                    "status": "ok"
                }
            ]
        },
        {
            "type": "block",
            "hash": "5d424ae60b31f8f570536114500e86ecd2e1776eed0e049d9b5a6826d13cd5e0",
            "prev_hash": "726bfd0aaddd4f6757ff7449d726c5f95295e4c2cd12f88797174a67703e2ea1",
            "tx_hash": "64d3e2d0b362a60dd2cae0b39cf2f3c8b1353b1281cb5ed375e9dcd2b9e17f28",
            "number": 1340487,
            "timestamp": 1565203742,
            "count_txs": 8,
            "sign": "726bfd0aaddd4f6757ff7449d726c5f95295e4c2cd12f88797174a67703e2ea1",
            "size": 1893,
            "fileName": "20190807.blk",
            "signatures": []
        }
    ]
}
```

### get-dump-block-by-number
```JSON
{
    "id": 1,
    "jsonrpc": "2.0",
    "method": "get-dump-block-by-number",
    "params": {
        "number": 1,
        "isHex": true
    }
}
// RESPONSE --->
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
    "jsonrpc": "2.0",
    "method": "get-dump-block-by-hash",
    "params": {
        "hash": "85e6c78616632e4fba97efb1dfb403834fe909bc34e3c7efa836ff2ea974ba9b",
        "isHex": true
    }
}
// RESPONSE --->
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
    "jsonrpc": "2.0",
    "method": "get-count-blocks"
}
// RESPONSE --->
{
    "id": 1,
    "result": {
        "count_blocks": 1340489
    }
}
```

### get-forging-sum-all
```JSON
{
    "id": 1,
    "jsonrpc": "2.0",
    "method": "get-forging-sum-all"
}
// RESPONSE --->
{
    "id": 1,
    "result": {
        "blockNumber": 1429969,
        "sums": [
            {
                "type": 101,
                "value": 6684472230145
            },
            {
                "type": 100,
                "value": 0
            },
            {
                "type": 102,
                "value": 155858088879880
            },
            {
                "type": 104,
                "value": 35506056329070
            },
            {
                "type": 103,
                "value": 194789794021418
            }
        ]
    }
}
```

### get-forging-sum
```JSON
{
    "id": 1,
    "jsonrpc": "2.0",
    "method": "get-forging-sum",
    "params": {
        "block_indent": 1
    }
}
// RESPONSE --->
{
    "id": 1,
    "result": {
        "blockNumber": 1424739,
        "sums": [
            {
                "type": 104,
                "value": 174674129635
            },
            {
                "type": 103,
                "value": 970411832343
            },
            {
                "type": 102,
                "value": 776329466476
            },
            {
                "type": 100,
                "value": 0
            },
            {
                "type": 101,
                "value": 19408227345
            }
        ]
    }
}
```


### get-last-node-stat-result
```JSON
{
    "id": 1,
    "jsonrpc": "2.0",
    "method": "get-last-node-stat-result",
    "params": {
        "address": "0x00d5b768fee94349103e2f69484dff207a3bbb2a5077defd6e"
    }
}
// RESPONSE --->
{
    "id": 1,
    "result": {
        "address": "0x00d5b768fee94349103e2f69484dff207a3bbb2a5077defd6e",
        "type": "Proxy",
        "avgRps": "2156",
        "ip": "116.202.103.152:9999",
        "geo": "us",
        "state": "{\"method\":\"proxy_load_results\",\"params\":{\"ver\":\"1.4\",\"mhaddr\":\"0x00d5b768fee94349103e2f69484dff207a3bbb2a5077defd6e\",\"ip\":\"116.202.103.152:9999\",\"qps\":\"2976\",\"rps\":\"1935\",\"closed\":\"1380\",\"timeouts\":\"1382\",\"geo\":\"us\",\"success\":\"true\"}}",
        "timestamp": 1566595800,
        "success": true,
        "lastBlockTimestamp": 1566596102
    }
}
```

### get-last-node-stat-trust
```JSON
{
    "id": 1,
    "jsonrpc": "2.0",
    "method": "get-last-node-stat-trust",
    "params": {
        "address": "0x00d5b768fee94349103e2f69484dff207a3bbb2a5077defd6e"
    }
}
// RESPONSE --->
{
    "id": 1,
    "result": {
        "address": "0x00d5b768fee94349103e2f69484dff207a3bbb2a5077defd6e",
        "trust": 265,
        "data": "{\"state\":81,\"trust\":265,\"delegate_to\":[{\"a\":\"0x666174686572206f662073657276657220666f7267696e6720\",\"v\":1000000000}],\"delegated_from\":[{\"a\":\"0x0031a11c63ee03d4f527cd2dce6807cce71724fd9a1713f738\",\"v\":1000000000},{\"a\":\"0x00d585ed843cbafa83b72f7854088aded64a5d9f143ea7727e\",\"v\":700000000},{\"a\":\"0x005cc86cf1915572360b0d2b3cb5b12900c1325620df2a7b81\",\"v\":6000000000},{\"a\":\"0x000f571063370c6988d04a039b02118a9c2ac8cd43a363719a\",\"v\":516000000},{\"a\":\"0x0031a11c63ee03d4f527cd2dce6807cce71724fd9a1713f738\",\"v\":543000000},{\"a\":\"0x004e2ffa57403f2445dfc3097093f4ab46529bb1c92cc7c623\",\"v\":30000000000},{\"a\":\"0x00722914d7a6f22cd4a3ec43a2b60ee304131028acd1966c85\",\"v\":100000000000},{\"a\":\"0x0023511e8f42ff0c5597c4a1369bf023435a41bae55fcbe9f8\",\"v\":1373165874},{\"a\":\"0x002bfe9f1d205835ab8a055eccea6627220e9296096e12ec07\",\"v\":512000000},{\"a\":\"0x00033e66432c545b646baba654c1215ad94ede07ce73305609\",\"v\":10000000000}]}",
        "timestamp": 1566518409,
        "lastBlockTimestamp": 1566596295
    }
}
```


### get-last-node-stat-count
```JSON
{
    "id": 1,
    "jsonrpc": "2.0",
    "method": "get-last-node-stat-count",
    "params": {
        "address": "0x00d5b768fee94349103e2f69484dff207a3bbb2a5077defd6e"
    }
}
// RESPONSE --->
{
    "id": 1,
    "result": {
        "address": "0x00d5b768fee94349103e2f69484dff207a3bbb2a5077defd6e",
        "day": 200,
        "count": 194,
        "countAll": 194,
        "testers": 3,
        "lastBlockDay": 200
    }
}
```


### get-last-nodes-stats-count
```JSON
{
    "id": 1,
    "jsonrpc": "2.0",
    "method": "get-last-nodes-stats-count"
}
// RESPONSE --->
{
    "id": 1,
    "result": {
        "day": 200,
        "count": 42204,
        "countAll": 75591,
        "testers": 3,
        "lastBlockDay": 200
    }
}
```


### get-all-last-nodes-count
```JSON
{
    "id": 1,
    "jsonrpc": "2.0",
    "method": "get-all-last-nodes-count",
    "params": {
        "count_tests": 100
    }
}
// RESPONSE --->
{
    "id": 1,
    "result": {
        "nodes": [
            {
                "node": "0x0000496c628660f91a19f04d41c497353d749fda793f86a844",
                "ip": "116.203.***.***",
                "type": "InfrastructureTorrent",
                "count": 196
            },
            {
                "node": "0x000168a8b22adad0c4634d334e37c5e5b4474ab208983f5df7",
                "ip": "142.91.***.***:9999",
                "type": "Proxy",
                "count": 193
            },
            {
                "node": "0x0001a6ba6fd9a6e9e87f468d7fa9f848ebf8adf7a522bd2a18",
                "ip": "37.48.***.***:9999",
                "type": "Proxy",
                "count": 194
            },
        ...
        ],
        "day": 200,
        "lastBlockDay": 200
    }
}
```

### get-nodes-raiting
```JSON
{
    "id": 1,
    "jsonrpc": "2.0",
    "method": "get-nodes-raiting",
    "params": {
        "address": "0x00d5b768fee94349103e2f69484dff207a3bbb2a5077defd6e",
        "count_tests": 10
    }
}
// RESPONSE --->
{
    "id": 1,
    "result": {
        "address": "0x00d5b768fee94349103e2f69484dff207a3bbb2a5077defd6e",
        "raiting": 4,
        "day": 200,
        "lastBlockDay": 200
    }
}
```

### get-common-balance
```JSON
{
    "id": 1,
    "jsonrpc": "2.0",
    "method": "get-common-balance"
}
// RESPONSE --->
{
    "id": 1,
    "result": {
        "balance": 3152838411460513
    }
}
```

### status
```JSON
{
    "id": 1,
    "version": "2.0.0",
    "method": "status"
}
// RESPONSE --->
{
    "id": 1,
    "result": "ok",
    "version": "0.129",
    "git_hash": "2f0b4c27d62671116adf72ec375c217d3759133d"
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
    "to":"0x0004cd0ecb06e091efd2fc486d13c94eafd422486d0d3fc80c",
    "value":"1",
    "fee":"",
    "nonce":"1",
    "data":"",
    "pubkey":"30563...1ed0af",
    "sign":"304502...adf804"
  }
}
// RESPONSE --->
{
    "id": 1,
    "jsonrpc": "2.0",
    "result": "27857e9bf3e00c35cbfb0d09870250af7585dfdf7b946265e97c8c5f244beaa5"
}
```

### getinfo
```JSON
{
    "id": 1,
    "version": "2.0.0",
    "method": "getinfo"
}
// RESPONSE --->
{
    "result": {
        "version": "0.2 "
    },
    "error": null
}
```