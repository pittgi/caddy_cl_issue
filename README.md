Credits to @lpisu98 for helping to investigate this issue.

Tested version of Caddy: v.2.9.1 (latest, precompiled binary)

Testing enviroment: Ubuntu 24.04.2 LTS x86_64

# How to replicate

 1. Setup wireshark to capture HTTP/3 and HTTP/2 secrets (see below) and start capturing
 2. Choose backend and run it
 3. Run caddy with correct Caddyfile
 4. Edit attacker.py to your desired content-length and data, then run it
 5. Observe traffic in wireshark

# Commands to run services

 - Node.js: `node node_server.js`
 - php: `php -S localhost:8080`
 - flask: `python3 flask_server.py`
 - h2: `python3 h2_server.py`
 - caddy: `sudo ./caddy run --config ./CaddyfileHttp2`
 - attacker: `python3 attacker.py`

# Setup Wireshark

 1. Edit attacker.py PATH_TO_TLS_SECRECTS (example "/home/USER/keys.log")
 2. Run in terminal: `export SSLKEYLOGFILE_="/home/USER/keys.log"`
 3. Run http2 server in same terminal instance
 4. Same path into Wireshark -> Edit -> Preferences -> (Left) Protocols -> TLS -> (Pre)-Master-Secret log filname
