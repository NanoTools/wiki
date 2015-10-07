The fastest way to set up a RaiBlocks node is via a docker container from DockerHub.  You'll need a semi-recent version of docker, Client Version ~ 1.5.0.

"sudo docker run -d -p 7075:7075/udp -p 7075:7075 -p 127.0.0.1:7076:7076 -v ~:/root clemahieu/rai_node /rai_node --daemon"

This command:
* Starts the docker container as a daemon "-d"
* Maps the network activity port "-p 7075:7075/udp"
* Maps the bootstrapping TCP port "-p 7075:7075"
* Maps the RPC control port to the local adapter only "-p 127.0.0.1:7076:7076"
* Maps the user's home directory to the /root directory inside the container "~:/root"
* Specifies the container to execute "clemahieu/rai_node"
* Specifies the command to execute in the container "/rai_node --daemon"