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















