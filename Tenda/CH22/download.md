The Tenda CH22 router (firmware CH22 upgrade software V1.0.0.6(468)) has an arbitrary file download vulnerability. An attacker can exploit this vulnerability to download any file from any directory.

Download the corresponding version of the firmware from the Tenda official website, and unpack the firmware to get the file system.

<img width="416" height="183" alt="image" src="https://github.com/user-attachments/assets/c07e6935-1523-4f34-a01b-d74f40dcb901" />


After analyzing the web backend file httpd, it was found that formexecommand can execute strictly restricted commands. When the cmdinput parameter is set to 'cat [a file]', it will download that file, leading to an arbitrary file download vulnerability.

<img width="416" height="444" alt="image" src="https://github.com/user-attachments/assets/e33baf7f-8e70-4344-8fca-b0f0d7263ffb" />


Here, we attempt to download the backend file httpd through the webpage by constructing the URL as http://192.168.0.1/goform/exeCommand?cmdinput=cat%20./bin/httpd

<img width="353" height="247" alt="image" src="https://github.com/user-attachments/assets/cfaba22f-b1bb-4cd2-a5ca-54b94a10d42f" />



Successfully downloaded this file, the same applies to other files.
