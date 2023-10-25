# ขั้นตอนการติดตั้ง Raspiblitz และใช้งาน Bitcoin Core
<img src="Post-BTC2023_Workshop/Post-BTC2023_Workshop_QR.png"  width="40%" height="40%"/>

https://github.com/teemie1/LNWorkshop/blob/main/Post-BTC2023_Workshop.md


สามารถเข้าสู่หน้าเว็บนี้โดยการสแกนที่ QR Code ด้านบน

## 1. เตรียมข้อมูล Bitcoin Blockchain โดยการคัดลอกจาก Copy Station (จัดการโดยผู้สอน)
ข้อมูลของ Bitcoin Blockchain มีขนาดประมาณ 550 GB ซึ่งใช้เวลา sync ถึง 1-3 วัน เพื่อลดเวลาลงจึงใช้วิธีคัดลอกจาก Copy Station ที่เตรียมไว้ล่วงหน้า จะลดเวลาลงเหลือประมาณ 0.5-1.5 ชั่วโมงเท่านั้น

ใน workshop มีเตรียม Copy Station ไว้ 2 ชุด ดังนี้

### Raspiblitz Node
นำ SSD ขนาด 1-2 TB มาเชื่อมต่อ USB กับ Raspiblitz Node และใช้คำสั่งสำหรับคัดลอกข้อมูลดังนี้
~~~
# From Raspiblitz Menu, select Exit to command line
$ sudo /home/admin/XXcopyStation.sh

# Wait for copy blockchain data.
~~~

### Thinkpad Labtop
นำ SSD ขนาด 1-2 TB มาเชื่อมต่อ USB กับ Thinkpad และใช้คำสั่งคัดลอกดังนี้
~~~
# Open terminal windows, identify the USB connected disk
$ lsblk
$ disk="/dev/sdX"

# create data partition to the full size of the disk
$ sudo parted ${disk} --align opt mkpart ext4 1 100%

# create ext4 filesystem
$ sudo mkfs.ext4 -L data ${disk}1
$ sudo ${disk}1 /media/tee/BLOCKCHAIN2

