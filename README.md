```code
cat > /usr/lib/systemd/system/frpc.service <<EOF
[Unit]
Description=Frp Client Service
After=network.target

[Service]
Type=simple
User=nobody
Restart=on-failure
RestartSec=5s
ExecStart=/usr/local/frp/frpc -c /usr/local/frp/frpc.ini
ExecReload=/usr/local/frp/frpc reload -c /usr/local/frp/frpc.ini

[Install]
WantedBy=multi-user.target
EOF
```


```code
cat > /usr/lib/systemd/system/frps.service <<EOF
[Unit]
Description=Frp Server Service
After=network.target

[Service]
Type=simple
User=root
Group=root
Restart=on-failure
RestartSec=5s
ExecStart=/usr/local/frps/frps -c /usr/local/frps/frps.ini

[Install]
WantedBy=multi-user.target
EOF
```