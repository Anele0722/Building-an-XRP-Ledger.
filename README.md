# Basics of Building an XRP Ledger Connected Application with XRP-py
This project is a guide to building an XRP Ledger connected application using XRP-py, a pure Python library built to interact with the XRP Ledger using native Python models and methods.

## Getting Started
To get started with this project, you will need to have the following:

+ Python 3.6 or higher
+ XRP-py library
+ Access to an XRP Ledger node

## Installation
+ Install Python 3.6 or higher

+ Install XRP-py library

```pip install xrpl-py
```

## Connecting to an XRP Ledger node

To connect to an XRP Ledger node, you can use the xrpl.core.client module in XRP-py. Here's an example of connecting to a public XRP Ledger node:


```from xrpl.clients import JsonRpcClient

client = JsonRpcClient("https://s1.ripple.com:51234/")
```


You can also connect to a local XRP Ledger node by specifying the URL of the node:


```from xrpl.clients import JsonRpcClient

client = JsonRpcClient("http://localhost:5005/")
```

## Sending XRP

To send XRP from one address to another, you can use the xrpl.transaction module in XRP-py. Here's an example of sending 10 XRP from one address to another:

```python
Copy code
from xrpl.wallet import Wallet
from xrpl.clients import JsonRpcClient
from xrpl.transaction import (
    Payment,
    Transaction,
    Wallet,
)

client = JsonRpcClient("https://s1.ripple.com:51234/")
sender = Wallet(seed="sender's secret seed")
receiver = "r12345678901234567890123"
tx = Payment(
    account=sender.classic_address,
    amount="10000000",
    destination=receiver,
    sequence=client.get_account_info(sender.classic_address)["sequence"],
    fee=12,
)
tx_signed = tx.sign(sender)
response = client.submit_transaction(tx_signed) 
```

## Checking XRP Balance

To check the XRP balance of an address, you can use the xrpl.account module in XRP-py. Here's an example of checking the XRP balance of an address:


```from xrpl.clients import JsonRpcClient
from xrpl.account import get_balance

client = JsonRpcClient("https://s1.ripple.com:51234/")
address = "r12345678901234567890123"
balance = get_balance(client, address)
print(balance)
```

## Contributing

Contributions to this project are welcome. If you find a bug or have a feature request, please open an issue or submit a pull request.

## License

This project is licensed under the MIT License - see the LICENSE file for details.
