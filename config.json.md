
## Structure of configuration file
 ```javascript
   {
    "version": "(int)", // Wallet version
    "wallet": "(string)", // Default wallet to load on boot (only for GUI wallet)
    "account": "(string)", // Default account to load on boot (only for GUI wallet)
    "node": {
        "version": "(int)", // Node version
        "peering_port": "7075", // Default node port
        "bootstrap_fraction_numerator": "1", 
        "enable_voting": "false", // Enable or disable voting for blocks. If disabled, saves some resources
        "receive_minimum": "1000000000000000000000000", // Minimum import receivable, default 1 Rai
        "logging": {
            "ledger": "false", // Track incoming blocks
            "ledger_duplicate": "false",
            "network": "true", // Track general network info like forks
            "network_message": "false",
            "network_publish": "false", // Track blocks you publish to
            "network_packet": "false", // Track packets origin
            "network_keepalive": "false",
            "node_lifetime_tracing": "false",
            "insufficient_work": "true",
            "log_rpc": "true", // Track RPC your node execute
            "bulk_pull": "false", // Bootstrap related logging
            "work_generation_time": "true",
            "log_to_cerr": "false",
            "max_size": "16777216",
            "rotation_size": "4194304", // Size of Log File before rotation in bytes, Default is 4MB 
            "version": "2",
            "work_peers": "",
            "vote": "false", // Track voting activities
            "flush": "true"  // Setting this to false gives better performance, but may lose entries on crashes.
        },
        "work_peers": "", // Delegate a node your hash work, you need to get RPC access to that node
        "preconfigured_peers": [ // List of defaults peers to connect on boot
            "rai.raiblocks.net",
            "raiblockscommunity.net",
            "64.137.172.219",
            "138.201.94.249"
        ],
        "preconfigured_representatives": [ // List of defaults representatives, which you delegate voting weight, of your wallet
            "xrb_3arg3asgtigae3xckabaaewkx3bzsh7nwz7jkmjos79ihyaxwphhm6qgjps4",
            "xrb_1stofnrxuz3cai7ze75o174bpm7scwj9jn3nxsn8ntzg784jf1gzn1jjdkou",
            "xrb_1q3hqecaw15cjt7thbtxu3pbzr1eihtzzpzxguoc37bj1wc5ffoh7w74gi6p",
            "xrb_3dmtrrws3pocycmbqwawk6xs7446qxa36fcncush4s1pejk16ksbmakis78m",
            "xrb_3hd4ezdgsp15iemx7h81in7xz5tpxi43b6b41zn3qmwiuypankocw3awes5k",
            "xrb_1awsn43we17c1oshdru4azeqjz9wii41dy8npubm4rg11so7dx3jtqgoeahy",
            "xrb_1anrzcuwe64rwxzcco8dkhpyxpi8kd7zsjc1oeimpc3ppca4mrjtwnqposrs",
            "xrb_1hza3f7wiiqa7ig3jczyxj5yo86yegcmqk3criaz838j91sxcckpfhbhhra1"
        ],
        "inactive_supply": "0", 
        "password_fanout": "1024", 
        "io_threads": "4", 
        "work_threads": "4", // PoW work threads. By deafault all available CPU threads, set lower value for 24/7 services
        "callback_address": "::ffff:127.0.0.1", // Callback IP address, in sample IPv4 localhost
        "callback_port": "17076", // Callback port
        "callback_target": "/", // Callback target, in sample root of callback listening server
        "bootstrap_connections": "16" // Multi-connection bootstrap. Should be a power of 2.
    },
    "rpc": {
        "address": "::ffff:127.0.0.1", // Allowed IP for RPC connection
        "port": "7076", // Default RPC port
        "enable_control": "true", // Enable particular RPC command like: send, account_create, etc...
        "frontier_request_limit": "16384", 
        "chain_request_limit": "16384" 
    },
    "rpc_enable": "true", // Enable or disable RPC
    "opencl_enable": "false", // Enable GPU hashing
    "opencl": {
        "platform": "0", // Platform ID
        "device": "0", // Device ID
        "threads": "1048576" 
    }
    }
```
## Where is the configuration file located? 

###  Windows
```bash
C:\Users\<user>\AppData\Local\RaiBlocks\
```  
###  OSX
```bash
/Users/<user>/Library/RaiBlocks/
```
### Linux
```bash
/home/<user>/RaiBlocks/
```

## Configuration Options
### work_peers
Used when offloading work generation to another node or service. Format must be ipv6, preceded by ::ffff: if ipv4, hostnames are not allowed at this time. Calls are made to the ip:port designated using the standard RPC format [work_generate](https://github.com/nanocurrency/raiblocks/wiki/RPC-protocol#work-generate) 
```javascript
"work_peers": [
    "::ffff:127.0.0.1:7076"
],
```