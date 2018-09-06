# Nano Beta Network

## Create a new Node 

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
