    {
    "version": "(int)", # Wallet version
    "wallet": "(string)", # Default wallet to load on boot
    "account": "(string)", # Default account to load on boot
    "node": {
        "version": "(int)", # Node version
        "peering_port": "7075", # Default node port
        "packet_delay_microseconds": "5000", #
        "bootstrap_fraction_numerator": "1", #
        "creation_rebroadcast": "2", #
        "rebroadcast_delay": "15", # 
        "receive_minimum": "1000000000000000000000000", # Minimum import receivable, default 1 Rai
        "logging": {
            "ledger": "false", # Track incoming blocks
            "ledger_duplicate": "false",
            "network": "true", # Track general network info like forks
            "network_message": "false",
            "network_publish": "false", # Track blocks you publish to
            "network_packet": "false", # Track packets origin
            "network_keepalive": "false",
            "node_lifetime_tracing": "false",
            "insufficient_work": "true",
            "log_rpc": "true", # Track RPC your node execute
            "bulk_pull": "false",
            "work_generation_time": "true",
            "log_to_cerr": "false",
            "max_size": "16777216",
            "version": "2",
            "work_peers": "",
            "vote": "false" # Track voting activities
        },
        "work_peers": "", # Delegate a node your hash work, you need to get RPC access to that node
        "preconfigured_peers": [ # List of defaults peers to connect on boot
            "rai.raiblocks.net",
            "raiblockscommunity.net",
            "64.137.172.219",
            "138.201.94.249"
        ],
        "preconfigured_representatives": [ # List of defaults representatives, which you delegate voting weight, of your wallet
            "xrb_3arg3asgtigae3xckabaaewkx3bzsh7nwz7jkmjos79ihyaxwphhm6qgjps4",
            "xrb_1stofnrxuz3cai7ze75o174bpm7scwj9jn3nxsn8ntzg784jf1gzn1jjdkou",
            "xrb_1q3hqecaw15cjt7thbtxu3pbzr1eihtzzpzxguoc37bj1wc5ffoh7w74gi6p",
            "xrb_3dmtrrws3pocycmbqwawk6xs7446qxa36fcncush4s1pejk16ksbmakis78m",
            "xrb_3hd4ezdgsp15iemx7h81in7xz5tpxi43b6b41zn3qmwiuypankocw3awes5k",
            "xrb_1awsn43we17c1oshdru4azeqjz9wii41dy8npubm4rg11so7dx3jtqgoeahy",
            "xrb_1anrzcuwe64rwxzcco8dkhpyxpi8kd7zsjc1oeimpc3ppca4mrjtwnqposrs",
            "xrb_1hza3f7wiiqa7ig3jczyxj5yo86yegcmqk3criaz838j91sxcckpfhbhhra1"
        ],
        "inactive_supply": "0", #
        "password_fanout": "1024", #
        "io_threads": "4", #
        "work_threads": "4" #
    },
    "rpc": {
        "address": "::ffff:127.0.0.1", # Allowed IP for RPC connection
        "port": "7076", # Default RPC port
        "enable_control": "true", # Enable particular RPC command like: send, account_create, etc...
        "frontier_request_limit": "16384", #
        "chain_request_limit": "16384" #
    },
    "rpc_enable": "true", # Enable or disable RPC
    "opencl_enable": "false", # Enable GPU hashing
    "opencl": {
        "platform": "0", # Platform ID
        "device": "0", # Device ID
        "threads": "1048576" #
    }
    }

config.json location:

    Windows: C:\Users\AppData\Local\RaiBlocks\
    OSX: /Users//Library/RaiBlocks/
    Linux: ~/RaiBlocks/