# Chain ID and Address Format

## Chain ID

Crypto.org Chain has different Chain ID to distinguish between _devnet_, _testnet_ and _mainnet_. When running the Crypto.org Chain in your local environment, you will also need to decide your own Chain ID.

For example, our testnet Chain ID is `testnet-croeseid-3`.

## Address prefix

[BIP-0173](https://github.com/satoshilabs/slips/blob/master/slip-0173.md) defines a new format for segregated witness output addresses that contains a human-readable part that identifies the coin type. Crypto.org Chain has different address prefixes for its corresponding network types, these prefixes are:

| Mainnet | Testnet | Devnet |
| ------- | ------- | ------ |
| `cro`   | `tcro`  | `dcro` |

Crypto.org Chain uses the Bech32 address format wherever users must handle binary data. Bech32 encoding provides robust integrity checks on data and the human readable part(HRP) that provides contextual hints that can assist UI developers with providing informative error messages. Specifically, we have the following HRP prefix for different addresses types in the mainnet:

|                    | Address bech32 Prefix |
| ------------------ | --------------------- |
| Account            | `cro`                 |
| Validator Operator | `crocncl`             |
| Consensus Nodes    | `crocnclcons`         |

We can use the `keys show` command of `chain-maind` with the flag `--bech <type> (acc|val|cons) ` to obtain the addresses and keys as mentioned above: for example,

```
$ chain-maind keys show test --bech acc
    - name: test0
    type: local
    address: cro1zdlttjrqh9jsgk2l8tgn6f0kxlfy98s3zwpck7
    pubkey: cropub1addwnpepq0ua07k8p3vrv5dap4pl77n4gjyyqsqrndzu0tdrr60ddhfg6ah0c4mu5gw
    mnemonic: ""
    threshold: 0
    pubkeys: []

$ chain-maind keys show test --bech val
    - name: test0
    type: local
    address: crocncl1zdlttjrqh9jsgk2l8tgn6f0kxlfy98s3prz35z
    pubkey: crocnclpub1addwnpepq0ua07k8p3vrv5dap4pl77n4gjyyqsqrndzu0tdrr60ddhfg6ah0ck5ad5l
    mnemonic: ""
    threshold: 0
    pubkeys: []

$ chain-maind keys show test --bech cons
    - name: test0
    type: local
    address: crocnclcons1zdlttjrqh9jsgk2l8tgn6f0kxlfy98s34pfmlc
    pubkey: crocnclconspub1addwnpepq0ua07k8p3vrv5dap4pl77n4gjyyqsqrndzu0tdrr60ddhfg6ah0ch6kdrc
    mnemonic: ""
    threshold: 0
    pubkeys: []
```
