Here's the English translation:

Vendor: D-Link
Product: DSL-3782
Firmware Version: DSL-3782_A1_EU_1.01_07282016
Vulnerability Type: Use of Hard-coded Credentials (CWE-798)
Reporter: clxhzg

This vulnerability is caused by the hard-coding of passwords for users such as admin in the DSL-3782 router firmware. During firmware analysis, it was discovered that the file storing user account information contains the password hash for the admin user. 
This hash can be easily cracked using password cracking tools, revealing the plaintext password and allowing attackers to log into the router system with admin privileges.

```
echo 'admin:$1$$iC.dUsGpxNNJGeOm1dFio/' > hash.txt
john --wordlist=/usr/share/john/password.lst hash.txt
john --show hash.txt
```

<img width="465" height="77" alt="image" src="https://github.com/user-attachments/assets/e3736490-2627-4fa5-b90c-d8fd3f1a9350" />
