# Lab11
## Lab - Configure a Site-to-Site VPN 
### Topology

![2023-04-14_13-15-55](https://user-images.githubusercontent.com/122459067/232017750-6e24afe1-ceab-4a49-aa17-9c810ebe2ff3.png)

### Addressing Table

![2023-04-14_13-16-46](https://user-images.githubusercontent.com/122459067/232018020-f8014642-56a4-4d37-a9d5-0aafef86d757.png)

### Objectives

#### Part 1: Configure Basic Device Settings

Configure hostnames, interface IP addresses, and access passwords.
Configure the OSPF dynamic routing protocol.

#### Part 2: Configure a Site-to-Site VPN Using Cisco IOS

Configure IPsec VPN settings on R1 and R3.
Verify site-to-site IPsec VPN configuration.
Test IPsec VPN operation.

#### Part 1: Configure Basic Device Settings

##### Step 1: Cable the network as shown in the topology.
a.	Configure hostnames, as shown in the topology.
b.	Configure the interface IP addresses, as shown in the Addressing Table.


##### Step 2: Configure basic settings for each router.

##### Step 3: Disable DNS lookup.

##### Step 4: Configure the OSPF routing protocol on R1, R2, and R3.
a.	On R1, use the following commands:

b.	On R2, use the following commands:

c.	On R3, use the following commands:


##### Step 5: Configure PC host IP settings.
a.	Configure a static IP address, subnet mask, and default gateway for PC-A, as shown in the IP Addressing Table.
b.	Configure a static IP address, subnet mask, and default gateway for PC-C, as shown in the IP Addressing Table.


##### Step 6: Verify basic network connectivity.
a.	Ping from R1 to the R3 G0/0/1 interface at IP address 192.168.3.1.
If the pings are unsuccessful, troubleshoot the basic device configurations before continuing.
b.	Ping from PC-A on the R1 LAN to PC-C on the R3 LAN.
If the pings are unsuccessful, troubleshoot the basic device configurations before continuing.


##### Step 7: Configure and encrypt passwords.
a.	Configure a minimum password length.
Use the security passwords command to set a minimum password length of 10 characters.
b.	Configure the enable secret password on both routers with a password of cisco12345. Use the type 9 (SCRYPT) hashing algorithm.
c.	Create a local admin01 account using admin01pass for the password. Use the type 9 (SCRYPT) hashing algorithm.


##### Step 8: Configure the console line.
Configure the console to use the local database for login. For additional security, configure the line to log out after five minutes of inactivity. Issue the logging synchronous command to prevent console messages from interrupting command entry.

##### Step 9: Configure SSH Server.
a.	Configure a domain name netsec.com.
b.	Configure the RSA keys with 2048 for the number of modulus bits.
c.	Issue the command to force the use of SSH version 2.
d.	Configure the vty lines on R1 and R3 to use the local database for login. Remote access to the routers should only be allowed using SSH. Configure the vty lines to logout after five minutes of inactivity.


##### Step 10: Save the basic running configuration for all three routers.
Save the running configuration to the startup configuration from the privileged EXEC mode prompt on R1, R2, and R3.
