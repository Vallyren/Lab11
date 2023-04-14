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

![2023-04-14_15-08-52](https://user-images.githubusercontent.com/122459067/232039633-33c1ee6a-546b-4fd0-8dee-e712275e3677.png)

##### Step 2: Configure basic settings for each router.
a.	Configure hostnames, as shown in the topology.
b.	Configure the interface IP addresses, as shown in the Addressing Table.

![2023-04-14_15-16-43](https://user-images.githubusercontent.com/122459067/232041144-33768e65-f935-4668-b054-63e2453062de.png)

![2023-04-14_15-19-37](https://user-images.githubusercontent.com/122459067/232041665-1e086771-98ed-487a-8e8e-245d5e6a8857.png)

![2023-04-14_15-22-40](https://user-images.githubusercontent.com/122459067/232042341-9c43ba1c-a5b4-4f99-a66f-31bea1832e9f.png)

![2023-04-14_15-24-26](https://user-images.githubusercontent.com/122459067/232042666-692237f5-e3f1-49c2-b0e3-4aab51985ab6.png)

![2023-04-14_15-25-26](https://user-images.githubusercontent.com/122459067/232042897-13c2fe7d-c8e8-4609-b643-b7a4fa4a81fd.png)

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

#### Part 2: Configure a Site-to-Site VPN with Cisco IOS
#### Task 1: Configure IPsec VPN Settings on R1 and R3.
##### Step 1: Enable IKE policies on R1 and R3.
IPsec is an open framework that allows for the exchange of security protocols as new technologies, and encryption algorithms as they are developed.
There are two central configuration elements in the implementation of an IPsec VPN:
Implement Internet Key Exchange (IKE) parameters
Implement IPsec parameters

a.	Verify that IKE is supported and enabled.
IKE Phase 1 defines the key exchange method used to pass and validate IKE policies between peers. In IKE Phase 2, the peers exchange and match IPsec policies for the authentication and encryption of data traffic.
IKE must be enabled for IPsec to function. IKE is enabled, by default, on IOS images with cryptographic feature sets. If it is disabled, you can enable it with the crypto isakmp enable command. Use this command to verify that the router IOS supports IKE and that it is enabled.

b.	Establish an ISAKMP policy and view the available options.
To allow IKE Phase 1 negotiation, you must create an ISAKMP policy and configure a peer association for that ISAKMP policy. An ISAKMP policy defines the authentication and encryption algorithms and the hash function used to send control traffic between the two VPN endpoints. When an ISAKMP security association has been accepted by the IKE peers, IKE Phase 1 has been completed. IKE Phase 2 parameters will be configured later.
Issue the crypto isakmp policy number global configuration mode command on R1 for policy 10.

c.	View the various IKE parameters available using Cisco IOS help by typing a question mark (?).

##### Step 2: Configure the IKE Phase 1 ISAKMP policy on R1 and R3.
a.	Configure an ISAKMP policy with a priority of 10. Use pre-shared key as the authentication type, aes 256 for the encryption algorithm, sha as the hash algorithm, and the Diffie-Hellman group 24 key exchange. Give the policy a lifetime of 3600 seconds (one hour).

b.	Configure the same policy on R3.

c.	Verify the IKE policy with the show crypto isakmp policy command.

##### Step 3: Configure pre-shared keys.
a.	Each IP address that is used to configure the IKE peers is also referred to as the IP address of the remote VPN endpoint. Configure the pre-shared key of cisco123 on router R1. Production networks should use a complex key. This command points to the remote peer R3 G0/0/0 IP address.

b.	Configure the pre-shared key cisco123 on router R3. The command for R3 points to the R1 S0/0/0 IP address.

##### Step 4: Configure the IPsec transform set and lifetime.
a.	The IPsec transform set is another crypto configuration parameter that routers negotiate to form a security association. To create an IPsec transform set, use the crypto ipsec transform-set tag command where tag is a name configured by the administrator. Use ? to see which parameters are available.

b.	On R1 and R3, create a transform set with tag R1-R3 and use an ESP transform with an AES 256 cipher with ESP and the SHA hash function. The transform sets must match on both ends of the VPN.
What is the function of the IPsec transform set?
Type your answers here.

c.	You can also change the IPsec security association lifetime from the default of 3600 seconds. On R1 and R3, set the IPsec security association lifetime to 30 minutes, or 1800 seconds.

##### Step 5: Define interesting traffic.
a.	Configure the IPsec VPN interesting traffic ACL on R1.

b.	Configure the IPsec VPN interesting traffic ACL on R3.
Does IPsec evaluate whether the access lists are mirrored as a requirement to negotiate its security association?
Type your answers here.

##### Step 6: Create and apply a crypto map.
a.	Create the crypto map on R1, name it CMAP, and use 10 as the sequence number. A message displays after the command is issued.

b.	Use the match address <access-list> command to specify which access list defines which traffic to encrypt.

c.	To view the list of possible set commands that you can do with a crypto map, use the help function.

d.	Setting a peer IP or hostname is required. Set it to R3’s remote VPN endpoint interface using the following command.

e.	Use the set transform-set tag command to hard code the transform set to be used with this peer. Set the perfect forwarding secrecy type using the set pfs type command, and modify the default IPsec security association life time with the set security-association lifetime seconds seconds command.

f.	Create a mirrored matching crypto map on R3.

g.	Apply the crypto maps to the appropriate interfaces on R1 and R3.

#### Task 2: Verify the Site-to-Site IPsec VPN Configuration.
##### Step 7: Verify the IPsec configuration on R1 and R3.
a.	Previously, you used the show crypto isakmp policy command to display the configured ISAKMP policies on the router. The show crypto ipsec transform-set command displays the configured IPsec policies in the form of the transform sets.

a.	Use the show crypto map command to display the crypto maps that will be applied to the router.

#### Task 3: Verify the IPsec VPN Operation.
##### Step 8: Display ISAKMP security associations.

##### Step 9: Display IPsec security associations.

Question:
Why haven’t any SAs been negotiated?
Type your answers here.

##### Step 10: Generate some uninteresting test traffic and observe the results.
a.	Ping from R1 to the R3 G0/0/0 interface IP address 10.2.2.1. These pings should be successful.
b.	Issue the show crypto isakmp sa command.
c.	Ping from R1 to the R3 G0/0/1 interface IP address 192.168.3.1. These pings should be successful.
d.	Issue the show crypto isakmp sa command again.
Question:
Was an SA created for these pings? Explain.
Type your answers here.
e.	Issue the debug ip ospf hello command. You should see OSPF hello packets passing between R1 and R3.
f.	Turn off debugging with the no debug ip ospf hello or undebug all command.
g.	Re-issue the show crypto isakmp sa command.
Question:
Was an SA created between R1 and R3? Explain.
Type your answers here.

##### Step 11: Generate some interesting test traffic and observe the results.
a.	Use an extended ping from R1 to the R3 G0/1 interface IP address 192.168.3.1. Extended ping allows you to control the source address of the packets. Respond as shown in the following example. Press Enter to accept the defaults, except where a specific response is indicated.

h.	Re-issue the show crypto isakmp sa command.
Questions:
Why was an SA created between R1 and R3 this time?
Type your answers here.
What are the endpoints of the IPsec VPN tunnel?
Type your answers here.
i.	Ping from PC-A to PC-C and then issue the show crypto ipsec sa command.
Question:
How many packets have been transformed between R1 and R3?
