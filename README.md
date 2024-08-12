<h1>UTILIZING ACTIVE DIRECTORY</h1>


<h2>DESCRIPTION</h2>
Active Directory is a core tool for System Administrators that need to manage Windows machines and it allows to manage users, groups, devices, and the policies that apply to all of them in a centralized fashion.  The examples below add users and groups, edit users memberships as well as create a new group policy object (GPO).
<br />
<br />
<h2>LANGUAGES AND UTILITIES USED</h2>

- <b>PowerShell</b> 
- <b>Active Directory Administrative Center</b>

<h2>ENVIROMENT USED</h2>

- <b>Windows 10</b>

<h2>INSTALLING AND CONFIGURING ACTIVE DIRECTORY:</h2>
First, you will need to install and configure Active Directory.  This is a complicated process, so we have provided PowerShell scripts to automate most of it.  Please follow the following instructions carefully.  After logging in, open Windows Powershell as an Administrator.  You can open Windows Powershell as an Administrator by opening the Start Menu, right-clicking the Windows Powershell icon and selecting More, then Run as Administrator: <br />
<img src="https://i.imgur.com/GBZW5F4.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
This will run for a couple of minutes.  It will print a few warnings, but don't worry, those are expected. When it's done, the script will pop-up a message indicating that it will restart the computer. <br />
<img src="https://i.imgur.com/C9ud0ys.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Active Directory has now been installed, but it still needs to be configured.  This should be simpler than the previous task.  Open Windows Powershell as an Administrator and run the following command to configure Active Directory and continue with the rest of the lab when it finishes:
C:\Qwiklabs\ADSetup\configure_active_directory.ps1 <br />
<img src="https://i.imgur.com/F7Hu53h.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<h2>MANAGING USERS AND GROUPS:</h2>
Once the above setup is done, you are now ready to experiment with Active Directory.  Open the Active Directory Administrative Center (ADAC), you can find it by typing "active" into the Windows start menu: <br />
<img src="https://i.imgur.com/NWiy3jH.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
The Active Directory Administrative Center allows you to manage your Active Directory installation by configuring users, groups, computers, and more: <br />
<img src="https://i.imgur.com/EbynErI.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
For this lab, I created a new user called Alex.  To do that, I selected the example (local) entry.  This is the entry for the domain that your account can manage.  Then I scrolled down and double click on the Users entry to see the list of users and groups that currently exist: <br />
<img src="https://i.imgur.com/9RE4YJ6.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Adding Users:
To create a new user, take a look at the tasks list on the right.  Under the Users section, there's a New menu entry, which opens a submenu to select what's the type of entity that you want to create.  In this case, we want to create a new user, so click on the User option: <br />
<img src="https://i.imgur.com/hmLnzcv.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
This will open a new window that lets you fill in a number of fields related to the new user.  There are a lot of fields available, but only a couple are mandatory (indicated with the red star).  You can leave the rest empty.  The user that we are creating is called Alex, with their username being also alex: <br />
<img src="https://i.imgur.com/I86xrYe.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Once you've entered the necessary data, click the OK button to have the user created.
<br />
If you click on the newly created account, you will see that where it displays the name of the user, the system says Alex (Disabled): <br />
<img src="https://i.imgur.com/FmabayW.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
What happens if you right click on the entry and try to Enable it? <br />
<img src="https://i.imgur.com/s5bdYoW.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
The system will not enable an account that doesn't have a good password.  In this case, the password is empty because we haven't set it.  Obviously, an empty password is not a good password.
<br />
You can set a password using the Reset password menu option: <br />
<img src="https://i.imgur.com/HB7neQ2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Enter the password and confirm password into the Reset Password window, and User must change password at next logon option is already checked, we ensure that the user will change their password when they log in.  So now click on the OK button to set the password.  The goal of this is that after they've logged in once, the system administrator will not know their new password:
<img src="https://i.imgur.com/NZGm4xF.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Once you've set a good password, you can retry enabling the account.  This time it should work.
<br />
<br />
Adding Groups:
Let's now add a new group.  If you browse through the existing groups, you will see that there's a group called Developers and a group called Java Developers.  We now want to add an additional group, called Python Developers.  Add the new group to the Developers group, then add the account we just created for Alex to the Python Developers group.  To create a new group, use the same menu that you used for creating a new user, but this time select the new Group option:
<img src="https://i.imgur.com/e6tJpb0.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
This will open a similar window to the one that we saw before, but this time it requires the data for the Group rather than the user:
<img src="https://i.imgur.com/2VxCdnw.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
We are creating a group called Python Developers and that's the only data that is mandatory.  You can also add additional information in the Description and Notes, if you want.  Once you are done, click OK to have the group created.
<br />
<br />
Adding Entities to Groups: We have a Python Developers group, now we want to add it to the Developers group that already exists.  We can do this by scrolling down to the new entry and then right clicking on the entry in the list and selecting the Add to another group entry:
<img src="https://i.imgur.com/B0GQlo4.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
This will open a small window where we need to enter the name of the group.  In this case, the group is called Developers:
<img src="https://i.imgur.com/bKFyVbH.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
You can use the Check Names button to verify that you have entered the name correctly.  If you have, it will underline the text. If the name is incorrect, it will show a window saying "Name Not Found."
<br />
<br />
Clicking the OK button will add the Python Developers group to the Developers group.  We now want to do the same for adding Alex to Python Developers.  But we'll follow a different path.
<br />
<br />
In this case, we will double click the Python Developers entry in the list, which will open up an editing window for the group:
<img src="https://i.imgur.com/6WNyvu0.png)" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
You can scroll down until you find the Members section of this window, or you can click on the Members link on the left.  This section allows us to manually add or remove members from the group Alex.
<br />
<br />
In this case, what we want to do is to add Alex to the group, so click the Add button, enter Alex in the text field and then OK for the addition and OK for saving the changes:
<img src="https://i.imgur.com/HqpY8YP.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Editing Memberships: Finally, there's an existing user called Alosha that has switched from programming in Java to programming in Python, we want to remove this user from the Java Developers group and add them to the Python Developers group.
<br />
<br />
To do this, look for the user Alosha in the list and double click on the entry.  This will open the properties of the user that you will be able to edit.  There's a lot of configuration to each user, click on the section on the left called Member Of:
<img src="https://i.imgur.com/FJKLGNs.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
We can see that Alosha is a member of the Domain Users group (all users of the domain are members of this group) and of the Java Developers group. You can select the Java Developers entry and click the Remove button to remove that group:
<img src="https://i.imgur.com/oMvRAbL.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Then click on the Add button to add a new membership.
<img src="https://i.imgur.com/7pHkg6l.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
This will pop-up a small window where you need to enter the name of the group that you want to add, in this case Python Developers.  Once you are done, click OK in the Select Groups window and then OK in the editing user window.
<br />
<br />
With that, we've created users and groups and we've added and removed group memberships using Active Directory. Let's now look into how to manage group policies.
<br />
<br />
<h2>MANAGING GROUP POLICIES:</h2>
To manage group policies, we need to use the Group Policy Management application. You can find it by typing group into the Windows start menu:
<img src="https://i.imgur.com/gKoRSyH.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
This application allows you to set policies that will manage the way machines in your domain behave.  You can apply these policies to the whole domain or to separate Organizational Units (OUs).
<br />
<br />
In our case, we want to add a new policy to the Developers OU that already exists in the domain.  To do that, expand the tree until you reach the example.com domain tree and find the Developers OU inside it.
<br />
<br />
To create a new policy, right click on the Developer option and select the first menu entry: Create a GPO in this domain and Link it here:
<img src="https://i.imgur.com/jyvwWPr.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
When you click this option, you will be prompted to set a name for the policy and once you do, the policy will get added to the OU.
<br />
<br />
We want to set a default wallpaper for the machines in the Developers OU, so we will call our policy "New Wallpaper":
<img src="https://i.imgur.com/7yHS8kr.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Once created, we want to edit the policy, to do this, right-click on the entry and click on the first menu entry:
<img src="https://i.imgur.com/uMZxX4P.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Note: You may get a warning message about what linking policies means.  That's ok, you can just accept the warning and move on.
<br />
<br />
This will open a new application: the Group Policy Management Editor.  This application allows you to navigate and configure all settings that can be set in a group policy.  As we want to set the wallpaper, we need to navigate to this setting by going to:  User Configuration > Policies > Administrative Templates > Desktop > Desktop:
<img src="https://i.imgur.com/hc8wad0.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
This opens a list of possible settings that we can configure, including the Desktop Wallpaper.  To set the wallpaper to a specific value, double-click on the Desktop Wallpaper entry.
<br />
<br />
The window that opens allows you to set the value of the wallpaper.  To do that, first click on the Enabled button and then enter a path for the wallpaper.  The path could be a local path in the machine or a network path on a server that shares files.
<br />
<br />
For this lab, simply enter C:\Qwiklabs\wallpaper.jpg in the section Wallpaper Name:
<img src="https://i.imgur.com/u1l0dcU.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Once you click OK, the group policy is created and contains the values we want.  To verify this, go back to the Group Policy Management application and click the Settings tab of the new policy.
<br />
<br />
Note: This may show a warning that the application needs to be allowed to generate web content. You will need to Add the application as a trusted website in order to view its contents.
<img src="https://i.imgur.com/T8e50XU.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
By clicking the show links in the webpage, you can see that the policy has been defined and that the only setting being modified is the Desktop Wallpaper, which is set to the value we set above.
</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
