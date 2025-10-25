The Tenda CH22 router (firmware CH22 upgrade software_V1.0.0.6(468)) has a hard-coded credential vulnerability. The root user account on the device uses a hard-coded password, which is stored in a file with an MD5 encrypted hash. This allows an attacker to obtain the root password using password-cracking tools, thereby gaining unauthorized access to the router's system.


Description: This vulnerability is caused by the hardcoding of the root user password in the Tenda CH22 router firmware. When analyzing the firmware, it was found that the file storing user account information contains the password hash of the root user. The hash can be easily cracked using password cracking tools, revealing the plaintext password and allowing an attacker to log into the router system with root privileges.

The main findings of the firmware analysis are as follows:Firmware extraction: 
After extracting the firmware files, the system file structure was obtained, including directories.File analysis: 

<img width="415" height="332" alt="image" src="https://github.com/user-attachments/assets/4ebcaaba-653a-426a-8cfe-73f092058055" />


The files in the directories were examined, and the password hash for the root user was found at shadow/etc_ro/.

<img width="416" height="359" alt="image" src="https://github.com/user-attachments/assets/6b844e4d-1faa-4693-b64d-c331c4cb8019" />


Password cracking: The above hash was cracked using the John tool, successfully obtaining the root user's plaintext password "Fireitup".

<img width="416" height="86" alt="image" src="https://github.com/user-attachments/assets/7a238f21-a967-474d-a426-a34d166a9dee" />
