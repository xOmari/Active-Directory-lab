# Home-Lab


## Objective


The Detection Lab project aimed to establish a controlled environment for simulating and detecting cyber attacks. The primary focus was to ingest and analyze logs within a Security Information and Event Management (SIEM) system, generating test telemetry to mimic real-world attack scenarios. This hands-on experience was designed to deepen understanding of network security, attack patterns, and defensive strategies.

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
- Network analysis tools (such as Wireshark) for capturing and examining network traffic.
- Telemetry generation tools to create realistic network traffic and attack scenarios.

## Steps

NetWork Architecture

![Screenshot 2024-04-14 202511](https://github.com/xOmari/Home-Lab/assets/159092818/141a4d73-4a85-4ba9-9d51-0e2467050dcc)


For this project ive Installed four Virtual Machines : Kali linux , Windows 2019 server for Active directory , Linux server for Splunk and Windows 10 as my target Machine.


![Screenshot 2024-04-15 092652](https://github.com/xOmari/Home-Lab/assets/159092818/ff5622a5-d766-4f4a-837c-28f0df9735d2)

Next I set up a Static ipaddress for my splunk server using: Sudo nano /etc/netplan/00-installer-config.yaml

![VirtualBox_splunk S_15_04_2024_10_46_28](https://github.com/xOmari/Home-Lab/assets/159092818/80b719eb-0e4b-486f-b402-32adf731fc6f)

Next I download splunk From their official website along with virtualbox guest additions so i can access on the splunk server using a shared folder.

Next we mount the file and begin installation

![VirtualBox_splunk S_18_03_2024_18_34_55](https://github.com/xOmari/Home-Lab/assets/159092818/582a014e-7cc3-4aee-b941-231a769219ed)




