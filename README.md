# Active Directory-Lab


## Objective


The Active Directory Lab project aimed to establish a controlled environment for simulating and detecting cyber attacks. The primary focus was to ingest and analyze logs within a Security Information and Event Management (SIEM) system, generating test telemetry to mimic real-world attack scenarios with atomic red team and splunk. This hands-on experience was designed to deepen understanding of network security, attack patterns, and defensive strategies.

### Skills Learned

- Active Directory, Splunk
- Advanced understanding of SIEM concepts and practical application.
- Proficiency in analyzing and interpreting network logs.
- Ability to generate and recognize attack signatures and patterns.
- Enhanced knowledge of network protocols and security vulnerabilities.
- Development of critical thinking and problem-solving skills in cybersecurity.

### Tools Used
[Bullet Points - Remove this afterwards]

- Security Information and Event Management (SIEM) system for log ingestion and analysis.
- Atomic Red team
- Telemetry generation tools to create realistic network traffic and attack scenarios.

## Steps

NetWork Architecture

![Screenshot 2024-04-14 202511](https://github.com/xOmari/Home-Lab/assets/159092818/141a4d73-4a85-4ba9-9d51-0e2467050dcc)


For this project ive Installed four Virtual Machines : Kali linux , Windows 2019 server for Active directory , Linux server for Splunk and Windows 10 as my target Machine.


![Screenshot 2024-04-15 092652](https://github.com/xOmari/Home-Lab/assets/159092818/ff5622a5-d766-4f4a-837c-28f0df9735d2)

Next I set up a Static ipaddress for my splunk server using: Sudo nano /etc/netplan/00-installer-config.yaml and set it as 192.168.10.10

![VirtualBox_splunk S_15_04_2024_10_46_28](https://github.com/xOmari/Home-Lab/assets/159092818/80b719eb-0e4b-486f-b402-32adf731fc6f)

Next I download splunk From their official website along with virtualbox guest additions so i can access on the splunk server using a shared folder.

Next we mount the file and begin installation

![VirtualBox_splunk S_18_03_2024_18_34_55](https://github.com/xOmari/Home-Lab/assets/159092818/582a014e-7cc3-4aee-b941-231a769219ed)

Next we change to the opt/splunk directory where splunk is located
using sudo -u splunk bash i will change to the user, Splunk next we will change directory to bin with, cd bin and then use the ./splunk start.
Next we wll make sure splunk starts everytime the server reboots, First I well exit the splunk user and then change to bin and use sudo ./splunk enable boot-start -user splunk.

Next we will go to our target machine to installer sysmon and splunk forwarder then do the smae steps on windows server
Set Static IP address

![VirtualBox_target_08_04_2024_03_59_48](https://github.com/xOmari/Home-Lab/assets/159092818/fe0b97db-067e-4662-8aee-65297b488c91)


Go to splunk offiacl website click Products> Free trial and downloads then universal forwarder
When insatalling set recieving index as 192.168.10.10 and use port 9997
Next we dwonload sysmon from sysinternals, also download the sysmon configuration file from Olaf Github

![VirtualBox_target_10_04_2024_19_42_50](https://github.com/xOmari/Home-Lab/assets/159092818/c703d944-4b6f-401a-be56-442b35359fae)

Next we locate the file in powershell to install

![VirtualBox_target_10_04_2024_19_28_26](https://github.com/xOmari/Home-Lab/assets/159092818/244087a5-3caa-4ed8-9213-99f021dc072f)

Next we go to your splunk fowarder file etc/system/local and drop the config file as inputs.conf
![VirtualBox_target_10_04_2024_19_46_27](https://github.com/xOmari/Home-Lab/assets/159092818/cd32dcdf-4394-489d-8828-7e9cd8a8d973)

Afterthat go to services and restart program also change the permissions from NT service to Loacal

![VirtualBox_target_10_04_2024_19_52_54](https://github.com/xOmari/Home-Lab/assets/159092818/33567385-04d3-4a1e-9a3d-5398c059783c)

Now we log in

![VirtualBox_target_19_03_2024_00_04_49](https://github.com/xOmari/Home-Lab/assets/159092818/79498057-38b3-477a-97be-7feba4e38fa9)

Next we install Active directory on windows server , add two users and configure our target to join active directory also add two organizationsl Unit as HR and IT


![VirtualBox_ADD_12_04_2024_09_36_11](https://github.com/xOmari/Home-Lab/assets/159092818/a7aea21d-27a3-4215-86e4-c1af88d6c054)

![VirtualBox_ADD_12_04_2024_05_39_55](https://github.com/xOmari/Home-Lab/assets/159092818/45e35a7c-48df-4ab5-8759-d52960fc8199)


Next we will anable RDP

![VirtualBox_ADD_13_04_2024_19_04_01](https://github.com/xOmari/Home-Lab/assets/159092818/326d9818-1b48-4125-8553-ca6c1b4a0171)

![VirtualBox_ADD_13_04_2024_19_07_24](https://github.com/xOmari/Home-Lab/assets/159092818/aef82de7-5047-450d-a459-079021132fbc)


Next we will be using kali linux to demonstrate a brute force attack and view telemetry on splunk
Also will then use Atomic Red team to simulate attacks to try and identify any gaps.


![VirtualBox_Kali_linux2023_12_04_2024_19_59_01](https://github.com/xOmari/Home-Lab/assets/159092818/3577e4a9-2772-4a03-acda-a08f973a04c4)

Editing Password list

![VirtualBox_Kali_linux2023_13_04_2024_09_12_10](https://github.com/xOmari/Home-Lab/assets/159092818/e6e8e14a-ade3-4faa-ae7a-3cf683747b8a)


![VirtualBox_Kali_linux2023_13_04_2024_09_15_59](https://github.com/xOmari/Home-Lab/assets/159092818/6e97fffd-145c-4bd6-bf16-10a0f635f414)

We will using crowbar as our brute force tool

![IMG_0175](https://github.com/xOmari/Home-Lab/assets/159092818/416f96ef-92fc-4a8e-92f3-0dfdba3f32cf)

Next we will see what telemetry was created

![IMG_0180](https://github.com/xOmari/Home-Lab/assets/159092818/88aff397-c82e-440f-bc54-29363cf9f534)

![IMG_0176](https://github.com/xOmari/Home-Lab/assets/159092818/7757c0fc-25cc-493f-b814-e22dca98fdf1)

With log event IDs we can tell what happened on a system

![IMG_0181](https://github.com/xOmari/Home-Lab/assets/159092818/d1d4065b-2759-45f2-9a4b-39c261518bb2)

Add a exclusion file for atomic Red team

![IMG_0185](https://github.com/xOmari/Home-Lab/assets/159092818/83c9422b-a380-49d8-b8fe-fbdf922570bb)

![IMG_0187](https://github.com/xOmari/Home-Lab/assets/159092818/eb501e45-b4a5-41c8-b7bf-21cecdcb9a90)

![IMG_0188](https://github.com/xOmari/Home-Lab/assets/159092818/0a6f1af0-9404-4397-8de4-cbe429474970)

Atomic red team's attacks has IDs so we use whichever we want to test
If we test something and recieve to telemetry we know we have a security gap

![IMG_0189](https://github.com/xOmari/Active-Directory-lab/assets/159092818/7e56fa57-4fac-42b1-b949-b7438ccd5d45)

In this test we see a Local user was created

![IMG_0192](https://github.com/xOmari/Active-Directory-lab/assets/159092818/5d82413d-cf4a-4af2-80e1-6ae5b3e0e114)

