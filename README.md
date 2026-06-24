# Active-Directory-Home-Lab

Introduction: 
  This project is a simulated Active Directory environment to practice identity + access management and endpoint configuration.

Architecture: 
  -Oracle Virtualbox
  -Server OS -> Windows Server 2022
  -Client OS -> Windows 11
  -Static IP -> 

Skills Demonstrated: A quick bulleted list of buzzwords for recruiters (e.g., Group Policy Management, Role-Based Access Control, DHCP/DNS Configuration, Active Directory Provisioning).

Implementation Steps: 
  ###
  Build Steps:
  1. Create a new virtualbox vm with windows 2022 ISO
      -set network adaptor to host only
      -at least 4 processors and 4096 mbs of mem
  2. rename server and set static ip address
  3. install active directory and promote it to domain controller

Challenges & Troubleshooting: 
  Problem: Installed the server core instead of the desktop experience for windows 2022 server
  Solution: Wiped the VM and reinstalled with Unattended Guest Installation turned off

  6/24
  Problem: Configured scope of new DHCP server to 192.168.10.100-192.168.10.244 when my active directory/dns server sits on 192.168.15
  Solution: Deleted the scope and created new with matching ip

  Problem: DNS server would not start, waiting for initial sync signal from AD DS
  Solution: added register key Repl Perform Initial Synchronizations to tell AD DS normal sync not necessary

  Problem: New client vm isolated from domain controller
  Solution: used ipconfig to check ip address, switched network mode to internal network with same name, used ipconfig /release and ipconfig /renew to obtain new addr
