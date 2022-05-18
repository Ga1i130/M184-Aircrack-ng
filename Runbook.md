# Airkrack-ng
## What needed?

1. MAC Address of the Attacker
2. BSSID 
3. ESSID
4. Channel
5. Interface

## What to do?

### Get information about the Target

1. Get SSID from the Traget.
 > netdicover
 
 Search for IP Address common for Access Points/ Routers
 Mac AP: 00:11:6b:2d:9f:b7
 
2. Use airmon-ng to check for wifi interfaces

3. Stop any useless interfaces with the command:
> airmon-ng stop <interface>
