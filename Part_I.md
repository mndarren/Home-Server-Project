# Part 1, Setup a Home Server
----------------------------
1. Hardware Preparation:
   ```
   Router version: NETGEAR N300 WiFi Cable Modem Router Model: C3000
   Server box version: Lenovo ThinkServer TS140 [No OS] Intel Core i3-4130 3.4GHz 8GB RAM No HDD Server 
   ```
2. Software Preparation & Architecture:
   ```
   ESXi 6.5,
   OS iso files (Debian 8, Windows 7, SUSE 11.3, Oracle Linux 7, etc)
   ```
   ![alt text](https://github.com/mndarren/Home-Server-Project/blob/master/resource/architecture.png)  

3. Create bootable flash drive:  
   Tool: `Rufus` (the best tool to create bootable USB disk)  
   Use rufus to build `ESXi 6.5` bootable USB disk.  
   ![alt text](https://github.com/mndarren/Home-Server-Project/blob/master/resource/Rufus.png)

4. Install ESXi on the Server Box  
   During installation, REMEMBER the password otherwise we have to reinstall it.  
   ![alt text](https://github.com/mndarren/Home-Server-Project/blob/master/resource/InstallESXi.png)  
   Note:  
   1) Add `hard drive` in the server box if without hard drive in server.
   2) Connect router with server using internet wire.
   3) Need a `monitor` and a `keyboard` to install ESXi. After installation, don't need them anymore.
   4) Remember the IP address since it will be used to remote the server.

5. Build VMs
   1) Upload iso files into data center
   2) Insert iso file into DVD drive
   3) Install OS on VMs  
   ![alt text](https://github.com/mndarren/Home-Server-Project/blob/master/resource/InstallVM.png)

6. Configure Router -- **Set up DDNS**  
   Why to do this?  
   ISP only provides dynamic IP for our home internet.  
   That means our home IP address will be changed usually. With DDNS, this problem is solved!<br /><br />
   With two options NoIP and DynDNS, we choose NoIP because it's free right now.  
   There are other DDNS service providers. Why to choose these two options? For better services.   
   1) Login noip.com web site and set up your free domain. Renew it once/30 days;
   2) Fill up the same user name and password with NoIP on your router;  
   ![alt text](https://github.com/mndarren/Home-Server-Project/blob/master/resource/DDNS.png)
   3) In a Windows VM, download the little tool from NoIp web site, named DDNS Update Client (DUC);
      Setup DUC--login and choose the domain. This little software will update you Dynamic IP once/5 minutes
   ![alt text](https://github.com/mndarren/Home-Server-Project/blob/master/resource/DUC.png)

7. Configure Router -- **Port Forwarding**  
   Why to do this?  
   All of VMs have private IP addresses. Outside computer cannot touch them directly.  
   With Port forwarding, this problem is solved!  
   ![alt text](https://github.com/mndarren/Home-Server-Project/blob/master/resource/PortForwarding.png)

8. Strong Recommendation -- **TeamViewer**  
   Why to do this?  
   Sometimes some of your settings gets failed. You couldn't access your VMs from outside your home network.  
   For example, if you forget to comfirm your NoIP, that happens.  
   With TeamViewer in these cases, you still can access your VMs via TeamViewer.  
   We can use TeamViewer to modify the settings to make service work.  
   ![alt text](https://github.com/mndarren/Home-Server-Project/blob/master/resource/TeamViewer.png)

Notes:
   1) Don't forget to confirm your NoIP domain in noip.com every month!
   2) Keep your Windows VM not to sleep, otherwise you cannot find it via TeamViewer!
   3) Install VMware tools for each VM to make easy to check the information.