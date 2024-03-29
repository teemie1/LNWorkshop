# Lightning Network Fundamental Workshop
<img src="btc-ln-2024-link.png"  width="40%" height="40%"/>

 - https://github.com/teemie1/LNWorkshop/blob/main/2024-02_BTC-LN_Workshop.md
 - http://tinyurl.com/btc-ln-2024


## Introduction

### Workshop Architecture
 - Workshop นี้จะมีการแบ่งกลุ่มผู้เรียนออกเป็นทั้งหมด 8 กลุ่ม โดยแต่ละกลุ่มได้มีหน้าที่ดูแล Lightning Node จำนวน 1 เครื่อง ดังนี้

<img src="node-diagram-01.png"  width="40%" height="40%"/>

|No.| Name |SW|IP Address     |Domain Name        |all_users_password |RTL|Thunder hub|LNDg|Seed & LNDg Password|LNbits Superuser|
|---|----------|--------|---------------|-------------------|---------------|---|----------|-|---|-------|
| 1 |  node01  |  LND   | 209.97.165.151 |node01.satsdays.com|BTC-LN_W0rk$h0p|[Link](https://node09.satsdays.com:4001/rtl/login)|[Link](https://satsdays.com:4002/)| [Link](http://node01.satsdays.com:8889/) |[Link](https://docs.google.com/spreadsheets/d/1XJwQTcZhcGYICkqOXlmo-uinYKcIBEXP4U5_Yw2ejN4/edit#gid=1304207126)|[Link](https://node01.satsdays.com/admin?usr=9a899a2daac041108cf506002959da7c)|
| 2 |  node02  |  LND   | 143.198.83.14 |node02.satsdays.com|BTC-LN_W0rk$h0p|[Link](https://node09.satsdays.com:4001/rtl/login)|[Link](https://satsdays.com:4002/)| [Link](http://node02.satsdays.com:8889/) |[Link](https://docs.google.com/spreadsheets/d/1XJwQTcZhcGYICkqOXlmo-uinYKcIBEXP4U5_Yw2ejN4/edit#gid=116730586)|[Link](https://node02.satsdays.com/admin?usr=416d6b5301aa4bf0a5ad3a6eb5db31ee)|
| 3 |  node03  |  LND   | 159.65.11.69 |node03.satsdays.com|BTC-LN_W0rk$h0p|[Link](https://node09.satsdays.com:4001/rtl/login)|[Link](https://satsdays.com:4002/)| [Link](http://node03.satsdays.com:8889/) |[Link](https://docs.google.com/spreadsheets/d/1XJwQTcZhcGYICkqOXlmo-uinYKcIBEXP4U5_Yw2ejN4/edit#gid=1070803002)|[Link](https://node03.satsdays.com/admin?usr=81aee542aaa247769858e4ae1b2ec700)|
| 4 |  node04  |  LND   | 178.128.223.181 |node04.satsdays.com|BTC-LN_W0rk$h0p|[Link](https://node09.satsdays.com:4001/rtl/login)|[Link](https://satsdays.com:4002/)| [Link](http://node04.satsdays.com:8889/) |[Link](https://docs.google.com/spreadsheets/d/1XJwQTcZhcGYICkqOXlmo-uinYKcIBEXP4U5_Yw2ejN4/edit#gid=1960160541)|[Link](https://node04.satsdays.com/admin?usr=51ee5e28929f41c39edc24af8033b3a1)|
| 5 |  node05  |  LND   | 167.71.220.141 |node05.satsdays.com|BTC-LN_W0rk$h0p|[Link](https://node09.satsdays.com:4001/rtl/login)|[Link](https://satsdays.com:4002/)| [Link](http://node05.satsdays.com:8889/) |[Link](https://docs.google.com/spreadsheets/d/1XJwQTcZhcGYICkqOXlmo-uinYKcIBEXP4U5_Yw2ejN4/edit#gid=1066962262)|[Link](https://node05.satsdays.com/admin?usr=5656c0726b204b1586de4ef20c65139a)|
| 6 |  node06  |  LND   | 178.128.216.88 |node06.satsdays.com|BTC-LN_W0rk$h0p|[Link](https://node09.satsdays.com:4001/rtl/login)|[Link](https://satsdays.com:4002/)| [Link](http://node06.satsdays.com:8889/) |[Link](https://docs.google.com/spreadsheets/d/1XJwQTcZhcGYICkqOXlmo-uinYKcIBEXP4U5_Yw2ejN4/edit#gid=693880070)|[Link](https://node06.satsdays.com/admin?usr=a0c9c57ce4bd40e0900ca31431a76e00)|
| 7 |  node07  |  LND   | 209.97.173.123 |node07.satsdays.com|BTC-LN_W0rk$h0p|[Link](https://node09.satsdays.com:4001/rtl/login)|[Link](https://satsdays.com:4002/)| [Link](http://node07.satsdays.com:8889/) |[Link](https://docs.google.com/spreadsheets/d/1XJwQTcZhcGYICkqOXlmo-uinYKcIBEXP4U5_Yw2ejN4/edit#gid=129394141)|[Link](https://node07.satsdays.com/admin?usr=24be5aeb6db24b91bded5bf6c0c93089)|
| 8 |  node08  |  LND   |146.190.96.228 |node08.satsdays.com|BTC-LN_W0rk$h0p|[Link](https://node09.satsdays.com:4001/rtl/login)|[Link](https://satsdays.com:4002/)| [Link](http://node08.satsdays.com:8889/) |[Link](https://docs.google.com/spreadsheets/d/1XJwQTcZhcGYICkqOXlmo-uinYKcIBEXP4U5_Yw2ejN4/edit#gid=709637060)|[Link](https://node08.satsdays.com/admin?usr=ac65dfacf1a840f2837da3455c2cdfdb)|
| 9 |  node09  |  CLN   |128.199.144.192|node09.satsdays.com|BTC-LN_W0rk$h0p|[Link](https://node09.satsdays.com:4001/rtl/login)| - | - | - |[Link](https://node09.satsdays.com/wallet?usr=844627c9e2564841ab88f295e6de7dd0)|
|10 |  node10  |  Eclair|146.190.111.127|node10.satsdays.com|BTC-LN_W0rk$h0p|[Link](https://node09.satsdays.com:4001/rtl/login)| - | - | - |[Link](https://node10.satsdays.com/admin?usr=b4243c86d5b34969baea0cca463af07a)|
|11 |  node11  |  CLN   |128.199.144.192|node09.satsdays.com|BTC-LN_W0rk$h0p|[Link](https://node09.satsdays.com:4001/rtl/login)| -     | - | -  | -     |
|12 |  node12  |  LND   |128.199.144.192|node09.satsdays.com|BTC-LN_W0rk$h0p|[Link](https://node09.satsdays.com:4001/rtl/login)| -     | -  | -     |

  สำหรับ node01 - node08 จะเป็นเครื่องของแต่ละกลุ่มสำหรับใช้งานร่วมกันใน workshop แต่ละเครื่องจะมีเครื่องมือที่สำคัญดังนี้
 - lncli เป็นคำสั่งหรือ command line เพื่อสั่งงานต่าง ๆ กับ node เราสามารถเข้าถึง command line ได้ด้วย [putty](https://the.earth.li/~sgtatham/putty/latest/w64/putty.exe) หรือ [MobaXterm](https://download.mobatek.net/2232022120824733/MobaXterm_Portable_v22.3.zip)
   - user: admin
   - password: BTC-LN_W0rk$h0p  
 - Right The Lightning หรือ RTL เป็นเครื่อง GUI สำหรับการบริหารจัดการ Lightning Node โดย RTL สามารถรองรับได้ทั้ง LND, Core Lightning และ Eclair
   - password: BTC-LN_Work$h0p
 - Thunderhub ทำหน้าที่ Node Management เช่นเดียวกับ RTL แต่รองรับได้เฉพาะ LND เท่านั้น
   - password: BTC-LN_Work$h0p
 - LNDg เป็นเครื่องมือระดับสูงสามารถใช้งานได้ทั้ง Node Management และ Auto Rebalance และรองรับเฉพาะ LND เท่านั้น
   - user: lndg-admin
   - password: เช็ดได้ที่ [link](https://docs.google.com/spreadsheets/d/1XJwQTcZhcGYICkqOXlmo-uinYKcIBEXP4U5_Yw2ejN4/edit#gid=0)
 - LNbits เป็นเครื่องมือในการให้บริการทางการเงินบน node ของตัวเอง สามารถใช้งาน lightning wallet, LNURL, Lightning Address, Boltcard ฯลฯ โดยแยกผู้ใช้ออกเป็น 2 ระดับคือ superuser และผู้ใช้ทั่วไป
 - rebalance-lnd เป้น command line ที่ใช้สำหรับจัดการ rebalancce channel

  ส่วน node09 - node12 เป็นเครื่องส่วนกลางเพื่อให้ workshop สามารถดำเนินการได้


### 1. Creating Bitcoin Receive Address

  ในสถานะเริ่มต้น node ที่แต่ละกลุ่มได้รับจะยังไม่มี channel ใด ๆ และยังไม่มี bitcoin อยู่เลย จึงต้องเริ่มต้นด้วยการ generate bitcoin address ขึ้นมาเพื่อทำการรับ bitcoin จากผู้สอน

**Assignment #1 ให้ generate bitcoin address แบบ p2wkh จาก node ที่ได้ และนำ address นั้นใส่ในแบบฟอร์ม [link](https://docs.google.com/spreadsheets/d/1XJwQTcZhcGYICkqOXlmo-uinYKcIBEXP4U5_Yw2ejN4/edit#gid=0) ในช่องตามกลุ่มของตนเอง**
  
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


### 2. Gather Node URI for Peer Connection

**Assignment #2 ระหว่างรอรับ bitcoin ให้แต่ละกลุ่มนำ Node URI ที่เป็น clearnet บันทึกใน google sheet [link](https://docs.google.com/spreadsheets/d/1XJwQTcZhcGYICkqOXlmo-uinYKcIBEXP4U5_Yw2ejN4) ตามกลุ่มของแต่ละคน**

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

  หลังจากได้รับ bitcoin testnet เรียบร้อยแล้ว เราจึงสามารถเปิด channel กับ node อื่น ๆ เพื่อสร้าง lightning network ขึ้นได้ โดยมีวิธีเปิด channel หลายแบบดังนี้

  
### 3. Opening Single Channel 

<img src="https://lh7-us.googleusercontent.com/_aRPj9jtRxNnOrGjrLdwmwN7OpXUi5NX6O0pc1vIvgkTvyu2mISKH5YxekqCIR8u3cjxEk_FxbbVb7EQ8JHF7FFI7L1vzDPsniUW2qVC7Q8uKUVzAuJ_q1yskTnE07mW6PQEe6up2mpsS1ofc7KFEwo"  width="80%" height="80%"/>

**Assignment #3 ให้เปิด channel กับ node ของกลุ่มอื่นตามตารางด้านล่าง**

<img src="node-diagram-02.png"  width="40%" height="40%"/>

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


### 4. Opening Multi-Channel by Batching

**Assignment #4 ให้เปิด channel กับ node ของกลุ่มอื่นแบบ batching ตามตารางด้านล่าง**

<img src="node-diagram-03.png"  width="40%" height="40%"/>

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


### 5. Opening Channel with Push Value

**Assignment #5 ให้เปิด channel กับ node ของกลุ่มอื่นแบบ push value ตามตารางด้านล่าง**

<img src="node-diagram-04.png"  width="40%" height="40%"/>

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


### 6. Channel Backup (SCB)

**Assignment #6 ให้ตรวจสอบ channel backup ด้วยคำสั่ง**

Check channel backup file by command line.
~~~
# Find the backup file path
grep backupfilepath /data/lnd/lnd.conf

# List backup file
ls -l /data/backup/nodeXX/channel.backup
~~~


### 7. Basic Rebalancing
<img src="https://lh4.googleusercontent.com/6104rP5F6K9wSZd0pUHKeJBuW3rn6XuF9wL6zjBFE_7Ju0z0rKPY629nZ512qwIW_u6LIK9dkXGf7XKsv6v1n_K992pGu1Ln2vL62dXYTXTzvw4g81UOvbrSvs7wSKnSDhnwM_V0m86U0IJfUqqpmSU"  width="80%" height="80%"/>

**Assignment #7 ให้ปรับ fee policy เป็น 0 เพื่อรองรับ rebalancing และให้ทำ rebalance channel ตามตารางด้านล่าง**

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


### 8. Paying by Bolt11 Invoice

**Assignment #8 ให้ทำการจ่ายเงินด้วย Bolt11 Invoice จาก [link](https://docs.google.com/spreadsheets/d/1XJwQTcZhcGYICkqOXlmo-uinYKcIBEXP4U5_Yw2ejN4/edit#gid=59734591)**

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


### 9. Paying by Keysend

**Assignment #9 ให้ทำการจ่ายเงินด้วย Keysend ตารางด้านล่าง**

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


### Paying by Bolt12 Offer (CLN Only)
|No.|Node Name |Pay to |Amount (Sats)     |
|---|----------|-----------|------------------|
| 1 | node09   | node11 | 3,000        |
| 2 | node11   | node09 | 4,000        |


## Closing Lightning Channel


### 10. Mutual/Cooperative Closing Channel

**Assignment #10 ให้ปิด channel ตารางด้านล่าง**

|No.|Node Name |Close Channel to |
|---|----------|-----------|
| 1 | node01   | node09 |
| 2 | node02   | node11 |
| 3 | node03   | node09 |
| 4 | node04   | node11 |
| 5 | node05   | node09 |
| 6 | node06   | node11 |
| 7 | node07   | node00 |
| 8 | node08   | node11 |

#### lncli
~~~
# List Channels
lncli listchannels
# List Pending Channels
lncli pendingchannels

# Close Channel
lncli closechannel --chan_point [CHANNEL_POINT]

# Example
lncli closechannel --chan_point 5d5525977da0bb762866afa953cdb2d69e7fe187f51e13b188345a7121596266:2
~~~
#### RTL
~~~
Go to Menu "Lightning"--> "Peers/Channels" --> Action Menu : "Close Channel"
~~~
#### Thunderhub
~~~
Go to Menu "Channels" --> Action "Close Channel"
~~~
#### LNDg
~~~
Click at "Close a Channel"
~~~


### 11. Force Closing Channel

**Assignment #11 ให้ปิด channel แบบ forced ตารางด้านล่าง**

|No.|Node Name |Force Close Channel to |
|---|----------|-----------|
| 1 | node01   | node10 |
| 2 | node02   | node10 |
| 3 | node03   | node10 |
| 4 | node04   | node10 |
| 5 | node05   | node10 |
| 6 | node06   | node10 |
| 7 | node07   | node10 |
| 8 | node08   | node10 |

#### lncli
~~~
# Close Channel
lncli closechannel --force --chan_point [CHANNEL_POINT]

# Example
lncli closechannel --force --chan_point 7be3bd753a31d7531b1819d89453b6e6d1b1c442634d0282e1b4b7425ada0f8a:0
~~~


## 12. Recovering LND from Channel Backup

  การกู้ระบบ LND Lightning Node จำเป็นต้องใช้ข้อมูล 2 ส่วนคือ 24 word seed phase และ channel.backup 
 
 - 24 word seed phase ได้มาตอนสร้าง wallet ครั้งแรก โดย seed ของ lnd ไม่ใช่มาตรฐาน BIP39 แต่เป็น aezeed แม้จะหน้าตาเหมือนกันแต่ไม่สามารถใช้แทนกันได้
 - channel backup เป็นไฟล์ที่ได้จาก lnd จะทำการสำรองข้อมูลโดยอัตโนมัติทุกครั้งที่มีการเปิดและปิด channel

 สำหรับขั้นตอนการกู้ระบบ lnd ทำได้ดังนี้

 - ใน workshop เราจะใช้ node12 สำหรับกู้ระบบ โดยในขั้นตอนการสร้าง wallet ของ lnd ให้เลือก 'y' ดังนี้
~~~
$ lncli create -multi_file=/data/backup/nodeXX/channel.backup

WARNING: You are attempting to restore from a static channel backup (SCB) file.
This action will CLOSE all currently open channels, and you will pay on-chain fees.

Are you sure you want to recover funds from a static channel backup? (Enter y/n): y
Static Channel Backup (SCB) recovery selected!
Input wallet password:
Confirm password:

Do you have an existing cipher seed mnemonic or extended master root key you want to use?
Enter 'y' to use an existing cipher seed mnemonic, 'x' to use an extended master root key
or 'n' to create a new seed (Enter y/x/n): y

Input your 24-word mnemonic separated by spaces: xxxx xxxxx

...

!!!YOU MUST WRITE DOWN THIS SEED TO BE ABLE TO RESTORE THE WALLET!!!

---------------BEGIN LND CIPHER SEED---------------
 1. ability   2. noise   3. lift     4. document
 5. certain   6. month   7. shoot    8. perfect
 9. matrix   10. mango  11. excess  12. turkey
13. river    14. pitch  15. fluid   16. rack
17. drill    18. text   19. buddy   20. pool
21. soul     22. fatal  23. ship    24. jelly
---------------END LND CIPHER SEED-----------------

!!!YOU MUST WRITE DOWN THIS SEED TO BE ABLE TO RESTORE THE WALLET!!!

lnd successfully initialized!
~~~
