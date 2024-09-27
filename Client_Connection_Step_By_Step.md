
![Screenshot (149)](https://github.com/user-attachments/assets/7d6ecd8a-4166-445c-adf2-ee4fb4c2d372)
Now we will finish the client side of our Network Diagram.

---------------------------------------------------------------------------------------------------

![Screenshot (182)](https://github.com/user-attachments/assets/d5a1eade-b88f-4bf8-aa46-261b8c33fb51)

I have installed Windows 10 Pro for this Lab and it is running on VirtualBox. The Network adapter configuration consists of only an internal network connection and no internet connection from the host machine.

---------------------------------------------------------------------------------------------------

![Screenshot (150)](https://github.com/user-attachments/assets/18743816-199f-4f8a-89c3-42f74d2dfcbf)

Once we have our machine powered on and have created a defualt user, log in and click on the start menu. Click search and enter View Your PC Name and Click. In my case I typed rename because it works the same. 

------------------------------------------------------------------------------------------------

![Screenshot (152)](https://github.com/user-attachments/assets/8f50b3cf-c650-4ced-b36f-9f0650868569)

Click Rename This PC and enter a name. I'm going with CLIENT but you can choose to name it anything. Click Next, and now your computer is going to restart. 

------------------------------------------------------------------------------------------------

![Screenshot (157)](https://github.com/user-attachments/assets/a9383812-7902-4a17-8c52-4bd9f7d84e5e)
Click the start menu and search for cmd, we are going to open a command prompt and type in ipconfig. Press Enter

------------------------------------------------------------------------------------------------

![Screenshot (158)](https://github.com/user-attachments/assets/08df26af-eb89-46f4-8a1c-8a60bac7e618)
Thanks to DHCP on our domain controller we are automatically assigned an IP. Next type in cls and click enter to clear our screen.

------------------------------------------------------------------------------------------------

![Screenshot (159)](https://github.com/user-attachments/assets/8a6d4828-71a0-4a5f-958a-b2cf7561523a)
Type in ping google.com and click Enter. This will see if our Client computer can ping through the domain controller to recieve a reply from Google.com. Meaning DNS works and it has an internet connection. 

------------------------------------------------------------------------------------------------


![Screenshot (160)](https://github.com/user-attachments/assets/c519880d-8bd7-41e0-aac3-b7be4f6875a6)
Reply from Google.com

------------------------------------------------------------------------------------------------

![Screenshot (161)](https://github.com/user-attachments/assets/eb2b84ec-6dcc-4b73-add4-2b4c3e35d690)
You can also ping our Domain Controller with ping 172.16.0.1

------------------------------------------------------------------------------------------------

![Screenshot (162)](https://github.com/user-attachments/assets/ea41a717-8da5-497a-ae52-438352f72d6e)
We recieve a reply. Close Command Prompt.

------------------------------------------------------------------------------------------------

![Screenshot (163)](https://github.com/user-attachments/assets/eaf3c5ac-23b4-4b7c-b4ed-21d836573425)
Now its time to join our domain. Click start and search for View your PC name.

------------------------------------------------------------------------------------------------

![Screenshot (164)](https://github.com/user-attachments/assets/112f1add-bbbc-4255-bd7c-0d5bca591170)
Scroll Down and Click Rename this PC (advanced)

------------------------------------------------------------------------------------------------

![Screenshot (165)](https://github.com/user-attachments/assets/ab05d97f-92a0-4555-9273-a6bae0903711)
Now we will click Change to login to our domain.

------------------------------------------------------------------------------------------------

![Screenshot (166)](https://github.com/user-attachments/assets/adb76163-7de8-4c2d-8a4c-28a9099728d3)
Click Next.

------------------------------------------------------------------------------------------------

![Screenshot (167)](https://github.com/user-attachments/assets/7f15c70f-d8fe-46f1-911b-c34b058acf6e)
Click Next.

------------------------------------------------------------------------------------------------

![Screenshot (168)](https://github.com/user-attachments/assets/ce2e5170-b902-4732-b510-a28c6e518cb8)
Click Next

------------------------------------------------------------------------------------------------

![Screenshot (169)](https://github.com/user-attachments/assets/8d6aa444-034e-47cd-933c-27a32094f35c)
Now enter your computer name, and check Domain under Member Of and enter the name of your domain in my case githubdomain.com.

-----------------------------------------------------------------------------------------------


![Screenshot (170)](https://github.com/user-attachments/assets/4f92ab27-bbf2-41d2-b642-c1553bb5a27c)
Enter your Admin credentials. Click OK.

-----------------------------------------------------------------------------------------------


![Screenshot (171)](https://github.com/user-attachments/assets/c654f510-f0d2-4d35-b7fd-e319005cbbb4)
Click OK.

-----------------------------------------------------------------------------------------------

![Screenshot (172)](https://github.com/user-attachments/assets/ca7b4272-ad70-4983-8b24-578c9045e303)
Click OK and restart.

-----------------------------------------------------------------------------------------------

![Screenshot (175)](https://github.com/user-attachments/assets/5b43dece-a4bd-4c9a-9009-b95ea5a4579c)
Click Other user, as you can see under the password input field we are signing into GITHUBDOMAIN.  Enter a user credentials and Log in. The user Credential will be one we made in the _USERS organizational unit. I will use the one I named after myself and login with kkamal. 

-----------------------------------------------------------------------------------------------

![Screenshot (179)](https://github.com/user-attachments/assets/7ea8f850-b975-4b96-91f0-6a42d9ad2eb7)
To Confirm we have our CLIENT computer connected to our domain lets head back to the domain controller. Head to the Server Managment Dashboard, Click Tools and select DHCP.

-----------------------------------------------------------------------------------------------

![Screenshot (180)](https://github.com/user-attachments/assets/e6966440-2e9e-4007-abaa-f50c502d4748)
Exapnd IPV4, Expand Scope and Click on Address Leases. As you can see we have a connection to CLIENT.githubdomain with the IP address of 172.16.0.1. Meaning the connection is Succesful.
