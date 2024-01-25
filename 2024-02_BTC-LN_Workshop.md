# Lightning Network Fundamental

## Introduction

### Workshop Architecture

|No.|Node Name |Software|IP Address     |Domain Name        |admin password |RTL|Thunderhub|LNDg|LNbits Superuser|
|---|----------|--------|---------------|-------------------|---------------|---|----------|---|-------|
| 1 |  node01  |  LND   |               |node01.satsdays.com|BTC-LN_W0rk$h0p|[Link](https://node09.satsdays.com:4001/rtl/login)|[Link](https://satsdays.com:4002/)| [Link](http://node01.satsdays.com:8889/) |[Link](https://node01.satsdays.com/admin?usr=)|
| 2 |  node02  |  LND   |               |node02.satsdays.com|BTC-LN_W0rk$h0p|[Link](https://node09.satsdays.com:4001/rtl/login)|[Link](https://satsdays.com:4002/)| [Link](http://node02.satsdays.com:8889/) |[Link](https://node02.satsdays.com/admin?usr=)|
| 3 |  node03  |  LND   |               |node03.satsdays.com|BTC-LN_W0rk$h0p|[Link](https://node09.satsdays.com:4001/rtl/login)|[Link](https://satsdays.com:4002/)| [Link](http://node03.satsdays.com:8889/) |[Link](https://node03.satsdays.com/admin?usr=)|
| 4 |  node04  |  LND   |               |node04.satsdays.com|BTC-LN_W0rk$h0p|[Link](https://node09.satsdays.com:4001/rtl/login)|[Link](https://satsdays.com:4002/)| [Link](http://node04.satsdays.com:8889/) |[Link](https://node04.satsdays.com/admin?usr=)|
| 5 |  node05  |  LND   |               |node05.satsdays.com|BTC-LN_W0rk$h0p|[Link](https://node09.satsdays.com:4001/rtl/login)|[Link](https://satsdays.com:4002/)| [Link](http://node05.satsdays.com:8889/) |[Link](https://node05.satsdays.com/admin?usr=)|
| 6 |  node06  |  LND   |               |node06.satsdays.com|BTC-LN_W0rk$h0p|[Link](https://node09.satsdays.com:4001/rtl/login)|[Link](https://satsdays.com:4002/)| [Link](http://node06.satsdays.com:8889/) |[Link](https://node06.satsdays.com/admin?usr=)|
| 7 |  node07  |  LND   |               |node07.satsdays.com|BTC-LN_W0rk$h0p|[Link](https://node09.satsdays.com:4001/rtl/login)|[Link](https://satsdays.com:4002/)| [Link](http://node07.satsdays.com:8889/) |[Link](https://node07.satsdays.com/admin?usr=)|
| 8 |  node08  |  LND   |146.190.96.228 |node08.satsdays.com|BTC-LN_W0rk$h0p|[Link](https://node09.satsdays.com:4001/rtl/login)|[Link](https://satsdays.com:4002/)| [Link](http://node08.satsdays.com:8889/) |[Link](https://node08.satsdays.com/admin?usr=ac65dfacf1a840f2837da3455c2cdfdb)|
| 9 |  node09  |  CLN   |128.199.144.192|node09.satsdays.com|BTC-LN_W0rk$h0p|[Link](https://node09.satsdays.com:4001/rtl/login)| - | - |[Link](https://node09.satsdays.com/wallet?usr=844627c9e2564841ab88f295e6de7dd0)|
|10 |  node10  |  Eclair|146.190.111.127|node10.satsdays.com|BTC-LN_W0rk$h0p|[Link](https://node09.satsdays.com:4001/rtl/login)| - | - |[Link](https://node10.satsdays.com/admin?usr=b4243c86d5b34969baea0cca463af07a)|
|11 |  node11  |  CLN   |          |node11.satsdays.com|BTC-LN_W0rk$h0p|   |      |
|12 |  node12  |  LND   |          |node12.satsdays.com|BTC-LN_W0rk$h0p|   |      |


### Creating Bitcoin Receive Address

#### lncli
~~~
# Generate address
lncli newaddress p2wkh

# Check the balance
lncli walletbalance
~~~
#### RTL
~~~
Go to Menu "On-chain"--> "Generate Address"
~~~
#### Thunderhub
~~~
Go to Menu "Home" --> "⚓Receive"
~~~
#### LNDg
~~~
Click at "New Onchain Address"
~~~
เมื่อสร้าง address สำหรับการรับ testnet bitcoin เรียบร้อยแล้วให้นำไปใส่ใน google sheet ที่ [link](https://docs.google.com/spreadsheets/d/1XJwQTcZhcGYICkqOXlmo-uinYKcIBEXP4U5_Yw2ejN4) ตามกลุ่มของแต่ละคน

### Gather Node URI for Peer Connection
#### lncli
~~~
lncli getinfo
~~~
#### RTL
~~~
Go to Menu "Publiv Key" --> "Node URI1"
~~~
#### Thunderhub
~~~
Go to Menu "Home" --> "Connect"
~~~
#### LNDg
~~~
Look at "Addresses"
~~~
เมื่อทราบ Node URI ของกลุ่มแล้วให้นำไปใส่ใน Google Sheet เช่นกัน[link](https://docs.google.com/spreadsheets/d/1XJwQTcZhcGYICkqOXlmo-uinYKcIBEXP4U5_Yw2ejN4) ตามกลุ่มของแต่ละคน

## Opening Lightning Channel

### Opening Single Channel 

|No.|Node Name |Open Channel to|Amount (Sats)     |
|---|----------|---------------|------------------|
| 1 | node01   | node02        | 1,000,000        |
| 2 | node02   | node03        | 1,000,000        |
| 3 | node03   | node04        | 1,000,000        |
| 4 | node04   | node05        | 1,000,000        |
| 5 | node05   | node06        | 1,000,000        |
| 6 | node06   | node07        | 1,000,000        |
| 7 | node07   | node08        | 1,000,000        |
| 8 | node08   | node01        | 1,000,000        |

#### lncli (command)
~~~
lncli openchannel --connect [Target Node IP]:[Target Node Port] [Target Node ID] [Amount in Sats]

# Example:
lncli openchannel --connect 203.132.94.196:9735 038863cf8ab91046230f561cd5b386cbff8309fa02e3f0c3ed161a3aeb64a643b9 1000000
~~~
#### RTL
~~~
Go to Menu "Lightning" --> "Peers/Channels" --> "Open Channel"
~~~
#### Thunderhub
~~~
Go to Menu "Home" --> "Quick Action : Open" --> "Manual : Open" 
~~~
#### LNDg
~~~
Go to  "Open a Channel"
~~~
#### LNbits
~~~
Go to Menu "Manage : Node" --> "Channels" --> "OPEN CHANNEL"
~~~

### Opening Multi-Channel by Batching

|No.|Node Name |Open Batch Channels to|Amount (Sats)     |
|---|----------|----------------|------------------|
| 1 | node01   | node09 & node11| 500,000        |
| 2 | node02   | node09 & node11| 500,000        |
| 3 | node03   | node09 & node11| 500,000        |
| 4 | node04   | node09 & node11| 500,000        |
| 5 | node05   | node09 & node11| 500,000        |
| 6 | node06   | node09 & node11| 500,000        |
| 7 | node07   | node09 & node11| 500,000        |
| 8 | node08   | node09 & node11| 500,000        |

#### lncli (command)
~~~
lncli batchopenchannel --sat_per_vbyte=[Fee] [Channel JSON]

# Example:
  lncli batchopenchannel --sat_per_vbyte=1 '[{
    "node_pubkey": "038863cf8ab91046230f561cd5b386cbff8309fa02e3f0c3ed161a3aeb64a643b9",
    "local_funding_amount": 500000
  }, {
    "node_pubkey": "03e84a109cd70e57864274932fc87c5e6434c59ebb8e6e7d28532219ba38f7f6df",
    "local_funding_amount": 500000
  }]'

~~~

#### LNDg
~~~
Click at "Batching" --> "Batch Open Up To 10 Channels"
~~~


### Opening Channel with Push Value

|No.|Node Name |Open Channel to|Amount (Sats)     |Push Amount (Sats)|
|---|----------|---------------|------------------|--|
| 1 | node01   | node10        | 400,000        |200,000|
| 2 | node02   | node10        | 400,000        |200,000|
| 3 | node03   | node10        | 400,000        |200,000|
| 4 | node04   | node10        | 400,000        |200,000|
| 5 | node05   | node10        | 400,000        |200,000|
| 6 | node06   | node10        | 400,000        |200,000|
| 7 | node07   | node10        | 400,000        |200,000|
| 8 | node08   | node10        | 400,000        |200,000|

#### lncli (command)
~~~
lncli openchannel --connect [Target Node IP]:[Target Node Port] [Target Node ID] [Amount in Sats] [Push Amount in Sats]

# Example:
 lncli openchannel --connect 146.190.111.127:9735 025e3a294d3b13e44a704fc3a825c977e8c46d214b696d51ddf1e55f5b193ced53 200000 100000

~~~
#### Thunderhub
~~~
Go to Menu "Home" --> "Quick Action : Open" --> "Manual : Open" --> "Advanced" --> "Push Token to Partner"
~~~

#### LNbits
~~~
Go to Menu "Manage : Node" --> "Channels" --> "OPEN CHANNEL" --> "Advanced" --> "Push Amount"
~~~
### Channel Backup (SCB)
Check channel backup file by command line.
~~~
# Find the backup file path
grep backupfilepath /data/lnd/lnd.conf

# List backup file
ls -l /data/backup/nodeXX/channel.backup
~~~

## Basic Rebalancing

|No.|Node Name |From Channel|To Channel|Rebalance Amount (Sats)     |
|---|----------|------------|----|------------------|
| 1 | node01   | node02 | node08| 51,000        |
| 2 | node02   | node03 | node01| 52,000        |
| 3 | node03   | node04 | node02| 53,000        |
| 4 | node04   | node05 | node03| 54,000        |
| 5 | node05   | node06 | node04| 55,000        |
| 6 | node06   | node07 | node05| 56,000        |
| 7 | node07   | node08 | node06| 57,000        |
| 8 | node08   | node01 | node07| 58,000        |

#### rebalance-lnd (command)
~~~
sudo -iu rebalance-lnd
# Check the channel id
rebalance.py --network testnet -c

# Rebalance without reckless
rebalance.py --network testnet -f [FROM_CHANNEL] -t [TO_CHANNEL] -a [AMOUNT] --fee-limit 1000

# Rebalance with reckless
rebalance.py --network testnet -f [FROM_CHANNEL] -t [TO_CHANNEL] -a [AMOUNT] --fee-limit 1000 --reckless
~~~

#### RTL
~~~
Go to Menu "Lightning"--> "Peers/Channels" --> At Action Menu "Circular Rebalance"
~~~
#### Thunderhub
~~~
Go to Menu "Rebalance"
~~~
#### LNDg
~~~
Click at "Rebalancing"
~~~

## Lightning Payment

### Paying by Invoice

#### lncli
~~~
# Pay invoice
lncli payinvoice [INVOICE]

# Example
  lncli payinvoice lntb10u1pjmyg39pp5cg7qra7ffwt9uvcxxwsda4gp03qplzq3zzg6d36yz0rqs9t54d6qdq2w3jhxapsxgsp5xzzwdrdq6rjze83x0u4ltl8rfcpp3hm8gk385d87ng8unmes8ynsmqz9gxqrrsscqp79q2sqqqqqysgq68hc8rqzcmudru7punu6k8gq47qrqup8k05tkcjykg22svj43j3sa8w9v77uy4y5s5zazd2ne9e5hhfdw6jdcav6d6jrg2sry7yhrksq5mef2x
~~~
#### RTL
~~~
Go to Menu "Lightning"--> "Transactions" --> "Send Payment"
~~~
#### Thunderhub
~~~
Go to Menu "Home" --> "⚡Send"
~~~
#### LNbits
~~~
Go to Menu "Wallet" --> "PASTE REQUEST"
~~~

### Paying by Keysend

|No.|Node Name |keysend to |Amount (Sats)     |
|---|----------|-----------|------------------|
| 1 | node01   | node03 | 11,000        |
| 2 | node02   | node05 | 12,000        |
| 3 | node03   | node07 | 13,000        |
| 4 | node04   | node01 | 14,000        |
| 5 | node05   | node08 | 15,000        |
| 6 | node06   | node04 | 16,000        |
| 7 | node07   | node06 | 17,000        |
| 8 | node08   | node02 | 18,000        |

#### lncli
~~~
# Pay invoice
lncli sendpayment --dest [TARGET NODE ID] --amt [AMOUNT] --keysend

# Example
  lncli sendpayment --dest 02594a72bb0405de2490eea7b592f9a09365e2112e75689357caefcff65fee4044 --amt 2000 --keysend
~~~

#### Thunderhub
~~~
Go to Menu "Home" --> "⚡Send" --> "Is keysend to Yes"
~~~


### Paying by Offer (CLN Only)

## Closing Lightning Channel

### Mutual Closing Channel

### Force Closing Channel

## Recovering LND from Channel Backup
