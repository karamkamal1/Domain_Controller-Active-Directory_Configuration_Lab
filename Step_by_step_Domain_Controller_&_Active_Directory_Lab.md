## Diagram
This network diagram outlines the setup for our upcoming lab environment. In this scenario, the client computer is configured to route all internet traffic through the internal network, ultimately passing through the domain controller for internet access. This design utilizes a domain controller (DC) that serves dual purposes: managing domain resources and handling network routing with RAS/NAT functionalities. 
![Screenshot (149)](https://github.com/user-attachments/assets/9d2b9083-431d-4be8-beea-201f24951ea9)


## Steps
![Screenshot (181)](https://github.com/user-attachments/assets/2fc44589-4d67-44a4-9bdb-566a0451330e)
This is our virtual machine or Server running Windows Server 2019

![Screenshot (49)](https://github.com/user-attachments/assets/a27996f7-1303-44e6-9f93-ff032653557b)
After a little time loading you're greeted by a Server Manager Dashboard this is where the majority of work is going to be done. But first we will need to go to the bottom right hand corner and click on the Network widget and click on unidentified network.

![Screenshot (50)](https://github.com/user-attachments/assets/5b453ea0-621d-4215-b467-e32aea9eb47f)
A settings window will pop up for displaying our two networks. I have configured my server virtual machine to have one connection to the internet as well as one connection to the internal net like shown by the diagram. Now click on change adapter options so we can edit our connections.

![Screenshot (51)](https://github.com/user-attachments/assets/28b35f07-0824-4679-8bce-b77cb7cc9087)
Here are our two network connections but how do we know which one is for the internet and which one is for the internal Network. 

![Screenshot (52)](https://github.com/user-attachments/assets/116ffca7-b8ae-4348-b23b-59d34fe4cb2e)
By right clicking on our Ethernet 1 connection and clicking on status we we are able to see the connection properties of the adapter. As you can see it has an IP that was automatically assigned by my home network letting us know this adapter has an internet connection.



