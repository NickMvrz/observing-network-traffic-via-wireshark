

![WIRESHARK](https://github.com/user-attachments/assets/7ae32197-93a1-4116-be32-7619ac495ffe)

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines using Wireshark</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />

<h2>Technologies used in this lab:</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Command Line/Powershell
- Various Network Protocols (ICMP, SSH, DHCP, DNS, RDP)
- Wireshark (Data Packet Analyzer)

<h2>Operating Systems Used:</h2>

- Windows 10 (21H2)
- Ubuntu Server 22.04

<h2>List of Steps:</h2>

- Create a Resource Group
- Create a Virtual Machine
- Observe ICMP Traffic
- Observe SSH Traffic
- Observe DHCP Traffic
- Observe DNS Traffic
- Observe RDP Traffic

 <h3 align="center">Download Wireshark via Virtual Machine</h3>

<p>
</p>
<p>- Remote into your Windows 10 Virtual Machine, install Wireshark, open it and filter for ICMP traffic only.</p>
<p>  
</p>
<img width="499" alt="Screenshot 2024-12-18 at 6 26 40 PM" src="https://github.com/user-attachments/assets/24b769aa-cd1a-4190-917c-505ccf1c876a" />

<img width="783" alt="Screenshot 2024-12-18 at 6 29 00 PM" src="https://github.com/user-attachments/assets/a8ed705b-d278-4289-a67c-a80c7422191f" />

<img width="788" alt="Screenshot 2024-12-18 at 6 29 28 PM" src="https://github.com/user-attachments/assets/c6c26944-ab91-4b31-9d90-3c0ea1187b91" />

<h3 align="center">Observing ICMP Traffic</h3>

<img width="1512" alt="Screenshot 2024-12-18 at 6 30 50 PM" src="https://github.com/user-attachments/assets/28836e71-90b1-42ac-a4eb-87abb130d5a0" />
</p>
<p>
  Retrieve the private IP address of the Ubuntu VM and attempt to ping it from within the Windows 10 VM. Observe ping requests and replies within WireShark:
</p>
<p>

<img width="787" alt="Screenshot 2024-12-18 at 6 31 29 PM" src="https://github.com/user-attachments/assets/1cea01f6-3813-4978-9540-bcc43e98fb8d" />

<img width="981" alt="Screenshot 2024-12-18 at 6 32 21 PM" src="https://github.com/user-attachments/assets/7e5ddb15-4a29-47b5-b76a-37340ab0add9" />

<img width="1512" alt="Screenshot 2024-12-18 at 6 32 42 PM" src="https://github.com/user-attachments/assets/31483547-b6ff-4ebd-9616-e9d963ecede2" />

<img width="753" alt="Screenshot 2024-12-18 at 6 34 45 PM" src="https://github.com/user-attachments/assets/de172ae6-58cc-48f0-8b73-8ecc1f19546f" />

<img width="752" alt="Screenshot 2024-12-18 at 6 35 42 PM" src="https://github.com/user-attachments/assets/f92efb64-b89f-4b1f-8ad8-70f98c2f0061" />
</p>
<p>
  Initiate a perpetual/non-stop ping from your Windows 10 VM to your Ubuntu VM:
</p>
<p>

<img width="740" alt="Screenshot 2024-12-18 at 6 38 34 PM" src="https://github.com/user-attachments/assets/f98194a0-7dd0-450c-ab0b-87ec145798cd" />
</p>
<p>
  Open the Network Security Group your Ubuntu VM is using and disable incoming (inbound) ICMP traffic, while back in the Windows 10 VM, observe the ICMP traffic in WireShark and the command line Ping activity:
</p>
<p>

<img width="1199" alt="Screenshot 2024-12-18 at 6 41 55 PM" src="https://github.com/user-attachments/assets/14b34c50-11d9-47ee-8be7-2c9eeb5f80aa" />

<img width="287" alt="Screenshot 2024-12-18 at 6 42 08 PM" src="https://github.com/user-attachments/assets/9e7ea3f3-be9d-4d86-b8a5-fb53a67814e6" />

<img width="588" alt="Screenshot 2024-12-18 at 6 45 08 PM" src="https://github.com/user-attachments/assets/0aa9d2fa-9c70-4be7-8d6f-67abac9f4dba" />
<p>
  Re-enable ICMP traffic for the Network Security Group in your Ubuntu VM and back in the Windows 10 VM, observe the ICMP traffic in WireShark and the command line ping activity (should start working again).Finally, stop the ping activity:
</p>
<p>

<img width="927" alt="Screenshot 2024-12-18 at 6 46 14 PM" src="https://github.com/user-attachments/assets/d1422022-982c-4a0b-a621-88c94e25a491" />
<h3 align="center">Observing SSH Traffic</h3>
<br />
<p>
  Back in Wireshark, filter for SSH traffic only and from your Windows 10 VM, “SSH into” your Ubuntu virtual machine (via its private IP address). Type commands (ls, pwd, etc) into the linux SSH connection and observe SSH traffic spam in WireShark.
</p>
</p>
  Exit the SSH connection by typing ‘exit’ and pressing [return]:
</p>

<img width="674" alt="Screenshot 2024-12-18 at 6 48 30 PM" src="https://github.com/user-attachments/assets/c1a7bdaf-2b7c-4596-b5f5-9ca051e2ec47" />

<img width="721" alt="Screenshot 2024-12-18 at 6 51 51 PM" src="https://github.com/user-attachments/assets/992b875c-dd45-4c54-8fea-09ca4e124288" />
 <h3 align="center">Observing DHCP Traffic</h3>
<br />
<p>
  Back in Wireshark, filter for DHCP traffic only. From your Windows 10 VM, attempt to issue your VM a new IP address from the command line (ipconfig /renew)
</p>

<img width="800" alt="Screenshot 2024-12-18 at 6 56 39 PM" src="https://github.com/user-attachments/assets/d667ee71-5183-4eed-ae46-2e4cab1f07e9" />

<img width="1439" alt="Screenshot 2024-12-18 at 7 04 07 PM" src="https://github.com/user-attachments/assets/eda4f314-ccbe-44d7-b1b1-056110b64837" />
<h3 align="center">
  Let's now observe our DNS traffic next
</h3>
<br />
<p>
  Back in Wireshark, filter for DNS traffic only.
</p>
<p>
  From your Windows 10 VM within a command line, use nslookup to see what google.com and disney.com’s IP addresses are and observe the DNS traffic being shown in WireShark:
</p>
<p>

<img width="1511" alt="Screenshot 2024-12-18 at 8 13 06 PM" src="https://github.com/user-attachments/assets/551b75a0-26ae-45ad-b8b5-e632ae6cb62a" />
<br />
<h3 align="center">Observing RDP Traffic</h3>
<br />
<p>
  Back in Wireshark, filter for RDP traffic only using "tcp.port==3389".
</p>
<p>
<img width="495" alt="Screenshot 2024-12-18 at 8 15 15 PM" src="https://github.com/user-attachments/assets/e13df9a9-0be2-4fc3-b2c4-e0bc9b25b9ce" />
<p>
  You'll notice the constant stream of traffic. Why is it continuous?
</p>
<p>
 RDP is constantly showing you a live stream from one computer to another, so traffic is always being transmitted:
</p>

<img width="1508" alt="Screenshot 2024-12-18 at 8 19 35 PM" src="https://github.com/user-attachments/assets/532e8149-d5e0-483b-96a6-96eea8b4746a" />
















