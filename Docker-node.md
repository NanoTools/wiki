The fastest way to set up a Nano node is via a docker container from DockerHub.  You'll need a semi-recent version of docker, Client Version ~ 1.5.0.

### Installation instructions

https://docs.docker.com/engine/installation

### Pulling docker image 

```bash
sudo docker pull nanocurrency/nano
```  
### Running

```bash
sudo docker run -d -p 7075:7075/udp -p 7075:7075 -p [::1]:7076:7076 -v ~:/root nanocurrency/nano
```

This command:
* Starts the docker container as a daemon "-d"
* Maps the network activity port "-p 7075:7075/udp"
* Maps the bootstrapping TCP port "-p 7075:7075"
* Maps the RPC control port to the local adapter only "-p [::1]:7076:7076"
* Maps the host's home directory to the guest /root directory "~:/root"
* Specifies the container to execute "nanocurrency/nano"

This will put the data in a permanent location in your hosts's home directory, outside the docker container.

### Troubleshooting

If you get `Error starting userland proxy: port is not a proto:IP:port: 'tcp:[:'.` or want to expose IPv4 port, use `-p 127.0.0.1:7076:7076`.

If you get `create ~: volume name is too short, names should be at least two alphanumeric characters.` replace the `~` with the full pathname such as `/Users/someuser`.

### Setting up a wallet and adding accounts

`curl -d '{ "action" : "wallet_create" }' [::1]:7076`  
The response will look like:  
`{ "wallet" : "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F" }`  
The number is the wallet ID that you can use to reference this wallet in other API commands.  

`curl -d '{ "action": "account_create", "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F" }' [::1]:7076`  
The response will look like:  
`{ "account" : "xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000" }`  
This is the account number that was just created.  

Back up the wallet seed following the backup instructions https://github.com/nanocurrency/raiblocks/wiki/Wallet-Backups

### Usability

You can find reference material for using docker here: https://docs.docker.com/engine/reference/commandline/

Once set up, using bashrc to create an alias can save you time.

For example (when 97bf54657cdb is your docker container):

`sudo docker exec 97bf54657cdb /usr/bin/rai_node --diagnostics`

Can be shortened to:

`rai --diagnostics`

By editing ~/.bashrc to add the alias:

`alias rai='sudo docker exec 97bf54657cdb /usr/bin/rai_node'`