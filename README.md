# SOC-Automation-Lab

![image](https://github.com/user-attachments/assets/1d306b93-e6ad-4d4e-b1f5-ef773e92efcf)
The above image depicts the SOC Automation Project diagram.

**The following tools will be used in this project:**
- Wazuh (SIEM)
- TheHive (Case Management)
- Shuffle (Automation)
- Windows VM
- DigitalOcean (For hosting Wazuh and Hive instances)

**Step 1: Create two droplets: one for Wazuh and another for TheHive.**
  ![Screenshot 2025-02-16 at 1 22 38 PM](https://github.com/user-attachments/assets/846fa8be-7f72-4064-b9c3-49bbe94951fd)
  ![Screenshot 2025-02-16 at 1 22 49 PM](https://github.com/user-attachments/assets/1869e5a8-8cc0-481f-a61f-ba05c8914fdb)
  ![Screenshot 2025-02-16 at 1 22 57 PM](https://github.com/user-attachments/assets/98182ab2-3a09-440a-aee3-01f7fc367117)
  ![Screenshot 2025-02-16 at 1 24 13 PM](https://github.com/user-attachments/assets/43a6249d-2112-4b26-bebe-91a56e6620ff)
  ![Screenshot 2025-02-16 at 1 25 36 PM](https://github.com/user-attachments/assets/aa3848a3-7b90-4ec3-955b-035acec09f76)
  We will use the same droplet configuration for Hive as well.
  
1. **After Hive and Wazuh Droplets are created, need to create a firewall rule and add your public IP address to prevent brute force attacks on the Wazuh and TheHive instances, as they will be accessible over the internet.**
2. Insert your **public IP address** where indicated by the red boxes, and configure the TCP and UDP rules as shown in the image.
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
   This installation will take some time, so wait until the installation is finished and then once its finished you should see the username and password like its shown in the below image, **make sure to take a note of the user and passwrod as this will be used for sign in to the dashboard.**
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

6. Need to make some changes in the Wazuh configuraiton file
<img width="1459" alt="Screenshot 2025-02-22 at 11 05 54 PM" src="https://github.com/user-attachments/assets/befabc0c-072e-43c4-8f63-e529b757845a" />
<img width="1461" alt="Screenshot 2025-02-22 at 11 06 14 PM" src="https://github.com/user-attachments/assets/1b653a8b-e939-46ec-9412-75a288c5eff8" />
<img width="1449" alt="Screenshot 2025-02-22 at 11 06 37 PM" src="https://github.com/user-attachments/assets/b7672409-106c-4919-b67c-850ace4ec680" />

Also using terminal go to the following file path and change the "archives:true", **_"/etc/filebeat/filebeat.yml"_**
<img width="1450" alt="Screenshot 2025-02-22 at 11 10 16 PM" src="https://github.com/user-attachments/assets/96afb4fc-ecd3-45c3-97ce-6efb140fcf46" />
Save the file and restart the wazuh manager, _**"systemctl restart wazuh-manager.service"**_

7. Need to create an archive index pattern to view all the logs from Windows Endpoint, because in "wazuh-alerts" index, you will only see events realted to alerts that are being triggered.
<img width="1451" alt="Screenshot 2025-02-22 at 10 35 47 PM" src="https://github.com/user-attachments/assets/16db0194-9d23-4f82-b649-20724ea236f6" />
<img width="1467" alt="Screenshot 2025-02-22 at 10 36 12 PM" src="https://github.com/user-attachments/assets/f0f30455-4538-462e-8478-cc4f33f73a3d" />
<img width="1027" alt="Screenshot 2025-02-22 at 11 14 27 PM" src="https://github.com/user-attachments/assets/d17db6ec-c976-4de2-a620-d32151cd4297" />
Click "Next"
<img width="1040" alt="Screenshot 2025-02-22 at 11 15 08 PM" src="https://github.com/user-attachments/assets/5d0e17a7-7135-4b9f-85a6-a5a5a539d982" />
Click create Index.


**Step 3: Need to Install the Hive**
1. [Hive Installation](https://github.com/divyank50/SOC-Automation-Lab/blob/main/Hive_Installation)
2. These images just shows the instllation of the  
![Screenshot 2025-02-16 at 3 07 18 PM](https://github.com/user-attachments/assets/2767cd1c-144b-41e2-9ee5-051b20e7e073)
![Screenshot 2025-02-16 at 3 07 29 PM](https://github.com/user-attachments/assets/d6fe7552-f59d-4486-a3a9-8e61cc63af48)
![Screenshot 2025-02-16 at 3 07 44 PM](https://github.com/user-attachments/assets/953e1cb4-39e3-4188-b149-b227e4208b3a)

3. You need to make changes in the "/etc/cassendra/cassendra.yaml" file, you can use nano to make changes
4. Configure the Public IP Address of the Hive instance as shown in the below image:
   <img width="1398" alt="Screenshot 2025-02-22 at 10 54 50 PM" src="https://github.com/user-attachments/assets/62440233-c002-482b-87c1-748550ca17a6" />
   Also add the Hive instance Public Ip address as shown in the below image:
   <img width="1456" alt="Screenshot 2025-02-22 at 10 55 58 PM" src="https://github.com/user-attachments/assets/9fa493bb-1f24-461e-9b4b-c72e6f4dffff" />
   Again change the ip address to hive instance and save the file.
   <img width="1443" alt="Screenshot 2025-02-22 at 10 57 27 PM" src="https://github.com/user-attachments/assets/dde3fb2a-b51c-401d-8b46-23155571e80e" />

5. Now stop the cassendra service. _**"systemctl stop cassendra.service"**_
6. Now remove the old cassendra files. _**"rm -rf /var/lib/cassendra/*"**_
7. Now start the cassendra service. _**"systemctl start cassendra.service"**_ And you can check the staus of cassendra using, _**"systemctl status cassendra.service"**_.

8. Now, you need to make the following changes in the _**"/etc/elasticsearch/elasticsearch.yml"**_ file.
![Screenshot 2025-02-16 at 3 10 47 PM](https://github.com/user-attachments/assets/955193bf-62d5-4de3-8edf-2241ba1d5a0d)
![Screenshot 2025-02-16 at 3 12 10 PM](https://github.com/user-attachments/assets/e9f2cb72-9c51-42e0-9a05-df7bfe707262)
9. After you make these changes, make sure to restart the elastic services using the following command: **"systemctl restart elasticsearch"**
10. Also need to change the folder access of the hive from root to "thehive" user to be able to access the hive, **"chown -R thehive:thehive /opt/thp"**



**Step 4: Installing SYSMON on the Windows Endpoint**
1. [CLick here to Download Sysmon](https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon)
2. Extract the Sysmon zip folder
3. [Also need to download Sysmon Config file](https://github.com/SwiftOnSecurity/sysmon-config/blob/master/sysmonconfig-export.xml)
4. Move the sysmon config file in the Sysmon folder and then execute the command that is shown in the image below, since you have moved the sysmonconfig file in the same folder, just don't include the file path after the **"-i"** paramter, instead just put the file name.
5. ![Screenshot 2025-02-16 at 6 45 21 PM](https://github.com/user-attachments/assets/1e1fb929-7b91-4753-84d3-de25f1401e26)
6. You can check if sysmon is confiured and runnig properly by going into: _Event Viewer> Application and Services > Microsoft > Windows > Sysmon > Operational_
   ![Screenshot 2025-02-20 at 10 11 42 PM](https://github.com/user-attachments/assets/59fc799e-be24-4109-8406-f544a34b13b1)

**Step 5: Install Mimikatz**
1. Before we install Mimikatz, make sure to exclude the Downloads Folder path by going into Windows Defender and Virus & Threat Protection and Exclude File path.
2. [Install Mimikatz](https://github.com/gentilkiwi/mimikatz/releases)
   Download the "mimikatz_trunk.zip" file
3. Extract the mimikatz folder.
4. Lets execute Mimikatz.exe
5. Open powershell/command prompt and go the mimikatz directory. The mimikatz.exe file is inside the x64 folder. Execute the file using powershell/cmd.
6. As you execute you should see events generated in Wazuh realted to this.
7. Upon the execution of the mimikatz, we can see the event from the archives index in wazuh:
   <img width="1465" alt="Screenshot 2025-02-22 at 11 22 45 PM" src="https://github.com/user-attachments/assets/c309cb5f-7ff7-4c33-8ba9-1bfa9a992e96" />
<img width="1455" alt="Screenshot 2025-02-22 at 11 23 48 PM" src="https://github.com/user-attachments/assets/0c953f9b-f4d9-4ccd-bea9-3e3127c4ead2" />
We can see there is a field name called "originalFileName", so lets create an alert/rule to detect whenever mimikatz is executed on the system, the reason why I have used the "originalFileName" field is because if you change the filename, it won't change the original file name that was captured by sysmon logs and everytime a file is executed it will generate an alert.

8.I created this rule in to detect mimikatz
<img width="874" alt="Screenshot 2025-02-22 at 11 26 08 PM" src="https://github.com/user-attachments/assets/7230ca94-5719-4d50-b0f3-6d5bb47b3f09" />

9.Since I exectued mimikatz bunch of times, these where the alerts that generated
<img width="1464" alt="Screenshot 2025-02-22 at 11 27 09 PM" src="https://github.com/user-attachments/assets/3a90680f-a6ef-4210-a2ef-2a8429a62d61" />

**Step 6: Configuring the Automation/Shuffle**
1. Visit shuffler.io website and create an account.
2. I created the following workflow, whenever a mimikatz alert is detected, the shuffle automation will received all the information about that alert, it will extract the SHA 256 hash and then using Virus Total Hash Report API functionality it will query results of the Hash and then it will create an alert in Hive and also send an email to the Analyst about the alert.

Image showcasing Automation Workflow in Shuffle
<img width="1232" alt="Screenshot 2025-02-22 at 11 33 41 PM" src="https://github.com/user-attachments/assets/49eec1cc-399c-48b7-89cd-b5529eeb5dc9" />
Image showcasing alert details from Wazuh
<img width="1442" alt="Screenshot 2025-02-22 at 11 33 59 PM" src="https://github.com/user-attachments/assets/b7fcd703-edac-4e9f-8538-845aa68db576" />
Image showcasing SHA256 hash regex
<img width="806" alt="Screenshot 2025-02-22 at 11 34 14 PM" src="https://github.com/user-attachments/assets/c4d6d279-e459-4cfc-974c-df439c908f5f" />
Image showcasing SHA256 queried via API to VT
<img width="1265" alt="Screenshot 2025-02-22 at 11 34 57 PM" src="https://github.com/user-attachments/assets/c53c78b8-6d2a-4797-b3f9-ec9656b13c54" />
I get error code 400, because I tried to re-run the workflow and forgot to delete the alert in hive and you can also see the error code mentions "alert already exists".
<img width="1451" alt="Screenshot 2025-02-22 at 11 35 26 PM" src="https://github.com/user-attachments/assets/eb5ba95b-7db2-4b8b-9511-13925905cefb" />

Image of Hive, showcasing Alert
<img width="1461" alt="Screenshot 2025-02-22 at 11 39 29 PM" src="https://github.com/user-attachments/assets/e15e818d-5593-477b-bb1c-ddc56d4c9bae" />
Image showcasing, Email sent upon alert detection
<img width="1097" alt="Screenshot 2025-02-22 at 11 40 55 PM" src="https://github.com/user-attachments/assets/9b8db5a0-a100-4e8d-8788-e0bbe7e4f549" />

This SOC Automation Lab/Project demonstrates the use of Wazuh SIEM to detect security events and alerts generated on a Windows endpoint. Upon detecting an alert, an automated workflow in Shuffle retrieves the alert details, extracts relevant IOCs, queries them using the VirusTotal API, and then creates a corresponding alert in TheHive. Additionally, an email notification is sent to the analyst for further investigation. This project also highlights the integration of various security tools and the use of a cloud environment (DigitalOcean) to deploy Wazuh and TheHive instances.
