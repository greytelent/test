### Change MAC Address
- Below command will show all of the wireless cards
```sh
iwconfig
```

- Disable the wireless card using below command
```sh
ifconfig wlan0 down
```

- macchanger tool
```sh
macchanger --help
```
> above will display all commands of macchanger
```sh
macchanger --show
```
> above command will display your current mac address. use as per your requirements
- Now we are going to change mac address using tool macchanger
```sh
macchanger --random wlan0
```

- Now enable the wireless card
```sh
ifconfig wlan0 up
```

### Wireless Modes
1.) Managed Mode
2.) Monitor Mode

-  For check your current wireless card mode
```sh
iwconfig
```
#### Enable monitor mode
##### #1 Method (airmon-ng)

- List available wireless card
```sh
airmon-ng
```
-  Start monitor mode
```sh
airmon-ng start wlan0
```
> now the interface is changed to mon0
-  Check mode
```sh
iwconfig wlan0mon
```
- Stop monitor mode
```sh
airmon-ng stop wlan0mon
```
##### #2 Method (Manual)
-  Check our wireless card
```sh
iwconfig wlan0
```
- Disable wireless card
```sh
ifconfig wlan0 down
```
- Enable monitor mode
```sh
iwconfig wlan0 mode monitor
```
- Enable wireless card
```sh
ifconfig wlan0 up
```
- Checking mode
```sh
iwconfig wlan0
```
> monitor mode is enabled in wlan0
##### #3 Method (airmon-ng check kill)
- Disable wireless card
```sh
ifconfig wlan0 down
```
- Kill processes
```sh
airmon-ng check kill
```
- Enable monitor mode
```sh
airmong-ng start wlan0
```
- Check mode
```sh
iwconfig
```


### Packet Sniffing

> Make sure your wireless card is in monitor mode
-  List all network around us
```sh
airodump-ng wlan0
```
> we can stop scanning by pressing Ctrl + C
- Packet sniffing
```sh
airodump-ng --channel {channel number} --bssid {bssid of target} --write {filename} wlan0 
```
> `filename` - packet saved as this filename
> after you got any connected client's mac address you canstop attack by pressing Ctrl + C

- Now list all saved file by below command
```sh
ls {filename}*
```

- Open wireshark (analyzing packets)
> open {filename.cap} in wireshark
### Deauthentication Attack
- 