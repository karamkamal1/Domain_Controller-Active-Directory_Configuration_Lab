## Diagram
This network diagram outlines the setup for our upcoming lab environment. In this scenario, the client computer is configured to route all internet traffic through the internal network, ultimately passing through the domain controller for internet access. This design utilizes a domain controller (DC) that serves dual purposes: managing domain resources and handling network routing with RAS/NAT functionalities. 
![Screenshot (149)](https://github.com/user-attachments/assets/9d2b9083-431d-4be8-beea-201f24951ea9)


## Steps
![Screenshot (181)](https://github.com/user-attachments/assets/2fc44589-4d67-44a4-9bdb-566a0451330e)
This is our virtual machine or Server running Windows Server 2019

--------------------------------------------------------------------------------------------

![Screenshot (49)](https://github.com/user-attachments/assets/a27996f7-1303-44e6-9f93-ff032653557b)
After a little time loading you're greeted by a Server Manager Dashboard this is where the majority of work is going to be done. But first we will need to go to the bottom right hand corner and click on the Network widget and click on unidentified network.

--------------------------------------------------------------------------------------------


![Screenshot (50)](https://github.com/user-attachments/assets/5b453ea0-621d-4215-b467-e32aea9eb47f)
A settings window will pop up for displaying our two networks. I have configured my server virtual machine to have one connection to the internet as well as one connection to the internal net like shown by the diagram. Now click on change adapter options so we can edit our connections.

--------------------------------------------------------------------------------------------

![Screenshot (51)](https://github.com/user-attachments/assets/28b35f07-0824-4679-8bce-b77cb7cc9087)
Here are our two network connections but how do we know which one is for the internet and which one is for the internal Network. 

--------------------------------------------------------------------------------------------

![Screenshot (53)](https://github.com/user-attachments/assets/9d6463b2-c6f9-4fce-aabe-20e70e41d180)
By right clicking on our Ethernet 1 connection and clicking on status we we are able to see the connection properties of the adapter. As you can see it has an IP that was automatically assigned by my home network letting us know this adapter has an internet connection.

--------------------------------------------------------------------------------------------

![Screenshot (54)](https://github.com/user-attachments/assets/14ac597c-004b-4248-aa75-572216c79116)
By following the same steps on Ethernet 2 we can see it has an IP starting with 169 this is an automatically assigned IP address by VirtualBox because it is unable to find a connection letting us know this is our internal network.

--------------------------------------------------------------------------------------------

![Screenshot (55)](https://github.com/user-attachments/assets/b32a5635-9085-463c-8af0-91fa57230aea)
Now lets right click on both and rename them to their coresponding use so they're easier to identify later. 

--------------------------------------------------------------------------------------------


![Screenshot (56)](https://github.com/user-attachments/assets/fe61415d-7fec-4f26-acba-1938e6828a2a)
Lastly we are going to right click on our Internal Net adapter and select properties. We will now click internet protocol version 4 and click on properties. This will allow us to assign an IP address, Gateway Mask and DNS to the Domain Controllers Internal Net Adapter.

--------------------------------------------------------------------------------------------

![Screenshot (57)](https://github.com/user-attachments/assets/c89b13c7-eccf-45e3-96bf-b966cade19de)
If you refer to the diagram you can see the assigned IP for the internal Network Adapter is 172.16.0.1, We will then assign our subnet mask to 255.255.255.0 as our IP is /24. We are not going to include a default gateway as our computer itself will be used as a default gateway. For the DNS our Domain Controller will be using itself for the DNS server so we can use a loopback address 127.0.0.1

--------------------------------------------------------------------------------------------

![Screenshot (58)](https://github.com/user-attachments/assets/6173977a-d227-4aef-8643-d28fb212c53d)
Now we can move on to installing Active Directory Domain Services. So open up or navigate to your Server Managment Dashboard. Click on Add Roles and Features.

--------------------------------------------------------------------------------------------

![Screenshot (59)](https://github.com/user-attachments/assets/1bc9c64b-1477-49bb-b324-9a00574ca8f4)
Click Next

--------------------------------------------------------------------------------------------

![Screenshot (60)](https://github.com/user-attachments/assets/c686b508-099b-433d-8f0f-1cb8f2f15e10)
Click Next

--------------------------------------------------------------------------------------------


![Screenshot (61)](https://github.com/user-attachments/assets/2475d874-16c1-454e-9535-b7296830a5b1)
Click Next

--------------------------------------------------------------------------------------------

![Screenshot (62)](https://github.com/user-attachments/assets/c60cbb4b-4378-46cb-9188-4b0661a8f9c2)

We are now going to check Active Directory Domain Services. Make sure you select the correct one for installation. Then Click Next.

--------------------------------------------------------------------------------------------

![Screenshot (63)](https://github.com/user-attachments/assets/07950ce0-fbc3-41fd-8f89-c9ccd14d0c8e)

Now Click Install. This can take some time to finish. Once its finished press close.

--------------------------------------------------------------------------------------------

![Screenshot (67)](https://github.com/user-attachments/assets/f5a550ce-682f-426a-8de2-742ba7e705cc)

Now that we're back on the Managment Dashboard were going to click on the flag with the warning symbol in the top right. When we click it we are greeted with Post Deployment Configuration. So the system is telling us to configure our newly installed Active Directory Domain. To start click on promote this server to a domain controller. 

--------------------------------------------------------------------------------------------

![Screenshot (70)](https://github.com/user-attachments/assets/2226b4d7-899f-4f4a-9a69-12418db73579)
A configuration window will pop up. You want to select new forest as it is a brand new directroy and name your domain. In my case I will be naming it githubdomain.com but you can name it anyhting you like an example being newdomain.com. Click Next

---------------------------------------------------------------------------------------------

![Screenshot (71)](https://github.com/user-attachments/assets/da7c9ab1-2692-4b91-a4ba-05f00739794d)
On the next page we will enter a password for DSRM we won't be using this in the lab but it is mandatory to continue the installation so enter a password and click next.

----------------------------------------------------------------------------------------------

![Screenshot (72)](https://github.com/user-attachments/assets/1045b1bc-af05-4112-b35f-f47d119b0ab1)
Click Next without checking the DNS Delegation Box.

----------------------------------------------------------------------------------------------

![Screenshot (73)](https://github.com/user-attachments/assets/d4affedc-d6a9-4a11-8071-2b9dd2bff47f)
It may take a minute to resolve the NETBIOs Domain Name once it does you will see the domain name you have entered earlier and click next.

----------------------------------------------------------------------------------------------

![Screenshot (74)](https://github.com/user-attachments/assets/b5d9ec21-7465-455d-97da-13b489a199fa)
Click Next

----------------------------------------------------------------------------------------------

![Screenshot (75)](https://github.com/user-attachments/assets/12c7b529-f087-4db6-9bf5-31034a88d165)
Click Next

----------------------------------------------------------------------------------------------

![Screenshot (76)](https://github.com/user-attachments/assets/ede6e3e5-73cf-49e1-99cd-626c176a145a)
Now it will take some time to do a prerequisite check so leave it alone. Once it finishes the check press Install. Once install finishes click close.

----------------------------------------------------------------------------------------------

![Screenshot (79)](https://github.com/user-attachments/assets/6723b2a4-062c-449c-912c-bbaa665f08a5)
Now we will navigate to the start menu and search for Active Directory Users and Computers and Click. 

----------------------------------------------------------------------------------------------

![Screenshot (81)](https://github.com/user-attachments/assets/91d39405-c9a6-49c3-844f-68168c9e59c1)
A window will pop-up. This is where we can create an Admin User to control the Active Directory Server. 

-----------------------------------------------------------------------------------------------

![Screenshot (82)](https://github.com/user-attachments/assets/e131b5f8-b872-4af8-b222-72c8ebf36604)
We will right click on the domain in my case githubdomain.com. We will then navigate to new and select organizational unit. An organizational unit is very simply put like a folder in active directory. 

-----------------------------------------------------------------------------------------------

![Screenshot (83)](https://github.com/user-attachments/assets/aec22767-650d-4479-9d03-d4c865f051da)
We will name this Organizational Unit _ADMINS and click okay.

-----------------------------------------------------------------------------------------------

![Screenshot (84)](https://github.com/user-attachments/assets/3f906513-9c1e-483b-b762-278fd4b7b8d3)
We will now right click our new Organizational unit _ADMINS hover over New and select User


-----------------------------------------------------------------------------------------------

![Screenshot (85)](https://github.com/user-attachments/assets/ddfac67c-74ac-4c4a-8b07-c6439276624d)
Now we will fill out our information to create the new Admin account. For user logon name I used a-kkamal where (a) represents admin and then kkamal my first initial and last name. But you can name it whatever you like. Click Next

-----------------------------------------------------------------------------------------------

![Screenshot (86)](https://github.com/user-attachments/assets/fdeb4801-917c-48bb-a6d2-686d5c122323)
Here we can input our password and confirm it then Click Next. I also choose to uncheck the change password at next logon and check password never expires simply because its a lab environment it would not be advisable in a real world scenario.

-----------------------------------------------------------------------------------------------

![Screenshot (87)](https://github.com/user-attachments/assets/b87ad274-18ab-42c5-aefc-f2db79a09074)
Click Finish

-----------------------------------------------------------------------------------------------

![Screenshot (88)](https://github.com/user-attachments/assets/3cb693aa-0163-4c24-85a9-d1ca80f44952)
Now if we click on the folder _ADMINS we will see our freshly made account. But just because its in a Organizational Unit named _ADMINS doesnt mean it has administrative privileges for that we'll need to double click on the account.

-----------------------------------------------------------------------------------------------


![Screenshot (89)](https://github.com/user-attachments/assets/e0b63df7-b9ff-4548-a8f2-e6bc628fd2f7)
Lets navigate to the tab Members of and once on that tab click Add. We are going to add our new account to the Domain Admins Object.

-----------------------------------------------------------------------------------------------

![Screenshot (90)](https://github.com/user-attachments/assets/5f1a4179-f7b7-4142-b92f-24c677779994)
Enter Domain Admins into the textbox and click next. 


-----------------------------------------------------------------------------------------------

![Screenshot (91)](https://github.com/user-attachments/assets/977054c0-6220-4d47-b3af-52b356912038)
As you can see our user is now a member of Domain Admins as well as Domain Users. Click Apply and then OK.

-----------------------------------------------------------------------------------------------

![Screenshot (92)](https://github.com/user-attachments/assets/87e16b26-e61b-453d-bf74-8654c542c9f0)
We're now going to go to the start menu and sign out from our default administrator account.

-----------------------------------------------------------------------------------------------

![Screenshot (93)](https://github.com/user-attachments/assets/7bb0080b-29d2-4bad-ae4f-efc05ec5ca26)
When we end up on the lock screen were going to select other user in the bottom left corner. As you can see under password it says sign into githubdomain. 

-----------------------------------------------------------------------------------------------

![Screenshot (94)](https://github.com/user-attachments/assets/f7dd827e-1fb3-4215-9f23-944a13f847fb)
We will login using our new githubdomain admin account.

-----------------------------------------------------------------------------------------------

![Screenshot (95)](https://github.com/user-attachments/assets/5b773e16-7247-448c-a3c8-93321c1168f4)
After logging in and letting the Server Manager load we're going to click on Add Roles And Features. Click Next

-----------------------------------------------------------------------------------------------

![Screenshot (96)](https://github.com/user-attachments/assets/29e9d7f7-168d-4a8f-b8c4-ddcf8a864fc6)
Click Next until you see

-----------------------------------------------------------------------------------------------

![Screenshot (99)](https://github.com/user-attachments/assets/a631c024-1ca4-4b87-9570-3afaad1d53ff)
Once you hit the server roles page we are going to scroll down ann check Remote Access. We need to enable remote access to be able to have our client computer on a segmented internal network while still allowing the client to access the Internet through the domain controller.

-----------------------------------------------------------------------------------------------

![Screenshot (102)](https://github.com/user-attachments/assets/fa7a7021-00cb-472e-be61-1030737700ad)
We're going to continue to click next until we get to the Role Services tab. Once there check routing and then click Add Features, then click Install.

-----------------------------------------------------------------------------------------------


![Screenshot (104)](https://github.com/user-attachments/assets/6d38df7e-0200-4fd3-8b93-cddbe64a84e4)
As you can see we now have AD(Active Directory) server installed and configured as well as DNS and remote Access.

-----------------------------------------------------------------------------------------------

![Screenshot (105)](https://github.com/user-attachments/assets/dfddbbae-e9e5-4293-b10a-e329d1ee3013)
Now we will click on Tools in the top right corner and click on Routing and Remote Access.

----------------------------------------------------------------------------------------------

![Screenshot (107)](https://github.com/user-attachments/assets/b2f478e7-a844-4d33-be3b-665d4ef9c855)
The Routing and Remote Access window will open up. Right click on DC(Local) and click configure and enable routing with remote access.

-----------------------------------------------------------------------------------------------

![Screenshot (108)](https://github.com/user-attachments/assets/b919c2c5-dba5-4d63-98da-926d8c8d7b7b)
On the next page we are going to select NAT to enable all our clietns to connect to the internet using a single IP address The domain Controllers. Click Next

-----------------------------------------------------------------------------------------------


![Screenshot (111)](https://github.com/user-attachments/assets/78817f1a-f021-4cf1-9723-5a9c3151ecde)
If you read the description of our option it says(Use this public interface to connect to the internet) we would select INTERNET as our public interface to connecct to the internet. Click Next and Click Finish

-----------------------------------------------------------------------------------------------

![Screenshot (113)](https://github.com/user-attachments/assets/ea0178f8-50b3-4c19-ac59-1f5deda87135)
Click OK

-----------------------------------------------------------------------------------------------

![Screenshot (114)](https://github.com/user-attachments/assets/2205b525-c585-4394-881b-bf08ec6e16d0)
Now we will right click the DC(Local) and press refresh. You will notice the arrow that was red before is now green. Indicating we have succesfully installed and configured NAT.

-----------------------------------------------------------------------------------------------

![Screenshot (115)](https://github.com/user-attachments/assets/496a5bff-8ec5-4010-84ec-b1aa8283f69b)
Finally we will install DHCP on our Domain controller to automate the configuration of devices IP joining our Internal network. To do this we will click on Add Roles and Features and Click Next until we ge to the Server Roles Tab.

-----------------------------------------------------------------------------------------------

![Screenshot (117)](https://github.com/user-attachments/assets/a43a8dae-c05d-409d-9339-40308b5e8351)
Check DHCP to install DHCP on our Domain Controller. Click next until the confirmation tab and Click Install. It will take some time but once it is finished click close.

-----------------------------------------------------------------------------------------------

![Screenshot (120)](https://github.com/user-attachments/assets/5325c640-2de4-4710-9d71-c71afe19a9db)
Now we're going to configure DHCP. Click tools in the top right corner and select DHCP.

-----------------------------------------------------------------------------------------------

![Screenshot (122)](https://github.com/user-attachments/assets/08a40590-43d5-4f16-9e6a-0fb2875b5040)
Expanding our dc.githubdomain we see IPV4 and IPV6 we are going to configure the scope on IPV4.

-----------------------------------------------------------------------------------------------

![Screenshot (122)](https://github.com/user-attachments/assets/70ad40f6-7177-477d-ab81-93233440e36e)
To configure the IPV4 scope we will right click it and select New Scope. 

-----------------------------------------------------------------------------------------------

![Screenshot (124)](https://github.com/user-attachments/assets/fa074700-7d80-486c-b510-94540fba29b2)
Here we can name our scope. You can name it whatever you like for example HR or Sales. In this case we are going to name it the same as the IP range we are giving it. 172.16.0.100-200

-----------------------------------------------------------------------------------------------

![Screenshot (125)](https://github.com/user-attachments/assets/4af05fef-e2c6-44ed-8e5a-6631c41e650c)
Now we create our scope, we will set it from 172.16.0.100 - 176.16.0.200. We will select a length of 24. We chose a /24 subnet for our IP scope because it allows for up to 254 usable IP addresses within the range. Subnet Mask will be 255.255.255.0 but shoudl be automatically set when we enter the length. Click Next

-----------------------------------------------------------------------------------------------

![Screenshot (126)](https://github.com/user-attachments/assets/30cb49b2-d668-4324-8f6f-57b23a791dc3)
Click next on the Add Exclusions as we dont need to reserve or block any particular IP address from being used.

-----------------------------------------------------------------------------------------------

![Screenshot (127)](https://github.com/user-attachments/assets/f2fccf0d-996d-4952-99d3-e8e30546db59)
Lease duration is how long a certain IP will be reserved for. For example lets say I connect my phone to a network and the lease time is set for 8 days. Even if my phone is no longer connected to the network that IP cannot be used by another device until the lease expires. In a lab environment 8 days is fine. In a corporate environment you may choose to change it. Click Next

-----------------------------------------------------------------------------------------------

![Screenshot (128)](https://github.com/user-attachments/assets/9ebe0c96-6fbf-4c11-9582-0523676c7393)
Click Next

-----------------------------------------------------------------------------------------------

![Screenshot (129)](https://github.com/user-attachments/assets/3dc02ac8-0342-4e4e-91c4-87695690aa11)
Since we have routing enabled on our Domain Controller we're going to enter our Domain Controllers IP 172.16.0.1 and click Add. Click Next.

-----------------------------------------------------------------------------------------------

![Screenshot (130)](https://github.com/user-attachments/assets/97f1d41a-d27f-4357-8a57-6198e5118f22)
Click Next.

-----------------------------------------------------------------------------------------------

![Screenshot (131)](https://github.com/user-attachments/assets/9a60e208-073b-43e4-b045-a374c92e043c)
We aren't going to use WINS Server so click Next.

-----------------------------------------------------------------------------------------------

![Screenshot (132)](https://github.com/user-attachments/assets/bbe4683f-12d1-43dd-a2f2-02e4cab25c76)
Click Next.

-----------------------------------------------------------------------------------------------

![Screenshot (134)](https://github.com/user-attachments/assets/95df4c4e-b801-4804-a13b-cff99398afc3)
Right click dc.githubdomain and select authorize to apply the changes. Then right click again select refresh. 

-----------------------------------------------------------------------------------------------

![Screenshot (135)](https://github.com/user-attachments/assets/2b6c23da-0692-4ea4-a768-46bc2b832911)
We now have our IPV4 Scope configured as you can see by our green arrows indicating they are up. Now close this window.

-----------------------------------------------------------------------------------------------

![Screenshot (136)](https://github.com/user-attachments/assets/db7640ea-e0c7-46bd-9656-1e48cce9078b)
Now we need to create a new organizational unit called _USERS to add the account information 
of the users on our domain. Go to start and search for Active Directory Users and Computers.

-----------------------------------------------------------------------------------------------


![Screenshot (137)](https://github.com/user-attachments/assets/d2022f8d-af80-41bc-9269-5225ff98b9fb)
We will right click githubdomain.com and hover over New and select Organizational Unit.

-----------------------------------------------------------------------------------------------

![Screenshot (138)](https://github.com/user-attachments/assets/5a03ef67-e1f1-4d79-ac60-a0b21182d1a5)
We will name it _USERS. Click OK.

-----------------------------------------------------------------------------------------------

![Screenshot (139)](https://github.com/user-attachments/assets/eb6b2188-bb84-4779-b5e6-72a62464e8be)
Click on _USERS. Right Click inside of it, hover over New and select User.

-----------------------------------------------------------------------------------------------

![Screenshot (144)](https://github.com/user-attachments/assets/a0fefa3e-94d2-439b-8bac-e6287753c10f)
Enter the information required. I will follow the same naming convention as I did earlier initial of the first name and last name. In this case kkamal. Click Next and enter a password then Click Next and Finish

-----------------------------------------------------------------------------------------------

![Screenshot (147)](https://github.com/user-attachments/assets/e26248ee-88dd-41bf-9cd2-74726762d1cd)
You will see your user appear. I have also made a couple more user accounts to simulate more of a corporate environment.

-----------------------------------------------------------------------------------------------

![Screenshot (148)](https://github.com/user-attachments/assets/cdc2e169-5185-4ef7-8086-402a374660c1)

We are now done configuring our Domain Controller with Active Directory Server, DHCP, DNS, Remote Access and Routing. As well as create an admin and user accounts for Active Directory. 
Congrats (:
