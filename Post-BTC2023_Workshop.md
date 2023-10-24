# ขั้นตอนการติดตั้ง Raspiblitz และใช้งาน Bitcoin Core

## เตรียมข้อมูล Bitcoin Blockchain

### Create ext4 Filesystem

~~~
# identify the USB connected disk
lsblk
df -h
# select the disk carefully
disk="/dev/sde"
# create data partition to the full size of the disk
$ parted ${disk} --align opt \
mkpart ext4 1 100%
# create ext4 filesystem
sudo mkfs.ext4 -L data ${disk}1
# mount filesystem
sudo ${disk}1 /mnt/hdd2
~~~

### Copy Blockchain Data

~~~
$ sudo rsync -a --info=progress2 /media/tee/BLOCKCHAIN/bitcoin /media/tee/BLOCKCHAIN1
$ rsync -a --info=progress2 --delete ${pathTemplateHDD}/* /mnt/hdd2
~~~

## สร้าง SD Card หรือ Flash Drive สำหรับบู๊ต Raspiblitz

การสร้าง Raspiblitz จำเป็นต้อง Flash Boot Device สามารถดาวน์โหลดไฟล์ image สำหรับเครื่องของเรา แยกเป็น 2 ประเภทคือ Raspberry Pi และ Intel X86 ได้ดังนี้

### Raspberry Pi
link https://raspiblitz.fulmo.org/images/raspiblitz-min-v1.10.0-2023-09-22.img.gz
### Intel X86 Base Machine
link https://teemie1-relay.duckdns.org:8088/raspiblitz-amd64-v1.10.0-2023-10-24-32G-ubuntu.img.gz

โปรแกรมสำหรับใช้ Flash สามารถใช้ balenaEtcher ซึ่งดาวน์โหลดได้จาก [Link](https://etcher.balena.io/#download-etcher)
สำหรับ device ที่ใช้สำหรับ flash สำหรับแต่ละ platform จะต่างกัน ถ้าใช้ raspberry pi จะใช้ SD Card ขนาด 32 GB ส่วนถ้าเป็น Intel X86 จำเป็นต้องใช้ flashdrive ขนาดอย่างน้อย 32 GB ซึ่งขั้นตอนการ flash นั้นเหมือนกันทั้ง 2 platform

### ประกอบเครื่องและบู๊ต Raspiblitz

เมื่อเราคัดลอก Bitcoin Blockchain Data บน SSD สำเร็จและ flash boot device เสร็จเรียบร้อยแล้ว เราจึงนำ SSD และ SD Card (หรือ flashdrive ขึ้นอยู่กับ platform) ประกอบเข้าด้วยกัน เชื่อมต่อสายไฟ สายแลน และต่อจอมอนิเตอร์เพื่อบู๊ตด้วย SD Card (หรือ flashdrive) เมื่อบู๊ตสำเร็จจึงขึ้นจอมอนิเตอร์ดังนี้
<img src="https://github.com/raspiblitz/raspiblitz/raw/v1.10/pictures/lcd0-welcome.png" />


#### Check Permission
~~~
$ ls -al /home
$ chmod 755 /home/admin
~~~

#### Internet Connection
~~~
$ ping 8.8.8.8
$ ping google.com
$ nslookup google.com
$ cat /etc/resolv.conf
nameserver 8.8.8.8
nameserver 8.8.4.4

~~~

#### Verify Tor Network
~~~
$ sudo systemctl status tor
● tor.service - Anonymizing overlay network for TCP (multi-instance-master)
     Loaded: loaded (/lib/systemd/system/tor.service; enabled; vendor preset: enabled)
     Active: active (exited) since Sun 2023-10-15 04:48:35 UTC; 37min ago
   Main PID: 802 (code=exited, status=0/SUCCESS)
        CPU: 1ms

Oct 15 04:48:35 raspiblitz systemd[1]: Starting Anonymizing overlay network for TCP (multi-instance-master)...
Oct 15 04:48:35 raspiblitz systemd[1]: Finished Anonymizing overlay network for TCP (multi-instance-master).

$ curl -x socks5h://localhost:9050 -s https://check.torproject.org/api/ip
{"IsTor":true,"IP":"149.56.22.133"}
~~~
#### Verify Bitcoin Core
~~~
$ sudo systemctl status bitcoind
● bitcoind.service - Bitcoin daemon on mainnet
     Loaded: loaded (/etc/systemd/system/bitcoind.service; enabled; vendor preset: enabled)
     Active: active (running) since Sun 2023-10-15 05:25:14 UTC; 1min 58s ago
    Process: 312259 ExecStartPre=/home/admin/config.scripts/bitcoin.check.sh prestart mainnet (code=exited, status=0/SUCCESS)
    Process: 312270 ExecStart=/usr/local/bin/bitcoind -daemonwait -conf=/mnt/hdd/bitcoin/bitcoin.conf -datadir=/mnt/hdd/bitcoin (code=exited, status=0/SUCCESS)
   Main PID: 312271 (bitcoind)
      Tasks: 18 (limit: 9081)
     Memory: 5.8G
        CPU: 2min 17.607s
     CGroup: /system.slice/bitcoind.service
             └─312271 /usr/local/bin/bitcoind -daemonwait -conf=/mnt/hdd/bitcoin/bitcoin.conf -datadir=/mnt/hdd/bitcoin

Oct 15 05:25:07 raspiblitz systemd[1]: Starting Bitcoin daemon on mainnet...
Oct 15 05:25:14 raspiblitz systemd[1]: Started Bitcoin daemon on mainnet.

$ bitcoin-cli -getinfo
Chain: main
Blocks: 812255
Headers: 812255
Verification progress: 99.9998%
Difficulty: 57321508229258.04

Network: in 2, out 11, total 13
Version: 250000
Time offset (s): 0
Proxies: 127.0.0.1:9050 (ipv4, ipv6, onion, cjdns)
Min tx relay fee rate (BTC/kvB): 0.00001000

Warnings: (none)

$ bitcoin-cli getblockchaininfo
{
  "chain": "main",
  "blocks": 812255,
  "headers": 812255,
  "bestblockhash": "00000000000000000002d91f8bc797b28d22a82b5919b637c1b26293b81c1048",
  "difficulty": 57321508229258.04,
  "time": 1697347110,
  "mediantime": 1697345448,
  "verificationprogress": 0.9999972595489079,
  "initialblockdownload": false,
  "chainwork": "000000000000000000000000000000000000000059186bd13ec3fa7bb0557f80",
  "size_on_disk": 588454820953,
  "pruned": false,
  "warnings": ""
}

$ bitcoin-cli getpeerinfo | grep \"addr\"
    "addr": "127.0.0.1:50632",
    "addr": "3dlf22xklplcrmwu7mwajukqemfu7jew75zysguei3g5cdmhppb2idid.onion:8333",
    "addr": "jqg3wpmlsp2hdatpl3makym7b2ffs6p5se3z6quw55meeduarwrgatad.onion:8333",
    "addr": "5g72ppm3krkorsfopcm2bi7wlv4ohhs4u4mlseymasn7g7zhdcyjpfid.onion:8333",
    "addr": "vheyznheu4wc3wwnrgx4wmwui6yyvjnl3q7cx3lzxfcoj5yyizkywwad.onion:8333",
    "addr": "6saadjlcre5bf2ajzsedxgiqyiughbk7vthqbbn37srhxgxslcnzovyd.onion:8333",
    "addr": "127.0.0.1:55136",
    "addr": "yv7ainbyxz6wejjhpjgzx6ghcomdwd3k7fclru4woooxcovyjwrp7dqd.onion:8333",
    "addr": "fgoaw2osm2jpxxxtudf7c43ar7jna6cgqlm7txyr2oen67c37doxe2id.onion:8333",
    "addr": "nigkr23k4xdsmqtoepgepvnmh33b6wnw2zsrbdu7r7unjvrv36wrcjqd.onion:8333",
    "addr": "ck5kmfvxcmuqfs3ful5pvssz467a6dgpmxbj6bylrzzyup6mutwsrnad.onion:8333",
    "addr": "jnrmetwubjv3zaz76nimxtladgirgrqjvxfjfpxz63dsymhm6nbh5tad.onion:8333",
    "addr": "d7hj5zeyqqyhc5fm5rfedwk5qmxivd276xoqkvrsnvvxnobtyrtm5iyd.onion:8333",

$ bitcoin-cli getnetworkinfo
{
  "version": 250000,
  "subversion": "/Satoshi:25.0.0/",
  "protocolversion": 70016,
  "localservices": "000000000000040d",
  "localservicesnames": [
    "NETWORK",
    "BLOOM",
    "WITNESS",
    "NETWORK_LIMITED"
  ],
  "localrelay": true,
  "timeoffset": 0,
  "networkactive": true,
  "connections": 12,
  "connections_in": 2,
  "connections_out": 10,
  "networks": [
    {
      "name": "ipv4",
      "limited": true,
      "reachable": false,
      "proxy": "127.0.0.1:9050",
      "proxy_randomize_credentials": true
    },
    {
      "name": "ipv6",
      "limited": true,
      "reachable": false,
      "proxy": "127.0.0.1:9050",
      "proxy_randomize_credentials": true
    },
    {
      "name": "onion",
      "limited": false,
      "reachable": true,
      "proxy": "127.0.0.1:9050",
      "proxy_randomize_credentials": true
    },
    {
      "name": "i2p",
      "limited": true,
      "reachable": false,
      "proxy": "",
      "proxy_randomize_credentials": false
    },
    {
      "name": "cjdns",
      "limited": true,
      "reachable": false,
      "proxy": "127.0.0.1:9050",
      "proxy_randomize_credentials": true
    }
  ],
  "relayfee": 0.00001000,
  "incrementalfee": 0.00001000,
  "localaddresses": [
    {
      "address": "rr7jonkwzi7opwrytefpz2qfopsabd2lgsoskmrjzairfmhhr5rxquid.onion",
      "port": 8333,
      "score": 4
    }
  ],
  "warnings": ""
}

~~~