# copy blockchain data
$ sudo rsync -a --info=progress2 /media/tee/BLOCKCHAIN/* /media/tee/BLOCKCHAIN2
$ rsync -a --info=progress2 --delete ${pathTemplateHDD}/* /mnt/hdd2
~~~
## 2. สร้าง SD Card หรือ Flash Drive สำหรับบู๊ต Raspiblitz

การสร้าง Raspiblitz จำเป็นต้อง Flash Boot Device สามารถดาวน์โหลดไฟล์ image สำหรับเครื่องของเรา แยกเป็น 2 ประเภทคือ Raspberry Pi และ Intel X86 ได้ดังนี้

### Raspberry Pi
  - flash image: [download](https://raspiblitz.fulmo.org/images/raspiblitz-min-v1.10.0-2023-09-22.img.gz) 
  - flash device: 32GB SD Card

### Intel X86 Base Machine
  - flash image: [download](https://teemie1-relay.duckdns.org:8088/raspiblitz-amd64-v1.10.0-2023-10-24-32G-ubuntu.img.gz)
  - flash device: 32GB flashdrive

จำเป็นต้องใช้โปรแกรม balenaEtcher ในการแฟลช ซึ่งดาวน์โหลดได้จาก [blenaEtcher](https://etcher.balena.io/#download-etcher)

### ประกอบเครื่องและบู๊ต Raspiblitz

  - เมื่อเราคัดลอก Bitcoin Blockchain Data บน SSD สำเร็จและ flash boot device เสร็จเรียบร้อยแล้ว เราจึงนำ SSD และ SD Card (หรือ flashdrive) ประกอบเข้าด้วยกัน เชื่อมต่อสายไฟ สายแลน และต่อจอมอนิเตอร์เพื่อบู๊ตด้วย SD Card (หรือ flashdrive) เมื่อบู๊ตสำเร็จจึงขึ้นจอมอนิเตอร์ดังนี้
<img src="https://github.com/raspiblitz/raspiblitz/raw/v1.10/pictures/lcd0-welcome.png" />

  - จดหมายเลข IP Address ที่ขึ้นบนหน้าจอ และเปิดโปรแกรมสำหรับ SSH โดยใช้ putty(สามารถดาวน์โหลดได้จาก [link](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html))
<img src="Post-BTC2023_Workshop/2023-10-23%2018%2015%2036%20(2).jpg"  width="50%" height="50%"/>

  - ใส่ username และ password ดังนี้
    - Username : admin
    - Password : raspiblitz
<img src="Post-BTC2023_Workshop/2023-10-23%2018%2015%2036%20(3).jpg"  width="70%" height="70%"/>

  - เลือกเมนู "FRESHSETUP" --> "USE BLOCKCHAIN" --> "DELETE DATA"
<img src="Post-BTC2023_Workshop/2023-10-23%2018%2015%2036%20(4).jpg"  width="70%" height="70%"/>
<img src="Post-BTC2023_Workshop/2023-10-23%2018%2015%2036%20(5).jpg"  width="70%" height="70%"/>
<img src="Post-BTC2023_Workshop/2023-10-23%2018%2015%2036%20(6).jpg"  width="70%" height="70%"/>

  - ตั้งชื่อ Node เช่น "node00"
<img src="Post-BTC2023_Workshop/2023-10-23%2018%2015%2036%20(7).jpg"  width="70%" height="70%"/>

  - เลือก lightning client เป็น "LND" --> "NEW"
<img src="Post-BTC2023_Workshop/2023-10-23%2018%2015%2036%20(8).jpg"  width="70%" height="70%"/>
<img src="Post-BTC2023_Workshop/2023-10-23%2018%2015%2036%20(9).jpg"  width="70%" height="70%"/>

  - กำหนด Password A,B,C แนะนำให้ตั้งค่า Password ทั้งสามให้ตรงกันเพื่อไม่ให้สับสน
<img src="Post-BTC2023_Workshop/2023-10-23%2018%2015%2036%20(10).jpg"  width="70%" height="70%"/>
<img src="Post-BTC2023_Workshop/2023-10-23%2018%2015%2036%20(11).jpg"  width="70%" height="70%"/>
<img src="Post-BTC2023_Workshop/2023-10-23%2018%2015%2036%20(12).jpg"  width="70%" height="70%"/>
<img src="Post-BTC2023_Workshop/2023-10-23%2018%2015%2036%20(13).jpg"  width="70%" height="70%"/>
<img src="Post-BTC2023_Workshop/2023-10-23%2018%2015%2036%20(14).jpg"  width="70%" height="70%"/>
<img src="Post-BTC2023_Workshop/2023-10-23%2018%2015%2036%20(15).jpg"  width="70%" height="70%"/>
<img src="Post-BTC2023_Workshop/2023-10-23%2018%2015%2036%20(16).jpg"  width="70%" height="70%"/>
<img src="Post-BTC2023_Workshop/2023-10-23%2018%2015%2036%20(17).jpg"  width="70%" height="70%"/>
<img src="Post-BTC2023_Workshop/2023-10-23%2018%2015%2036%20(18).jpg"  width="70%" height="70%"/>
<img src="Post-BTC2023_Workshop/2023-10-23%2018%2015%2037.jpg"  width="70%" height="70%"/>

  - รอให้ Raspiblitz ทำการ setup ทั้งหมดจนเสร็จ
<img src="Post-BTC2023_Workshop/2023-10-23%2018%2015%2037%20(5).jpg"  width="70%" height="70%"/>

  - เมื่อแสดงค่า seed ของ LND ให้จด seed ทั้ง 24 คำไว้บนกระดาษ ห้าม copy เก็บไว้บนคอมพิวเตอร์เพื่อความปลอดภัย
<img src="Post-BTC2023_Workshop/2023-10-23%2018%2015%2037%20(6).jpg"  width="70%" height="70%"/>

  - เลือก "CONTINUE" --> "OK" เสร็จแล้วระบบจำทำการ reboot เครื่อง
<img src="Post-BTC2023_Workshop/2023-10-23%2018%2015%2037%20(7).jpg"  width="70%" height="70%"/>
<img src="Post-BTC2023_Workshop/2023-10-23%2018%2015%2037%20(8).jpg"  width="70%" height="70%"/>
<img src="Post-BTC2023_Workshop/2023-10-23%2018%2015%2037%20(9).jpg"  width="70%" height="70%"/>

  - หลังจาก reboot เสร็จแล้วให้เชื่อมต่อ putty อีกครั้ง โดยเลือกที่เมนู "Restart Session"
<img src="Post-BTC2023_Workshop/2023-10-23%2018%2015%2037%20(10).jpg"  width="70%" height="70%"/>

 - ใส่ username และ password
   - Username : admin
   - Password : raspiblitz
<img src="Post-BTC2023_Workshop/2023-10-23%2018%2015%2037%20(11).jpg"  width="70%" height="70%"/>

  - ใส่ Password C ที่ได้ตั้งค่าไว้
<img src="Post-BTC2023_Workshop/2023-10-24%2018%2035%2043.png"  width="70%" height="70%"/>

  - เลือกเมนู "INFO"
<img src="Post-BTC2023_Workshop/2023-10-23%2018%2015%2038%20(6).jpg"  width="70%" height="70%"/>

  - เมื่อติดตั้งระบบ Raspiblitz สำเร็จและพร้อมใช้งานจะปรากฏภาพดังนี้
<img src="Post-BTC2023_Workshop/2023-10-23%2018%2015%2038%20(7).jpg"  width="70%" height="70%"/>

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

~~~
https://docs.google.com/spreadsheets/d/1XJwQTcZhcGYICkqOXlmo-uinYKcIBEXP4U5_Yw2ejN4/edit?usp=sharing
