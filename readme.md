# MetaHash API

## Sources
https://github.com/metahashorg/metahash-fullnode-client/blob/master/src/task_handlers/task_handlers.cpp#L29



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
---
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
---
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



```JSON
POST http://proxy.net-main.metahashnetwork.com:9999
{
    "id": "1",
    "version": "2.0.0",
    "method": "getinfo"
}

---
{
  "result": {
    "version": "0.2 "
  },
  "error": null
}
```

