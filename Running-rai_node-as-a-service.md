**To enable RPC for node edit [config.json](https://github.com/clemahieu/raiblocks/wiki/config.json) after first launch**   
./rai_node --daemon  
sed -i 's/"rpc_enable": "false"/"rpc_enable": "true"/g' ~/RaiBlocks/config.json   
sed -i 's/"enable_control": "false"/"enable_control": "true"/g' ~/RaiBlocks/config.json  

**Launch rai_node in test mode**   
./rai_node --daemon

**Check if RPC is enabled with curl (use different terminal or session)**   
curl -g -d '{ "action": "block_count" }' [::1]:7076   

**To stop node, use**   
curl -g -d '{ "action": "stop" }' [::1]:7076   

**Launch rai_node as a service with system.d**   
sudo touch /etc/systemd/system/rai_node.service   
sudo chmod 664 /etc/systemd/system/rai_node.service   
sudo nano /etc/systemd/system/rai_node.service   
>_Paste your specific user, group, path settings (example)_   
    
    [Unit]
    Description=RaiBlocks node service
    After=network.target
    
    [Service]
    ExecStart=/path_to_rai_node/rai_node --daemon
    Restart=on-failure
    User=username
    Group=groupname

    [Install]
    WantedBy=multi-user.target
>_Start rai_node service_    

sudo service rai_node start

>_Enable at startup_    

sudo systemctl enable rai_node
    
    
**To manage node, use [RPC commands](https://github.com/clemahieu/raiblocks/wiki/RPC-protocol) or [CLI](https://github.com/clemahieu/raiblocks/wiki/Command-line-interface)**   