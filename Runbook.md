# Airkrack-ng
## What needed?

1. MAC Address of the Attacker
2. BSSID 
3. ESSID
4. Channel
5. Interface
6. Root acccess

## What to do?

### Get information about the Target

1. Get SSID from the Traget.
 > netdicover
 
 Search for IP Address common for Access Points/ Routers
 Mac AP: 00:11:6b:2d:9f:b7
 
2. Use airmon-ng to check for wifi interfaces

![image](https://user-images.githubusercontent.com/63262820/169005453-2e40bcd5-5bb8-4e8d-a191-6609c73f74ac.png)

3. Stop any useless interfaces with the command:
> airmon-ng stop "interface"

4. Start interface wlan0 in monitor mode and with de realated wlan channel:
>  airmon-ng start wlan0 9

![image](https://user-images.githubusercontent.com/63262820/169005722-cf7c77fd-35a8-41af-918f-7f8a86376acf.png)

5. Now the interface wlan0 is called wlan0mon


7. To confirm the interface is properly setup, enter:
> iwconfig

![image](https://user-images.githubusercontent.com/63262820/169006405-f3db4138-3622-4365-93b4-9324c1331d76.png)

8. Now capture the WPA Handshake.
> airodump-ng -c 9 --bssid "AP MAC" -w psk wlan0mon


