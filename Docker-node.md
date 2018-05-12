[![Docker Pulls](https://img.shields.io/docker/pulls/nanocurrency/nano.svg)](https://hub.docker.com/r/nanocurrency/nano/)

The fastest way to set up a Nano node is via a docker container from DockerHub.  You'll need a semi-recent version of Docker, Client Version ~ 1.5.0.

### Installation instructions

https://docs.docker.com/engine/installation

### Pulling Docker image

```bash
sudo docker pull nanocurrency/nano
```

### Running

```bash
sudo docker run -d -p 7075:7075/udp -p 7075:7075 -p [::1]:7076:7076 -v ~:/root --restart=unless-stopped nanocurrency/nano
```

This command:

* Starts the docker container as a daemon `-d`
* Maps the network activity port `-p 7075:7075/udp`
* Maps the bootstrapping TCP port `-p 7075:7075`
* Maps the RPC control port to the local adapter only `-p [::1]:7076:7076`
* Maps the host's home directory to the guest /root directory `~:/root`
* Restarts the container if it crashes `--restart=unless-stopped`
* Specifies the container to execute `nanocurrency/nano`

This will put the data in a permanent location in your hosts's home directory, outside the docker container.

### Troubleshooting

If you get `Error starting userland proxy: port is not a proto:IP:port: 'tcp:[:'.` or want to expose IPv4 port, use `-p 127.0.0.1:7076:7076`.

If you get `create ~: volume name is too short, names should be at least two alphanumeric characters.` replace the `~` with the full pathname such as `/Users/someuser`.

### Setting up a wallet and adding accounts

You'll need the container ID for the following commands. You can get it with `sudo docker ps` e.g. `d9416b274092`. Replace `<CONTAINERID>` with that ID.

First create a new wallet:

```bash
sudo docker exec <CONTAINERID> /usr/bin/rai_node --wallet_create
```

You should get a wallet ID which you need in the next step.

```bash
sudo docker exec <CONTAINERID> /usr/bin/rai_node --account_create --wallet=<WALLETID>
```

You get a new Nano address starting with xrb_1234… back.

To get your seed execute:

```bash
sudo docker exec <CONTAINERID> /usr/bin/rai_node --wallet_decrypt_unsafe --wallet=<WALLETID>
```

More information about the wallet backup is available here: [Wallet Backups](https://github.com/nanocurrency/raiblocks/wiki/Wallet-Backups)

Restart your container afterwards:

```bash
sudo docker restart <CONTAINERID>
```

### RPC interface

You can use the RPC interface on the local host via `curl`.

For example the version of the node:

```bash
curl -d '{ "action" : "version" }' [::1]:7076
```

Or the blockcount:

```bash
curl -d '{ "action" : "block_count" }' [::1]:7076
```

All available RPC commands are listed here: [RPC protocol](https://github.com/nanocurrency/raiblocks/wiki/RPC-protocol)

### Updating

To update your container you need to rebuild it.

**Make sure that you have your seed backup up!**

First stop your old container:

```bash
sudo docker stop <CONTAINERID>
```

Then remove it:

```bash
sudo docker rm <CONTAINERID>
```

Then pull the new image and run the image just like you did at first start.

### Usability

You can find reference material for using docker here: https://docs.docker.com/engine/reference/commandline/

You can create a custom name for your container at the `docker run`command by adding e.g. `--name nanonode`.

Once set up, using bashrc to create an alias can save you time.

For example (when `nanonode` is the name your docker container):

`sudo docker exec nanonode /usr/bin/rai_node --diagnostics`

Can be shortened to:

`rai --diagnostics`

By editing ~/.bashrc to add the alias:

`alias rai='sudo docker exec nanonode /usr/bin/rai_node'`