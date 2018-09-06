# Nano Beta Network

The Nano beta network allows developers and interested people to test new features and helps to improve the stability of the network without influencing the main network.

## Create a new Node 

The beta node uses port 54000 TCP/UDP for communication and 55000 for RPC (at default).
All configuration files etc. will be created at `~\RaiBlocksBeta`.

### Docker

```bash
sudo docker run -d -p 54000:54000/udp -p 54000:54000 -p [::1]:55000:55000 -v ~:/root --name nanonodebeta --restart=unless-stopped nanocurrency/nano-beta
```

### Build

_TODO_

## Websites

* https://beta.nano.org/ - Official site and Faucet
* https://beta.nanocrawler.cc/ - Explorer
* https://nanode21.cloud/testnetstats.php - Nodes and Stats
* https://beta.nanoticker.info/ - TPS
