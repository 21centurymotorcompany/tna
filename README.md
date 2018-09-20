# TNA

TNA translates raw bitcoin transaction into bitdb document format, which allows for powerful queries into the bitcoin universe.

![protein](./protein.png)

# Installation

```
npm install --save tna
```

# Usage

There are two methods:

1. **fromHash:** Generates bitdb document from transaction hash. (requires a local bitcoin node for JSON-RPC)
2. **fromtx:** Generates bitdb document from raw transaction (Local operation and doesn't require a bitcoin node)

## 1. fromHash

Generate bitdb document format from transaction hash

```
const TNA = require('tna');
(async function() {
  let result = await TNA.fromHash("3a737de7faa2ae1914f57ca0a11fd471334e40d4079d98cd77d27727e388b09d")
  console.log(result)
})();
```

prints:

```
{
  "tx": {
    "hash": "3a737de7faa2ae1914f57ca0a11fd471334e40d4079d98cd77d27727e388b09d"
  },
  "input": [
    {
      "index": 0,
      "b0": "MEUCIQDBoMX/xbeOOay1vhQ44ooQ5arIM39dp+TCW6TF8+sBtQIgUOmZe65CNYXaUtfNyJUTefW/8HrbZ1b/5w58cYH4pb1B",
      "b1": "Ays0X4liCvdfWaqR1HzDWeTdkHgWzgZSYEkicmAlcS9S",
      "str": "<Script: 72 0x3045022100c1a0c5ffc5b78e39acb5be1438e28a10e5aac8337f5da7e4c25ba4c5f3eb01b5022050e9997bae423585da52d7cdc8951379f5bff07adb6756ffe70e7c7181f8a5bd41 33 0x032b345f89620af75f59aa91d47cc359e4dd907816ce0652604922726025712f52>",
      "sender": {
        "tx": "6d9697ba950f86f2379eccdb8a7a3c22a17e01812a01f074fa667ee7451300d5",
        "index": 0,
        "a": "qz439w0qcqfg6zjjknmpuvzrc32mxd6cuv7dueqa4a"
      }
    }
  ],
  "output": [
    {
      "index": 0,
      "b0": {
        "opcodenum": 118
      },
      "b1": {
        "opcodenum": 169
      },
      "b2": "xhh3R/gLhRcO73ATIY57D6RBR5k=",
      "s2": "�\u0018wG�\u000b�\u0017\u000e�p\u0013!�{\u000f�AG�",
      "b3": {
        "opcodenum": 136
      },
      "b4": {
        "opcodenum": 172
      },
      "str": "<Script: OP_DUP OP_HASH160 20 0xc6187747f80b85170eef7013218e7b0fa4414799 OP_EQUALVERIFY OP_CHECKSIG>",
      "receiver": {
        "v": 6461258,
        "index": 0,
        "a": "qrrpsa68lq9c29cwaacpxgvw0v86gs28nyprgamwj8"
      }
    },
    {
      "index": 1,
      "b0": {
        "opcodenum": 118
      },
      "b1": {
        "opcodenum": 169
      },
      "b2": "fkYWt0UxhaXwcUF7tKwI4ibb75g=",
      "s2": "~F\u0016�E1���qA{��\b�&��",
      "b3": {
        "opcodenum": 136
      },
      "b4": {
        "opcodenum": 172
      },
      "str": "<Script: OP_DUP OP_HASH160 20 0x7e4616b7453185a5f071417bb4ac08e226dbef98 OP_EQUALVERIFY OP_CHECKSIG>",
      "receiver": {
        "v": 4129604,
        "index": 1,
        "a": "qplyv94hg5cctf0sw9qhhd9vpr3zdkl0nq0gw2gwj7"
      }
    }
  ]
}
```

## 2. fromTx

Generate bitdb document format from raw transaction string.

The following code does the same thing as the `fromHash` example above, but doesn't require a bitcoin node since it's directly transforming from raw transaction.

```
const TNA = require('tna');
(async function() {
  let result = await TNA.fromTx("0100000001d5001345e77e66fa74f0012a81017ea1223c7a8adbcc9e37f2860f95ba97966d000000006b483045022100c1a0c5ffc5b78e39acb5be1438e28a10e5aac8337f5da7e4c25ba4c5f3eb01b5022050e9997bae423585da52d7cdc8951379f5bff07adb6756ffe70e7c7181f8a5bd4121032b345f89620af75f59aa91d47cc359e4dd907816ce0652604922726025712f52ffffffff024a976200000000001976a914c6187747f80b85170eef7013218e7b0fa441479988ac44033f00000000001976a9147e4616b7453185a5f071417bb4ac08e226dbef9888ac00000000")
  console.log(result)
})();
```
