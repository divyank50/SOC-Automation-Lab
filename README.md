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

**After Hive and Wazuh Droplets are created, we need to create a Firewall and _add your Public IP Address_, so the Wazuh and Hive instances don't get brute forced because these instance will be open to the internet, so by adding our Public IP Address, we are only allowing us to connect to these 2 instances.**
![Screenshot 2025-02-16 at 1 27 42 PM](https://github.com/user-attachments/assets/513b39b0-fa2b-474c-8976-cb58a6a6841d)
Insert your **PUBLIC IP ADDRESS** where you see red boxes, and configure the TCP and UDP rules like its shown in the image.
![Screenshot 2025-02-16 at 1 28 4![Screenshot 2025-02-16 at 1 29 46 PM](https://github.com/user-attachments/assets/5ed1b20c-7dd4-4613-b6e2-59be9c107165)

Now we need to add both of the instances in the Firewall group, therefore click on the instance/droplet and then click Networking.
![Screenshot 2025-02-16 at 1 29 46 PM](https://github.com/user-attachments/assets/b254c724-da20-4696-b66c-8288839882f9)
![Screenshot 2025-02-16 at 1 30 55 PM](https://github.com/user-attachments/assets/b0970efd-134a-4f77-9c98-b20e079616f0)


