Port usage:
7075 UDP: Primary node activity port
* Port configurable in config.json:node/peering_port
* Always enabled
* Binds to all adapters
* Contents: Raw rai protocol datagrams
* All standard ledger activity goes through this port
* If blocked the node will not function

7075 TCP: Node bootstrapping server
* Port same as UDP port
* Always enabled
* Binds to all adapters
* Contents: Raw rai protocol stream
* Transmits the ledger to new nodes in bulk
* If blocked other nodes will not be able to use this node as a bootstrap server

7076 TCP: RPC server
* Port configurable in config.json:rpc/port
* Disabled by default, enable with config.json:rpc_enable
* Binds to localhost by default for security reasons
* Contents: Unencrypted HTTP requests containing JSON object bodies
* Allows the node to be controlled through HTTP requests
* If blocked the node will not be able to be controlled by HTTP
