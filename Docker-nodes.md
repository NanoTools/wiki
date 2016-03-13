The fastest way to set up a RaiBlocks node is via a docker container from DockerHub.  You'll need a semi-recent version of docker, Client Version ~ 1.5.0.

On Ubuntu 14.04 you can do:
"sudo apt-get install docker.io"
"sudo docker pull clemahieu/rai_node"
"sudo docker run -d -p 7075:7075/udp -p 7075:7075 -p 127.0.0.1:7076:7076 -v ~:/root clemahieu/rai_node /rai_node --daemon"

This command:
* Starts the docker container as a daemon "-d"
* Maps the network activity port "-p 7075:7075/udp"
* Maps the bootstrapping TCP port "-p 7075:7075"
* Maps the RPC control port to the local adapter only "-p 127.0.0.1:7076:7076"
* Maps the host's home directory to the guest /root directory "~:/root"
* Specifies the container to execute "clemahieu/rai_node"
* Specifies the command to execute in the container "/rai_node --daemon"

This will put the data in a permanent location in your hosts's home directory, outside the docker container.

RPC access is disabled by default, edit your RaiBlocks/config.json file to enable RPC control and optionally enable control commands e.g. send, add key, create wallets, etc.  By default the RPC binds only to the localhost adaptor otherwise the RPC would be open to anyone.  When running inside a docker container the RPC needs to bind to all adapters so the port can be tunneled outside the container.  You'll need to change "::ffff:127.0.0.1" to "::ffff:0.0.0.0" for rpc_address in the config file.  RPCs within docker are secured by binding the mapped port to the localhost adapter via the "-p 127.0.0.1:7076:7076" option.  **It's very important the 127.0.0.1 is not omitted on the RPC port mapping** otherwise the RPC could be opened to anyone who can reach the node via a network.