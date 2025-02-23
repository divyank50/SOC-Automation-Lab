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
You will have to search your instance name to add here and same for the Hive instance as well, search it.
![Screenshot 2025-02-16 at 1 31 14 PM](https://github.com/user-attachments/assets/f9a6d1ce-6f4c-4a8e-817e-3ca102547c87)


**Step 2: Download Wazuh on the Wazuh instance.**
1. You have to connect to Wazuh instance via ssh.
   _Command_: ssh root@wazuh_instance_ip_address

2. After you connect via SSH, run the following command to update all the packages:
   apt-get update && apt upgrade

3. After all the packages are installed/updated to the latest version, now we will download wazuh
   ![Screenshot 2025-02-16 at 1 49 51 PM](https://github.com/user-attachments/assets/614b9913-f27f-4d9d-bbb2-c8c2ef028df9)
    Run the command that is showed in the above image or [Click the following link for the latest version](https://documentation.wazuh.com/current/quickstart.html)
   ![Screenshot 2025-02-16 at 1 52 17 PM](https://github.com/user-attachments/assets/331208aa-e73d-40de-a4a3-fbd8bcd67065)
   This installaiton will take some time, so wait until the installtion is finished and then once its finished you should see the username and password like its shown in the below image, **make sure to take a note of the user and passwrod as this will be used for sign in to the dashboard.**
   ![Screenshot 2025-02-16 at 2 00 25 PM](https://github.com/user-attachments/assets/8c334de7-6e4f-4057-b691-0fe5a8b9482a)

4. Once you get the username and password you can visit the wazuh Dashboard: https://wazuh_instance_ip_address.
   
5. Now we need to deploy the wazuh agent on the Windows Endpoint:
 ![Screenshot 2025-02-16 at 2 18 23 PM](https://github.com/user-attachments/assets/b0880f0f-a65c-4e51-8820-9ae17a617c3a)
![Screenshot 2025-02-16 at 2 04 32 PM](https://github.com/user-attachments/assets/8642e1b9-3d3e-4ce1-a5d6-7fc38b2dee4b)
![Screenshot 2025-02-16 at 2 04 41 PM](https://github.com/user-attachments/assets/39739f97-97b8-4bed-9e08-0171b4e5f115)
![Screenshot 2025-02-16 at 2 20 45 PM](https://github.com/user-attachments/assets/c5c7dd79-5103-4903-a244-d61ab1594a0c)
You can confirm if the agent is installed on your system by going to the control panel> programs > program and feature.
![Screenshot 2025-02-16 at 2 21 01 PM](https://github.com/user-attachments/assets/7e914579-3040-4caf-96bc-54bc1f20b21f)
![Screenshot 2025-02-16 at 2 21 25 PM](https://github.com/user-attachments/assets/50a73334-c2fb-4fba-bc12-37f251258348)

**Step 3: Need to Install the Hive**
1. [Hive Installation](https://github.com/divyank50/SOC-Automation-Lab/blob/main/Hive_Installation)
2. These images just shows the instllation of the  
![Screenshot 2025-02-16 at 3 07 18 PM](https://github.com/user-attachments/assets/2767cd1c-144b-41e2-9ee5-051b20e7e073)
![Screenshot 2025-02-16 at 3 07 29 PM](https://github.com/user-attachments/assets/d6fe7552-f59d-4486-a3a9-8e61cc63af48)
![Screenshot 2025-02-16 at 3 07 44 PM](https://github.com/user-attachments/assets/953e1cb4-39e3-4188-b149-b227e4208b3a)

After you install, you need to make the following changes in the "/etc/elasticsearch/elasticsearch.yml" file.
![Screenshot 2025-02-16 at 3 10 47 PM](https://github.com/user-attachments/assets/955193bf-62d5-4de3-8edf-2241ba1d5a0d)
![Screenshot 2025-02-16 at 3 12 10 PM](https://github.com/user-attachments/assets/e9f2cb72-9c51-42e0-9a05-df7bfe707262)


**Step 4: Installing SYSMON on the Windows Endpoint**
1. [CLick here to Download Sysmon](https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon)
2. Extract the Sysmon zip folder
3. [Also need to download Sysmon Config file](https://github.com/SwiftOnSecurity/sysmon-config/blob/master/sysmonconfig-export.xml)
4. Move the sysmon config file in the Sysmon folder and then execute the command that is shown in the image below, since you have moved the sysmonconfig file in the same folder, just don't include the file path after the **"-i"** paramter, instead just put the file name.
5. ![Screenshot 2025-02-16 at 6 45 21 PM](https://github.com/user-attachments/assets/1e1fb929-7b91-4753-84d3-de25f1401e26)
