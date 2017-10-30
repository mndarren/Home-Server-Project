# Part II Implement Data Security Technology on the Home Server
================================================================

1. Implement Layered Security using Cloud Zone(Design)  
----------------------------------------------
![alt text](https://github.com/mndarren/Home-Server-Project/blob/master/resource/cloud_zone.png)  
   ```
   1) Network configuration
      i) Gateway VM network configuration: 
         Set up 2 NICs (one for this zone itself gateway, another for connection to outside of the zone)
        --> Modify the /etc/network/interfaces file. In this case, the Debians are used
          to simulate it. The detail settings are shown in the following snapshots.
        --> Restart network service ($sudo service networking restart)
      ii) Zone VM network configuration:
      	  Only need one NIC
      	--> In the /etc/network/interfaces file, set up the gateway to the one gateway VM uses,
      	  and determine specific net mask based on how many zones you need. In this case, set up 4 zones
   2) IP forward enable
         Run this command ($echo 1 > /proc/sys/net/ipv4/ip_forward)
     --> Check if it works ($cat /proc/sys/net/ipv4/ip_forward), return 1 means it works.

   3) Test the new network
         $ping www.google.com  #ping any web domain from gateway VM and zone inside VM
   ```
![alt text](https://github.com/mndarren/Home-Server-Project/blob/master/resource/gateway_network.png)  
![alt text](https://github.com/mndarren/Home-Server-Project/blob/master/resource/zone_network.png)
