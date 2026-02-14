Checking monitor mode
```bash
iwconfig
```
(airmon-ng) Starting monitor mode
```bash
sudo airmon-ng start wlan0
```
(airmon-ng) Killing bad processes that could interfere with monitor mode
```bash
sudo airmon-ng check kill
```
(airodump-n)