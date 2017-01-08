---
title: Steemit API Reference

language_tabs:
  - shell

toc_footers:

includes:

search: true
---

# Introduction

Welcome to the [steemit](https://steemit.com) API and developer wiki portal! Steemit is the social media platform where everyone gets paid for creating and curating content.

The following API documents provide details on how to interact with the Steem blockchain database API which can get information on accounts, content, blocks and much more!

The developer portal will also serve as a toolbox for steem clients, libraries, and language wrappers.

The developer portal is currently in early release. Our developer portal docs are open source and
steem developers are encouraged to contribute as this becomes the ultimate developer resource for steemit.

Please visit [https://github.com/steemit/steemit-docs](https://github.com/steemit/steemit-docs)

# Architecture
Steem is a decentralized social-media platform. It is based on DPOS consensus algorithm that manage state consistency of underlying databased, [a blockchain](https://en.wikipedia.org/wiki/Blockchain_(database)), key feature of which is absence of any single administrator. This benefits involved community with algorithmic censorship protection and guaranty of immutable history.

From a developer point of view that means that there is no such thing as API keys for read operations. Any developer is able to get own source of [JSON-RPC](http://www.jsonrpc.org/specification) and [Websocket](https://developer.mozilla.org/en-US/docs/Web/API/WebSockets_API) API without necessity to ask somebody permission. Such possibility comes with costs of maintaining full blockchain node though.

In order to execute write, update and delete operations registered account is required. Anybody can register account anonymously either through mining or paying a one-time lifetime fee which defined by a consensus of delegates. Fee should be paid in STEEM, internal currency. Usually it is managed to stick $5 but may vary. Also Steemit.com [give out accounts](https://steemit.com/enter_email) for free in exchange for identity.
Blockchain set up a limit on your account's bandwidth based on STEEM POWER of you account and tracks your account's bandwidth usage effectively limiting it. Thus no transaction fees are never involved but the more bandwidth you account uses the STEEM POWER it should have. Fortunately it is possible to design an apps thus no account with huge STEEM POWER is needed. Every user interacting with your app will manage it's limits by himself.

Setup and configuration of a API node depends on application need.

## Local Node

## Self-Hosted Node

## Blockchain as a Service

# Node Installation

## Ubuntu

## OS X

## Docker

# Developer Environment
## Local Testnet

## Public Testnet

# Accounts

## Get Account Count

```shell
get_account_count
```

> The above command returns JSON structured like this:

```shell
{
"id": 2,
"result": 91171
}
```

Use this to get number of accounts registered on the blockchain

### Request

`get_account_count`

## Get Account History

```shell
get_account_history
```

> The above command returns JSON structured like this:

```shell
{
"id": 3,
"result": [
  [10, {
    "id": "2.17.929",
    "trx_id": "cd7913782657e609167f62194eea36375defbdeb",
    "block": 18717,
    "trx_in_block": 0,
    "op_in_trx": 0,
    "virtual_op": 929,
    "timestamp": "2016-03-25T08:02:33",
    "op": ["pow", {
      "worker_account": "steemit",
      "block_id": "0000491c7e73f1dddcf8f8f93f128f96930370b8",
      "nonce": "3572148442797474411",
      "work": {
        "worker": "STM65wH1LZ7BfSHcK69SShnqCAH5xdoSZpGkUjmzHJ5GCuxEK9V5G",
        "input": "81df53d541cc33591e73d626beb298951eaa58d39b5838b07bafe538ba5aa505",
        "signature": "200467a1e98e79de953dfeb767d9f193eccf3aeb197754c57c9620d8571c0cafe018caaa3186740ab987d16247318bb51239df7dfa0ad60085c023a8edabc00acf",
        "work": "0000000bb8deb767063d26a186d77c60280ce203c3fb84f59aa3627d7e95cb4a"
      },
      "props": {
        "account_creation_fee": "100.000 STEEM",
        "maximum_block_size": 131072,
        "sbd_interest_rate": 1000
      }
    }]
  }]]
}

```

This endpoint return account history

### Request

`get_account_history`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
account | string |
from | uint32_t |
limit | uint32_t |


## Get Account References

```shell
get_account_references
```

function

> The above command returns JSON structured like this:

```shell
{

}
```
### Request

`get_account_references`

### Query Parameters

Use this to get

Parameter | Type | Description
--------- | ------- | -----------
account | string |

## Get Account Votes

```shell
get_account_votes
```

> The above command returns JSON structured like this:

```shell
{

}
```

Use this to get

Parameter | Type | Description
--------- | ------- | -----------
account | string |

## Get Accounts

```shell
get_accounts
```

> The above command returns JSON structured like this:

```shell

```

Use this to get

### Request

`get_accounts`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
 accounts | string  | in nested array

# Blocks

Blocks are fundamental building bricks of Steem blockchain. Blocks are created, signed and timestamped by witnesses. Purpose of blocks is to hash all included in blocks transactions and link to hash of previuous block making databased history tamperproof. Get example of data structure on [steemd](https://steemd.com/b/7656182).


## Get Block

```shell
get_block
```

> The above command returns JSON structured like this:

```shell
{
"id": 2,
"result": {
  "previous": "003d08ff118b27e093103b580daca817342f9596",
  "timestamp": "2016-08-11T22:00:06",
  "witness": "silversteem",
  "transaction_merkle_root": "a4ed1b655c56040fd77857c2983f390fa30852cd",
  "extensions": [],
  "witness_signature": "206e7847032dd57c821fb45f880123c57a88fef17e11e4da218b7ece631d4c8338124ad02bca19710fa2376672dc2c531469f3499a208c4bf01bb990cde4ec03f0",
  "transactions": [{
    "ref_block_num": 2303,
    "ref_block_prefix": 3760687889,
    "expiration": "2016-08-11T22:00:33",
    "operations": [
      ["witness_update", {
        "owner": "supercomputing05",
        "url": "http://fxxk.com",
        "block_signing_key": "STM5b3wkzd5cPuW8tYbHpsM6qo26R5eympAQsBaoEfeMDxxUCLvsY",
        "props": {
          "account_creation_fee": "1.000 STEEM",
          "maximum_block_size": 65536,
          "sbd_interest_rate": 1000
        },
        "fee": "0.000 STEEM"
      }]
    ],
    "extensions": [],
    "signatures": []
  }
}
```

Use this to get

### Request

`get_block`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
block number | uint32_t |

## Get Block Header

```shell
get_block_header
```

> The above command returns JSON structured like this:

```shell
{
  "id": 4,
  "result": {
    "previous": "0001d4bf70af1312e019091fcd82261870744146",
    "timestamp": "2016-03-28T20:53:33",
    "witness": "steemit45",
    "transaction_merkle_root": "0000000000000000000000000000000000000000",
    "extensions": []
  }
}
```

Use this to get

### Request

`get_block_header`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
 block number | uint32_t |

# Content

## Get Content

```shell
get_content
```

> The above command returns JSON structured like this:

```shell
{
  "id": 6,
  "result": {
    "id": "0.0.0",
    "author": "",
    "permlink": "",
    "category": "",
    "parent_author": "",
    "parent_permlink": "",
    "title": "",
    "body": "",
    "json_metadata": "",
    "last_update": "1970-01-01T00:00:00",
    "created": "1970-01-01T00:00:00",
    "active": "1970-01-01T00:00:00",
    "last_payout": "1970-01-01T00:00:00",
    "depth": 0,
    "children": 0,
    "children_rshares2": "0",
    "net_rshares": 0,
    "abs_rshares": 0,
    "vote_rshares": 0,
    "children_abs_rshares": 0,
    "cashout_time": "1970-01-01T00:00:00",
    "max_cashout_time": "1970-01-01T00:00:00",
    "total_vote_weight": 0,
    "reward_weight": 23228,
    "total_payout_value": "0.000 SBD",
    "curator_payout_value": "0.000 SBD",
    "author_rewards": 0,
    "net_votes": 0,
    "root_comment": "2.8.0",
    "mode": "first_payout",
    "max_accepted_payout": "1000000.000 SBD",
    "percent_steem_dollars": 10000,
    "allow_replies": true,
    "allow_votes": true,
    "allow_curation_rewards": true,
    "url": "",
    "root_title": "",
    "pending_payout_value": "0.000 STEEM",
    "total_pending_payout_value": "0.000 STEEM",
    "active_votes": [],
    "replies": [],
    "author_reputation": 0
  }
}

```

Use this to get

### Request

`get_content`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
account | string |


## Get Content Replies

```shell
get_content_replies
```

> The above command returns JSON structured like this:

```shell

```

Use this to get

### Request

`get_content_replies`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
account | string |

# Discussions

## Get Discussions by Active

```shell
get_discussions_by_active
```

> The above command returns JSON structured like this:

```shell

```

Use this to get

### Request

`get_discussions_by_active`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
tag | string |
limit | integer |

## Get Discussions by Cashout

```shell
get_discussions_by_cashout
```

> The above command returns JSON structured like this:

```shell

```

Use this to get

### Request

`get_discussions_by_cashout`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
tag | string |
limit | integer |

## Get Discussions by Children

```shell
get_discussions_by_children
```

> The above command returns JSON structured like this:

```shell

```

Use this to get

### Request

`get_discussions_by_children`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
tag | string |
limit | integer |

## Get Discussions by Created

```shell
get_discussions_by_created
```

> The above command returns JSON structured like this:

```shell

```

Use this to get

### Request

`get_discussions_by_created`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
tag | string |
limit | integer |

## Get Discussions by Feed

```shell
get_discussions_by_feed
```

> The above command returns JSON structured like this:

```shell

```

Use this to get

### Request

`get_discussions_by_feed`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
tag | string |
limit | integer |

## Get Discussions by Hot

```shell
get_discussions_by_hot
```

> The above command returns JSON structured like this:

```shell

```

Use this to get

### Request

`get_discussions_by_hot`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
tag | string |
limit | integer |

## Get Discussions by Payout

```shell
get_discussions_by_payout
```

> The above command returns JSON structured like this:

```shell

```

Use this to get

### Request

`get_discussions_by_payout`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
tag | string |
limit | integer |

## Get Discussions by Trending

```shell
get_discussions_by_trending
```

> The above command returns JSON structured like this:

```shell

```

Use this to get

### Request

`get_discussions_by_votes`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
tag | string |
limit | integer |

## Get Discussions by Votes

```shell
get_discussions_by_votes
```

> The above command returns JSON structured like this:

```shell

```

Use this to get

### Request

`get_discussions_by_votes`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
tag | string |
limit | integer |

## Get Discussions by Author before Date

```shell
get_discussions_by_author_before_date
```

> The above command returns JSON structured like this:

```shell

```

Use this to get

### Request

`get_discussions_by_author_before_date`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
tag | string |
start_permalink | string |
before_date | integer |
limit | integer |

# Categories


## Get Trending Categories

```shell
get_trending_categories
```

> The above command returns JSON structured like this:

```shell

```

Use this to get

### Request

`get_trending_categories`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
tag | string |
limit | integer |


## Get Best Categories

```shell
get_best_categories
```

> The above command returns JSON structured like this:

```shell

```

Use this to get

### Request

`get_best_categories`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
tag | string |
limit | integer |


## Get Active Categories

```shell
get_active_categories
```

> The above command returns JSON structured like this:

```shell

```

Use this to get

### Request

`get_active_categories`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
tag | string |
limit | integer |

# Feeds

## Get Feed History

```shell
get_feed_history
```

> The above command returns JSON structured like this:

```shell
{
  "id": 5,
  "result": {
    "id": "2.14.0",
    "current_median_history": {
      "base": "0.713 SBD",
      "quote": "1.000 STEEM"
    },
    "price_history": [{
      "base": "0.797 SBD",
      "quote": "1.000 STEEM"
    }, {
      "base": "0.801 SBD",
      "quote": "1.000 STEEM"
    }, {
      "base": "0.800 SBD",
      "quote": "1.000 STEEM"
    }
  }
 }
```

Use this to get

### Request

`get_feed_history`

# Witness

## Get Active Witnesses

```shell
get_active_witnesses
```

> The above command returns JSON structured like this:

```shell
{
  "id": 14,
  "result": ["xeldal", "bitcube", "joseph", "roadscape", "clayop"]
}
```

Use this to get

### Request

`get_active_witnesses`

## Get Witness by Account

```shell
get_witness_by_account
```

> The above command returns JSON structured like this:

```shell
{
  "id": 14,
  "result": ["xeldal", "bitcube", "joseph", "roadscape", "clayop"]
}
```

Use this to get

### Request

`get_witness_by_account`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
account | string |

## Get Witness Schedule

```shell
get_witness_schedule
```

> The above command returns JSON structured like this:

```shell
{
  "id": 14,
  "result": ["xeldal", "bitcube", "joseph", "roadscape", "clayop"]
}
```

Use this to get

### Request

`get_witness_schedule`

## Get Witness Count

```shell
get_witness_count
```

> The above command returns JSON structured like this:

```shell

```

Use this to get

### Request

`get_witness_count`

## Get Witnesses by Vote

```shell
get_witnesses_by_vote
```

> The above command returns JSON structured like this:

```shell

```

Use this to get

### Request

`get_witnesses_by_vote`

# Escrow

## Escrow Transfer Operation

```shell
escrow_transfer_operation
```

> The above command returns JSON structured like this:

```shell

```

Use this to get

### Request

`escrow_transfer_operation`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
 |  |

## Escrow Approve Operation

```shell
escrow_approve_operation
```

> The above command returns JSON structured like this:

```shell

```

Use this to get

### Request

`escrow_approve_operation`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
|  |

## Escrow Dispute Operation

```shell
escrow_dispute_operation
```

> The above command returns JSON structured like this:

```shell

```

Use this to get

### Request

`escrow_dispute_operation`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
 |  |

## Escrow Release Operation

```shell
escrow_release_operation
```

> The above command returns JSON structured like this:

```shell

```

Use this to get

### Request

`escrow_release_operation`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
|  |

# Savings

## Transfer to Savings Operation

```shell
transfer_to_savings_operation
```

> The above command returns JSON structured like this:

```shell

```

Use this to get

### Request

`transfer_to_savings_operation`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
 |  |

## Transfer from Savings Operation

```shell
transfer_from_savings_operation
```

> The above command returns JSON structured like this:

```shell

```

Use this to get

### Request

`transfer_from_savings_operation`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
|  |

## Cancel Transfer From Savings Operation

```shell
cancel_transfer_from_savings_operation
```

> The above command returns JSON structured like this:

```shell

```

Use this to get

### Request

`cancel_transfer_from_savings_operation`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
 |  |

# Libraries

Listed below is the ever-growing list of steem toolkit libraries, pluggins and wrappers to make consuming steem data a breeze.

This list will frequently be updated as new Libraries/Wrappers are released.

Direct links to respective GitHub repositories along with example when available are also included.

*Categorized below is a list of development tools - if your looking for steem apps please visit [Steemtools](http://steemtools.com)*

## Piston

Python Based - Swiss army knife for interacting with the STEEM blockchain.

Command line tool to interact with the STEEM network

`https://github.com/xeroc/piston`

## Steemduino

An Open Source Arduino Library for Steem.

steemduino allows you to communicate with the Steem websocket API using an Arduino, the open source electronics platform.

`https://github.com/jonblack/steemduino`


## SteemJS ~ 1

Lightweight JavaScript library to communicate with steemd.

`https://github.com/adcpm/steem`

```javascript
<script src="./steem.min.js"></script>
<script>
steem.api.getAccounts(['ned', 'dan'], function(err, response){
    console.log(err, response);
});
</script>
```

## SteemJS ~ 2

Pure JavaScript Steem crypto library for node.js and browsers. Can be used to construct, sign and broadcast transactions in JavaScript.

`https://github.com/svk31/steemjs-lib`

```javascript
// Example generate transaction

var { TransactionBuilder, Login } = require("steemjs-lib");
var login = new Login();
login.setRoles(["posting"]);
var loginSuccess = login.checkKeys({
    accountName: "myacccount",
    password: "mypassword",
    auths: {
        posting: [["STMpostingAuthKey", 1]]
    }}
);
```

## Steem-rpc

A simple websocket wrapper enabling RPC communication with the steem client steemd for node.js and browsers.

`https://github.com/svk31/steem-rpc`

## Steemcli

A command-line client for posting content to Steem

`https://github.com/yamadapc/steemcli`
