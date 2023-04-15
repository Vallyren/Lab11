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

##### Step 3: Disable DNS lookup.

![2023-04-14_15-30-14](https://user-images.githubusercontent.com/122459067/232043894-085aed90-cbd0-4a6a-8a34-03ac44ac50be.png)

![2023-04-14_15-31-01](https://user-images.githubusercontent.com/122459067/232044032-6d87795f-6d58-4d80-b011-572172b61395.png)

![2023-04-14_15-31-36](https://user-images.githubusercontent.com/122459067/232044166-21ec1761-1043-4372-b4ba-1b16414714ec.png)

##### Step 4: Configure the OSPF routing protocol on R1, R2, and R3.

a.	On R1, use the following commands:

![2023-04-14_15-33-32](https://user-images.githubusercontent.com/122459067/232044643-2840c01e-d0d1-4a08-a46e-8cdb401cc669.png)

b.	On R2, use the following commands:

![2023-04-14_15-34-54](https://user-images.githubusercontent.com/122459067/232044895-097a2dc2-ecaf-4883-bf1b-1eda78cdc0c9.png)

c.	On R3, use the following commands:

![2023-04-14_15-35-54](https://user-images.githubusercontent.com/122459067/232045136-bbe7113c-12f8-462e-a349-34c35d26a2d1.png)

##### Step 5: Configure PC host IP settings.

a.	Configure a static IP address, subnet mask, and default gateway for PC-A, as shown in the IP Addressing Table.

![2023-04-14_15-24-26](https://user-images.githubusercontent.com/122459067/232042666-692237f5-e3f1-49c2-b0e3-4aab51985ab6.png)

b.	Configure a static IP address, subnet mask, and default gateway for PC-C, as shown in the IP Addressing Table.

![2023-04-14_15-25-26](https://user-images.githubusercontent.com/122459067/232042897-13c2fe7d-c8e8-4609-b643-b7a4fa4a81fd.png)

##### Step 6: Verify basic network connectivity.

a.	Ping from R1 to the R3 G0/0/1 interface at IP address 192.168.3.1.
If the pings are unsuccessful, troubleshoot the basic device configurations before continuing.

![2023-04-14_15-39-12](https://user-images.githubusercontent.com/122459067/232045908-927fde5d-8ff8-4a70-9057-9af6eedcd7c8.png)

b.	Ping from PC-A on the R1 LAN to PC-C on the R3 LAN.
If the pings are unsuccessful, troubleshoot the basic device configurations before continuing.

![2023-04-14_15-40-05](https://user-images.githubusercontent.com/122459067/232046082-3e0f8cde-023e-4a87-9a03-5d99dfa4e092.png)

##### Step 7: Configure and encrypt passwords.

a.	Configure a minimum password length. Use the security passwords command to set a minimum password length of 10 characters.

b.	Configure the enable secret password on both routers with a password of cisco12345. Use the type 9 (SCRYPT) hashing algorithm.

c.	Create a local admin01 account using admin01pass for the password. Use the type 9 (SCRYPT) hashing algorithm.

![2023-04-14_15-49-09](https://user-images.githubusercontent.com/122459067/232048247-dcfa6859-643a-46a5-8462-c44d277a0ec4.png)

![2023-04-14_15-51-13](https://user-images.githubusercontent.com/122459067/232048524-a0a57002-3657-4099-93d3-8f6cc523a820.png)

##### Step 8: Configure the console line.
Configure the console to use the local database for login. For additional security, configure the line to log out after five minutes of inactivity. Issue the logging synchronous command to prevent console messages from interrupting command entry.

##### Step 9: Configure SSH Server.

a.	Configure a domain name netsec.com.

b.	Configure the RSA keys with 2048 for the number of modulus bits.

c.	Issue the command to force the use of SSH version 2.

d.	Configure the vty lines on R1 and R3 to use the local database for login. Remote access to the routers should only be allowed using SSH. Configure the vty lines to logout after five minutes of inactivity.

![2023-04-14_16-03-08](https://user-images.githubusercontent.com/122459067/232051330-53d4ca0e-6834-47dc-811d-7363e3128345.png)

![2023-04-14_16-04-46](https://user-images.githubusercontent.com/122459067/232051581-d25052ea-0ebc-437c-80aa-76ab50a75067.png)

![2023-04-14_16-08-05](https://user-images.githubusercontent.com/122459067/232052444-3371f9bf-4719-4275-aaa9-2fd624b92f8f.png)

![2023-04-14_16-10-53](https://user-images.githubusercontent.com/122459067/232053031-fe2ccaff-9ab2-4ec9-92c3-14391062ee03.png)

##### Step 10: Save the basic running configuration for all three routers. Save the running configuration to the startup configuration from the privileged EXEC mode prompt on R1, R2, and R3.

![2023-04-14_16-12-46](https://user-images.githubusercontent.com/122459067/232053395-a7a2a2ea-d0d2-4d89-991b-5de609b35c60.png)

![2023-04-14_16-13-28](https://user-images.githubusercontent.com/122459067/232053530-0f0f23fa-756a-4db8-893b-a0a8818f1772.png)

![2023-04-14_16-14-00](https://user-images.githubusercontent.com/122459067/232053647-391da143-3bcd-49a4-b818-75175cdb74f7.png)

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

![2023-04-14_16-21-54](https://user-images.githubusercontent.com/122459067/232055427-1a0a52d6-028c-4a31-9d80-83d29127d3fe.png)

![2023-04-14_16-24-03](https://user-images.githubusercontent.com/122459067/232055953-b6fecb11-73d0-4d73-9533-28fc4bfb95c9.png)

b.	Establish an ISAKMP policy and view the available options.
To allow IKE Phase 1 negotiation, you must create an ISAKMP policy and configure a peer association for that ISAKMP policy. An ISAKMP policy defines the authentication and encryption algorithms and the hash function used to send control traffic between the two VPN endpoints. When an ISAKMP security association has been accepted by the IKE peers, IKE Phase 1 has been completed. IKE Phase 2 parameters will be configured later.
Issue the crypto isakmp policy number global configuration mode command on R1 for policy 10.

![2023-04-14_16-26-44](https://user-images.githubusercontent.com/122459067/232056586-77e8f358-f345-4874-a55d-c0c1ab253452.png)

c.	View the various IKE parameters available using Cisco IOS help by typing a question mark (?).

![2023-04-14_16-27-44](https://user-images.githubusercontent.com/122459067/232056783-4907bf50-0ea2-44a4-b4b0-b5c09d2268e3.png)

##### Step 2: Configure the IKE Phase 1 ISAKMP policy on R1 and R3.
a.	Configure an ISAKMP policy with a priority of 10. Use pre-shared key as the authentication type, aes 256 for the encryption algorithm, sha as the hash algorithm, and the Diffie-Hellman group 24 key exchange. Give the policy a lifetime of 3600 seconds (one hour).

![2023-04-14_16-31-13](https://user-images.githubusercontent.com/122459067/232057567-fef7ffff-4928-41cc-959c-beb05d4dd32f.png)

b.	Configure the same policy on R3.

![2023-04-14_16-32-53](https://user-images.githubusercontent.com/122459067/232057889-be9e19c1-ee65-436f-ad52-a5458b14a037.png)

c.	Verify the IKE policy with the show crypto isakmp policy command.

![2023-04-14_16-33-38](https://user-images.githubusercontent.com/122459067/232058048-43697a68-dffd-4c68-b7dc-088b6a9654f9.png)

![2023-04-14_16-34-13](https://user-images.githubusercontent.com/122459067/232058173-053f33c0-d93b-4ede-97a3-71a911ac7e00.png)

##### Step 3: Configure pre-shared keys.
a.	Each IP address that is used to configure the IKE peers is also referred to as the IP address of the remote VPN endpoint. Configure the pre-shared key of cisco123 on router R1. Production networks should use a complex key. This command points to the remote peer R3 G0/0/0 IP address.

![2023-04-14_16-45-24](https://user-images.githubusercontent.com/122459067/232060805-fd8b36d2-066e-4ee3-8e08-f4e6802a86f6.png)

b.	Configure the pre-shared key cisco123 on router R3. The command for R3 points to the R1 S0/0/0 IP address.

![2023-04-14_16-46-13](https://user-images.githubusercontent.com/122459067/232061035-4887b790-703e-4808-81ca-c703a0a2b4c3.png)

##### Step 4: Configure the IPsec transform set and lifetime.
a.	The IPsec transform set is another crypto configuration parameter that routers negotiate to form a security association. To create an IPsec transform set, use the crypto ipsec transform-set tag command where tag is a name configured by the administrator. Use ? to see which parameters are available.

![2023-04-14_16-47-47](https://user-images.githubusercontent.com/122459067/232061478-4661de5e-31d1-4370-97bd-6595a967292a.png)

b.	On R1 and R3, create a transform set with tag R1-R3 and use an ESP transform with an AES 256 cipher with ESP and the SHA hash function. The transform sets must match on both ends of the VPN.
What is the function of the IPsec transform set?
Type your answers here.

![2023-04-14_16-48-45](https://user-images.githubusercontent.com/122459067/232061719-97275910-0a1f-4462-a3e1-01eb53e4d093.png)

![2023-04-14_16-49-33](https://user-images.githubusercontent.com/122459067/232061989-e9262f36-2953-4e14-b538-e94072936099.png)

c.	You can also change the IPsec security association lifetime from the default of 3600 seconds. On R1 and R3, set the IPsec security association lifetime to 30 minutes, or 1800 seconds.

![2023-04-14_16-50-09](https://user-images.githubusercontent.com/122459067/232062273-6ff45a16-69c0-455e-924d-94cbf56d9d53.png)

![2023-04-14_16-50-52](https://user-images.githubusercontent.com/122459067/232062594-ca37bcb7-9b5b-4243-900a-430133736c27.png)

##### Step 5: Define interesting traffic.
a.	Configure the IPsec VPN interesting traffic ACL on R1.

![2023-04-14_16-53-42](https://user-images.githubusercontent.com/122459067/232063699-9655bc1a-c20e-4f0f-ab53-840e2b0442ed.png)

b.	Configure the IPsec VPN interesting traffic ACL on R3.
Does IPsec evaluate whether the access lists are mirrored as a requirement to negotiate its security association?
Type your answers here.

![2023-04-14_16-54-32](https://user-images.githubusercontent.com/122459067/232063978-b746ea6f-9c4f-4583-a12b-4ce9e5cb4def.png)

##### Step 6: Create and apply a crypto map.

a.	Create the crypto map on R1, name it CMAP, and use 10 as the sequence number. A message displays after the command is issued.

![2023-04-14_16-56-19](https://user-images.githubusercontent.com/122459067/232064600-4cf495bd-f381-431b-888f-c971166e35fe.png)

b.	Use the match address <access-list> command to specify which access list defines which traffic to encrypt.

![2023-04-14_16-57-11](https://user-images.githubusercontent.com/122459067/232064933-a9f220b2-0da0-492e-b1ba-cb84c41fbea8.png)

c.	To view the list of possible set commands that you can do with a crypto map, use the help function.

![2023-04-14_16-58-14](https://user-images.githubusercontent.com/122459067/232065173-820a0ed0-d9df-444a-bd9d-62458933e8be.png)

d.	Setting a peer IP or hostname is required. Set it to R3’s remote VPN endpoint interface using the following command.

![2023-04-14_16-59-08](https://user-images.githubusercontent.com/122459067/232065486-18a10872-e0de-4ffa-a829-0c6c477322a2.png)

e.	Use the set transform-set tag command to hard code the transform set to be used with this peer. Set the perfect forwarding secrecy type using the set pfs type command, and modify the default IPsec security association life time with the set security-association lifetime seconds seconds command.

![2023-04-15_08-51-48](https://user-images.githubusercontent.com/122459067/232187176-b840002e-d2cf-419a-9c9d-578fbfad26fe.png)

![2023-04-15_08-55-25](https://user-images.githubusercontent.com/122459067/232187267-a6b6ae70-d30c-426d-871f-f593faa23441.png)

f.	Create a mirrored matching crypto map on R3.

![2023-04-15_08-57-55](https://user-images.githubusercontent.com/122459067/232187357-6a423a2b-10f3-4e1b-86a0-8445829e8d4b.png)

g.	Apply the crypto maps to the appropriate interfaces on R1 and R3.

![2023-04-15_08-59-25](https://user-images.githubusercontent.com/122459067/232187421-0cbe8f5a-5627-448a-b8f9-20da7808de1c.png)

![2023-04-15_09-00-26](https://user-images.githubusercontent.com/122459067/232187452-f92f46b5-c845-4530-b15d-aa0208edd041.png)

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
