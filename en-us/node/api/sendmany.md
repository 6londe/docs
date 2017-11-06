# sendmany Method

Transfers to a batch of addresses. Change address can be specified.

> [!Note]
> You must open the wallet in the Neo-CLI node before executing this command.

## Parameter Description

`\<outputs_array> \[fee=0] \[change_address]`

- outputs_array：array. The data structure of each object in the array is as follows: 

  `{"asset": \<asset>,"value": \<value>,"address": \<address>}`
  - asset: asset ID (asset identifier) , the transaction ID of the RegistTransaction when the asset is  registered.

    For example, NEO is: c56f33fc6ecfcd0c225c4ab356fee59390af8560be0e930faebe74a6daff7c9b

    NeoGas is 602c79718b16e442de58778e148d0b1084e3b2dffd5de6b7b16cee7969282de7

    For other assets ID, you can either query using the [CLI commands](../cli.md)  `list asset`  or search in the blockchain browser. 

  - value: transfer amount

  - address: deposit address

- fee: Optional. The default value is 0.

- change_address: Optional. Change address. It is the first standard address in the wallet by default.


## Example

Request text:

```json
{
  "jsonrpc": "2.0",
  "method": "sendmany",
  "params": [[{"asset": "025d82f7b00a9ff1cfe709abe3c4741a105d067178e645bc3ebad9bc79af47d4","value": 1,"address": "AbRTHXb9zqdqn5sVh4EYpQHGZ536FgwCx2"},{"asset": "025d82f7b00a9ff1cfe709abe3c4741a105d067178e645bc3ebad9bc79af47d4","value": 1,"address": "AbRTHXb9zqdqn5sVh4EYpQHGZ536FgwCx2"}]],
  "id": 1
}
```

Response text:

```json
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": {
        "txid": "27b9a82ed519eec17c5520927b3f472e4df28b835c24dba25645e1650ed8d2ac",
        "size": 322,
        "type": "ContractTransaction",
        "version": 0,
        "attributes": [],
        "vin": [
            {
                "txid": "8674c38082e59455cf35cee94a5a1f39f73b617b3093859aa199c756f7900f1f",
                "vout": 0
            }
        ],
        "vout": [
            {
                "n": 0,
                "asset": "025d82f7b00a9ff1cfe709abe3c4741a105d067178e645bc3ebad9bc79af47d4",
                "value": "1",
                "address": "AbRTHXb9zqdqn5sVh4EYpQHGZ536FgwCx2"
            },
            {
                "n": 1,
                "asset": "025d82f7b00a9ff1cfe709abe3c4741a105d067178e645bc3ebad9bc79af47d4",
                "value": "1",
                "address": "AbRTHXb9zqdqn5sVh4EYpQHGZ536FgwCx2"
            },
            {
                "n": 2,
                "asset": "025d82f7b00a9ff1cfe709abe3c4741a105d067178e645bc3ebad9bc79af47d4",
                "value": "999998",
                "address": "AbRTHXb9zqdqn5sVh4EYpQHGZ536FgwCx2"
            }
        ],
        "sys_fee": "0",
        "net_fee": "0",
        "scripts": [
            {
                "invocation": "40844144eb6819cb094afee2db5e5da078cfc7bbe29dbc60e47b4c3b4bdf77a5fd97865ae9b5a8d8bb3fa20f1441a58a05f848b2ea49c6c0dbbfc5ed241b226665",
                "verification": "210208c5203d32f960c54c225f140c1020408b114c15d29082fc959dac6874828fccac"
            }
        ]
    }
}
```

Response Description:

Returning of the transaction details as above indicates the transaction was sent successfully. If not, the transaction has failed to send.

If the JSON format is wrong, Parse error is returned.                                                                                                                                         

If the signature is incomplete, the transaction to be signed is returned.

If the balance is insufficient, an error message is returned.