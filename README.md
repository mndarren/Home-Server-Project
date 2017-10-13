# Home Server Project
==============================

Goal: 
-----
1. Set up a Home Server using a server box and a home router.
2. Build a security environment implementing Security technologies, such as cloud layered security,
   VPN, 2-factor authentication, etc
3. Create a Web Server and a DB server in the security environment.

Part 1, set up a Home Server
----------------------------
1. Hardware Preparation:
```
   Router version: NETGEAR N300 WiFi Cable Modem Router Model: C3000
   Server box version: Lenovo ThinkServer TS140 [No OS] Intel Core i3-4130 3.4GHz 8GB RAM No HDD Server 
``` 
2. Software Preparation:
```
   ESXi 6.5,
   OS iso files (Debian 8, Windows 7, SUSE 11.3, Oracle Linux 7, etc)
```
3. Create bootable flash drive:
   Tool: Rufus (the best tool to create bootable USB disk)
   Use rufus to build ESXi 6.5 bootable USB disk.
   ![alt text](https://github.com/mndarren/Home-Server-Project/blob/master/resource/Rufus.png)

4. Install ESXi on the Server Box
   During installation, REMEMBER the password otherwise we have to reinstall it.

5. Build VMs
   -- Upload iso files into data center
   -- Insert iso file into DVD drive
   -- Install OS on VMs

6. Configure Router -- Set up DDNS
   With two options NoIP and DynDNS, we choose NoIP because it's free right now.
   There are other DDNS service providers. Why to choose these two options? For better services.
   1) Login noip.com web site and set up your free domain. Renew it once/30 days;
   2) Fill up the same user name and password with NoIP on your router;
   3) In a Windows VM, download the little tool from NoIp web site, named DDNS Update Client (DUC);
        Setup DUC--login and choose the domain. This little software will update you Dynamic IP once/5 minutes
   
7. Configure Router -- Port Forwarding
      