# Run LND and Sparrow in Testnet

## Run Testnet LND
~~~
$ nohup sudo -u bitcoin /usr/local/bin/lnd \
    --listen=0.0.0.0:19735 \
    --rpclisten=0.0.0.0:11009 \
    --restlisten=0.0.0.0:18080 \
    --nat=false \
    --debuglevel=debug \
    --gc-canceled-invoices-on-startup=true \
    --gc-canceled-invoices-on-the-fly=true \
    --ignore-historical-gossip-filters=1 \
    --sync-freelist=true \
    --stagger-initial-reconnect=true \
    --tlsautorefresh=1 \
    --tlsdisableautofill=1 \
    --tlscertpath=/home/bitcoin/.lnd/tls.cert \
    --tlskeypath=/home/bitcoin/.lnd/tls.key \
    --bitcoin.active=1 \
    --bitcoin.testnet=1 \
    --bitcoin.node=bitcoind \
    --bitcoind.rpcuser=raspibolt \
    --bitcoind.rpcpass=raspiblitz \
    --bitcoind.rpchost=192.168.1.69:18332 \
    --bitcoind.zmqpubrawblock=tcp://192.168.1.69:21332 \
    --bitcoind.zmqpubrawtx=tcp://192.168.1.69:21333 \
    --db.bolt.auto-compact=true \
    --db.bolt.auto-compact-min-age=672h \
    --workers.sig=4 \
    --workers.write=4 \
    --tor.active=true \
    --tor.v3=true \
    --tor.privatekeypath=/mnt/hdd/lnd/tv3_onion_private_key \
    --tor.socks=9050 \
    --tor.control=9051 \
    --rpcmiddleware.enable=true \
    --healthcheck.chainbackend.interval=1m30s \
    --healthcheck.chainbackend.timeout=2m0s \
    --healthcheck.chainbackend.attempts=3 \
    &
	
$ alias tlncli='sudo -u bitcoin /usr/local/bin/lncli -n=testnet --rpcserver localhost:11009'

$ tlncli -getinfo
$ tlncli stop
~~~

## Run Sparrow in Testnet Mode
