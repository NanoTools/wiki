    {
    "version": wallet version
    "wallet": default wallet to start
    "account": default account to start
    "node": {
        "version": node version
        "peering_port": node default ports
        "packet_delay_microseconds": 
        "bootstrap_fraction_numerator": 
        "creation_rebroadcast": 
        "rebroadcast_delay": 
        "receive_minimum": minimum amount processable
        "logging": {
            "ledger": 
            "ledger_duplicate": 
            "network": 
            "network_message": 
            "network_publish": 
            "network_packet": 
            "network_keepalive": 
            "node_lifetime_tracing": 
            "insufficient_work": 
            "log_rpc": 
            "bulk_pull": 
            "work_generation_time": 
            "log_to_cerr": 
            "max_size": max size of each log file
        },
        "work_peers": 
        "preconfigured_peers": [
            list of preconfigured peers your node connects at start
        ],
        "preconfigured_representatives": [
            list of preconfigured representative your node delegates voting weight
        ],
        "inactive_supply": 
        "password_fanout": 
        "io_threads": 
        "work_threads": 
    },
    "rpc": {
        "address": IP address from your RPC accepts connections
        "port": RPC default ports
        "enable_control": allow RPC commands to control signing node functions
        "frontier_request_limit": 
        "chain_request_limit": 
    },
    "rpc_enable": "true"/"false" enable or disable RPC
    "opencl_enable": "true"/"false" enable or disable asic or gpu hashing
    "opencl": {
        "platform": (int) platform id
        "device": (int) device id id
        "threads": "1048576"
    }
    }

config.json location:

    Windows: C:\Users\AppData\Local\RaiBlocks\
    OSX: /Users//Library/RaiBlocks/
    Linux: ~/RaiBlocks/