# SOC-Automation-Lab

![image](https://github.com/user-attachments/assets/1d306b93-e6ad-4d4e-b1f5-ef773e92efcf)
The above image shows the diagram of the SOC Automation Project

**The following tools will be used in this project:**
- Wazuh (SIEM)
- HIVE (Case Management)
- Shuffle (Automation)
- Windows VM
- DigitalOcean (For hosting Wazuh and Hive instances)

**Step 1: Create 2 droplets, one for Wazuh and another one for Hive**
  ![Screenshot 2025-02-16 at 1 22 38 PM](https://github.com/user-attachments/assets/846fa8be-7f72-4064-b9c3-49bbe94951fd)
  ![Screenshot 2025-02-16 at 1 22 49 PM](https://github.com/user-attachments/assets/1869e5a8-8cc0-481f-a61f-ba05c8914fdb)
  ![Screenshot 2025-02-16 at 1 22 57 PM](https://github.com/user-attachments/assets/98182ab2-3a09-440a-aee3-01f7fc367117)
  ![Screenshot 2025-02-16 at 1 24 13 PM](https://github.com/user-attachments/assets/43a6249d-2112-4b26-bebe-91a56e6620ff)
  ![Screenshot 2025-02-16 at 1 25 36 PM](https://github.com/user-attachments/assets/aa3848a3-7b90-4ec3-955b-035acec09f76)
  We will use the same droplet configuration for Hive as well.
  
1. **After Hive and Wazuh Droplets are created, we need to create a Firewal rule and _add your Public IP Address_, so the Wazuh and Hive instances don't get brute forced as these instance will be open to the internet.**
2. Insert your **PUBLIC IP ADDRESS** where you see red boxes, and configure the TCP and UDP rules like its shown in the image.
  ![Screenshot 2025-02-16 at 1 27 42 PM](https://github.com/user-attachments/assets/513b39b0-fa2b-474c-8976-cb58a6a6841d)

3. Now lets add both of the instances in the Firewall Group that we created.
4. Click on the wazuh instance and follow the same step to add the Hive instance by clicking onto the Hive instance add that instance to the firewall group.
![Screenshot 2025-02-16 at 1 28 41 PM](https://github.com/user-attachments/assets/a6bfe2c9-26a3-44f6-8749-a347c5d4ebfd)
![Screenshot 2025-02-16 at 1 29 46 PM](https://github.com/user-attachments/assets/9f080487-c4c5-4f1b-a188-39470cb74431)
![Screenshot 2025-02-16 at 1 30 55 PM](https://github.com/user-attachments/assets/863ce59a-82ee-4ac8-a927-94067ca40915)
![Screenshot 2025-02-16 at 1 31 01 PM](https://github.com/user-attachments/assets/2a8d5fc4-1ba9-4585-8885-f4d73c04bc1e)
![Screenshot 2025-02-16 at 1 31 14 PM](https://github.com/user-attachments/assets/f9a6d1ce-6f4c-4a8e-817e-3ca102547c87)


