<p align="center">
<img src="https://github.com/user-attachments/assets/58685463-747e-4cdc-beef-3ec68f99d5fc"/>
</p>


<h1>Network File Sharing and Permissions</h1>
In this lab, I use the VM infrastructure created in the previous Active Directory projects to demonstrate File Sharing and Permissions. Active Directory is used to create Security Groups to configure group permissions. <br />



<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop Connection
- Active Directory
- User Permissions
- Group Permissions 

<h2>Operating Systems Used </h2>

- Windows 10 Pro (21H2)
- Ubuntu Server 20.04

<h2>The Set-Up</h2>

We will utilize the infrastructure from preveious lab...

- Connect/log into DC-1 as your domain admin account (mydomain.com\jane_admin)
- Connect/log into Client-1 as a normal user (mydomain\<someuser>)

  ![image](https://github.com/user-attachments/assets/a466eb44-3b3d-45ce-96a6-2cc471d870c3)

  ![image](https://github.com/user-attachments/assets/69079db9-3de9-464d-afd1-19a91c368838)


<h2>Create Folders and Set Permissions</h2>

- On DC-1, on the C:\drive, create 4 folders: "read-access", "write-access", "no-access,", "accounting"
 
  ![image](https://github.com/user-attachments/assets/ce9492a8-1a1c-4289-987a-295f74541f4e)
  
- Set the following permissions (share the folder)
  - Folder: "read-access", Group: "Domain Users", Permission: "Read"

    ![image](https://github.com/user-attachments/assets/921d134c-84ce-41b9-8b02-2aaf0c552144)

  - Folder: “write-access”,  Group: “Domain Users”, Permissions: “Read/Write”
    
    ![image](https://github.com/user-attachments/assets/ba8cb0b7-2d78-45fd-b280-73c5a4b0d5e6)

  - Folder: “no-access”, Group: “Domain Admins”, “Permissions: “Read/Write”

    ![image](https://github.com/user-attachments/assets/9852ad19-e335-44fd-b9a4-3809479bfe56)

<h2>Attempt to access file shares as a normal user</h2>

- On Client-1, navigate to the shared folder (start, run, \\dc-1)
  
  ![image](https://github.com/user-attachments/assets/18379b33-fb47-4435-bf1f-39633bd9aa1f)

- Try to access the folders and observe.

  ![image](https://github.com/user-attachments/assets/c18025b3-863d-42f3-bd7e-4fdf493697ff)
  ![image](https://github.com/user-attachments/assets/21be3909-6f98-4a5a-be26-fc56c3526da7)

  ![image](https://github.com/user-attachments/assets/e12dc460-ed59-4663-b822-a4ad9359a6d6)

<h2>Create an "ACCOUNTANTS" Security Group, assign permissions, and test access</h2>

- Go back to DC-1, in Active Directory, create a security group called “ACCOUNTANTS” (Make a new Organizational Unit: "_GROUPS")
    
  ![image](https://github.com/user-attachments/assets/a4e4a2d1-5cf2-496d-ab94-8189ea97b5cb)
  ![image](https://github.com/user-attachments/assets/819602df-413b-4261-a8b6-a25962284877)
  ![image](https://github.com/user-attachments/assets/a9e342ae-0694-4ac5-be13-aa534d483a81)

- On the “accounting” folder you created earlier, set the following permissions:
  - Folder: “accounting”, Group: “ACCOUNTANTS”, Permissions: “Read/Write”
  ![image](https://github.com/user-attachments/assets/9aeb5b21-6344-4b08-a9a2-58cd426c33a7)
  ![image](https://github.com/user-attachments/assets/cde8dbd5-3595-4110-88ba-64812390baf2)

- On Client-1, as regular-user, try to access the accountants folder. It should fail.
  ![image](https://github.com/user-attachments/assets/33cff26e-a3e7-4a8f-aeb5-0594d1494f56)

- Log out of Client-1 as  regular-user
- On DC-1, make regular-user(fox-civ) a member of the “ACCOUNTANTS”  Security Group

  ![image](https://github.com/user-attachments/assets/554561f3-c017-4f3a-b628-77b54e8c0d56)

- Sign back into Client-1 as <someuser> and try to access the “accounting” share in \\DC-1\

  ![image](https://github.com/user-attachments/assets/fc3afac5-3c2d-47fa-9289-206f1d06b118)
  ![image](https://github.com/user-attachments/assets/03c0a128-8516-4737-b0eb-6698b84feeca)
  ![image](https://github.com/user-attachments/assets/48f1215e-e774-4cd8-a6e2-78ebf08799e4)






  



  


  
  
