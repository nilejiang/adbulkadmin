adbulkadmin
===========

ADBulkAdmin is a free tool for AD administrators to manage Active Directory users in bulk. You can use it to check a large number of users’ attributes, get users from OU, get members from Group, get all disabled users, get all locked out users, get users password expiration days, create a large number of AD users with specific attributes, unlock a large number of  users, reset a large number of  users’ passwords, enable or disable a large number of users, remove a large number of users, set a large number of users’ properties, check a large number of  groups, add a large number of  users to group or remove a large number of users from group, test users if using easy password, get user lock status on all the domain controllers.

https://youtu.be/3SJ8tjgEFaY

Prerequisite:

1. .net Framework 4.0 or higher.
2. Office 2007 or higher. Run ADBulkAdmin.exe in 32 or 64 bit Office folder according to your office version. With Office Excel, you can create a large number of users or set properties for users. If you are using Office 2016 and you can’t operate Excel, please download and install Microsoft Access Database Engine 2010 Redistributable from http://www.microsoft.com/en-US/download/details.aspx?id=13255  or Microsoft Access 2013 Runtime https://www.microsoft.com/en-us/download/details.aspx?id=39358
3. Files of the tool: ADBulkAdmin.exe, ADBulkAdmin.exe.config, users.xlsx, ADBATData.accdb. (You must not change the name of these files!)
4. User with necessary AD permissions, and run this tool as administrator.

Description:

Unzip the compressed file, make sure the tool ADBulkAdmin.exe, users.xlsx and ADBulkAdmin.exe.config are in the same folder. You can save ADBATData.accdb in the same folder or in a shared path with others. Run ADBulkAdmin.exe as administrator according to your Office version 32bit or 64bit. If your computer has already joined to domain or you run the tool on a domain controller, it can connect to a domain controller automatically, and then you can use it directly. If your computer has not joined to domain yet, you can connect to a domain controller by clicking “Settings”. You can specify the logpath, dcpath, select the attributes you want to check user, create new user or set user.

1. Check User: You can input samAccountName, userPrincipalName, mail or displayName to search user. If you select All, it will search all of these attributes and display all results match the value. You also can search via selecting one attribute. Each row with one user, and then you can get the users’ common attributes by clicking Run. I think you must know the common attributes of an AD user.

2. Get Users: Get users from OU, get members from Group, get all disabled users, get all locked out users, get password expiration days users.

3. New User: First select the attributes in Settings->NewUserAttr, then click Save to save the selected attributes to newuser sheet in users.xlsx. If you want to create new user to your specified OU path, you need to check OU in Settings-NewUserAttr and input the ou path like “ou=deptou,dc=domain,dc=com” to newuser sheet in users.xlsx, if not you must create an OU named “tempuserou” to store new users.Please input the users’ information into Sheet “newuser” in users.xlsx, if you don’t want to set the attributes, just leave the data cell blank. You must input the users’ samAccountNames, and then you can choose to input the other attribute values as your necessary. If you don’t set the Password value, the tool will use “abcD.1234″ as the default password, so you must think if it matches your password policy and you can customize a new password to meet your password policy by inputting the Password data.

For one important thing, if your computer doesn’t join to domain, or you don’t want the user’s UPN to use the default domain name, you must select UNP option in Settings->NewUserAttr and input the UPN value in the Sheet newuser. Then input the user’s User Principle Name like abc@abc.com , the the UPN will be  abc@abc.com .

For proxyAddresses attribute, if you have selected to input this value in Setting->NewUserAttr, you have to split the multiple values with ‘^’ , like:

SMTP:niletest@abc.com^smtp:niletest@nile.com

Or

SMTP:niletest@abc.com

If you are using Exchange on-premises, this value should be generated automatically after you enable user’s mailbox, no necessary to input.

For the new user, its Name is the same to the Display Name, you can decide if user must change password at next logon by clicking “Settings->NewUserAttr->Force Password Change at Next Logon”.

For Manager, you need to input the manager’s samAccountName like nilejiang.

For HomeDrive, you just need to input the value like Z:

4. Unlock User: You can unlock users which are locked, just input the users’ samaccountnames in the textbox and click Run, it will unlock all the users. You can check if the users are locked by Check User feature, if the user is locked, its status will be locked and its color will be red.

5. Reset Password: You can reset a large number of users’ passwords to the same password by inputting the “Custom Pwd”, if not, the password will be reset to “abcD.1234″, and you can choose if user must change password at next logon.

6. Disable/Enable User: You can disable or enable a large number of users by Xable User feature, just input the user’s samAccountNames and choose “Disable User” or “Enable User”.

7. Remove User: You can remove users from AD by Remove User feature after you input the users’ samAccountNames.

8. Set Properties: Please select the attributes in Settings->SetUserAttr first, then click Save to save the selected attributes to setprop sheet in users.xlsx. You can input the attribute values of the user as necessary, if you don’t want to set the attributes, just leave the data cell blank, if you want to clear the attribute value, just input the word “clear” to the cell. The clear function is not used for “NewPassword”, “AccountExpires” and “NewOU”.

If you choose the attribute proxyAddresses, you have to split the multiple address values with ‘^’ , like:

SMTP:niletest@abc.com^smtp:niletest@nile.com

Or

SMTP:niletest@abc.com

If you are using Exchange on-premises, this value should be generated automatically after you enable user’s mailbox, no necessary to input.

9. Check Group: You can check the group common attributes with Check Group feature, just input the group’s samAccountName.

10. Add to Group: You can add a large number of users to a group by this feature. First input the users’ samAccountNames, then input the group’s samAccountName on the right side. You will get the result after clicking the button Run.

11. Remove from Group: It is the same to Add to Group. You can use it to remove a large number of users from a group.

12. Log View: Every operation you did with ADBulkAdmin will generate logs into the database file ADBATData.accdb. You can use Log View to check all the operations you did, and you can search logs by changing the search conditions.

13. Test Password: This is used for administrators to see if users are using too easy passwords, this feature is locked by default, if you need it please send email to me, maybe you need to pay a little.

14. Lockout&LastLogon: This is used to search user lockout status on all domain controllers, get user locked out time and so on.

15. Export to CSV: You can export any data in the datagridview to a CSV file.

We know that there are many attributes for an AD user, I just use the common attributes. If you want to customize some attributes according to your environment, please feel free to contact me. If you think this tool is helpful for you, please donate a little by clicking Donate. That would be a big encouragement.

There is a detailed manual in the compressed file. If you find any bugs or meet any problems, please send email to me.

If you want to customize features, please send email to me at nilejiang#gmail.com.

Update History:

2013.1.23 v1.0.0.1

Add Lync and DN attribute in Check User feature to check if the user is enabled Lync and get the user’s OU path via DN.

2013.3.11 v1.0.0.2

Add account expires time attribute etc. and fix some small bugs.

2013.3.11 v1.0.0.3

Add telephoneNumber, mobile and description etc. to create new users and fix some small bugs.

2013.3.11 v1.0.0.4

Add password and mail attributes to create new users and set users.

2014.2.8 V1.0.0.5

Add new feature of specifying domain controller.

2014.2.16 V1.1.0.0

Enhance dc specify feature. Generate two versions for bothe 32bit office and 64bit office, fix some small bugs and exceptions.

2014.5.15 V1.1.0.1

Fix the bug of wrong result when adding to group or removing from group, add some new user attributes.

2014.8.26 V1.1.0.2

Select “User must change password at next logon” when creating new users and reseting user pasword.

2014.9.17 V1.1.0.3

Add the feature of recording and searching logs to Access database.

2014.11.4 V1.1.0.4

Add the feature that user can select attributes when checking users, creating new users and setting users, fix some small bugs.

2015.4.29 V1.1.0.5

Add Unlock User function and fix some small bugs, like reset name attribute when change Display Name, create user successfully when name includes “,” etc..

2015.5.1 V1.1.0.6

Add all the common AD user attributes to the tool when checking, creating and modifying users, can specify ou path when creating new users, fix some small bugs.

2015.8.12 V1.1.0.7

Add attributes employeeNumber and proxyAddresses for check users, create new users and set properties according to user’s requirement.

2015.8.17 V1.1.0.8

Add Check Update featue in About. It can check if there is a new version and can download the latest version.

2015.9.30 V1.1.0.9

Add some new attributes like ProfilePath, HomeDrive and HomeDirectory and so on. Add detail logs when operating. Fix some small bugs and make some optimizations like use samAccountName as cn when not input the DisplayName attribute.

2015.12.03 V1.1.0.10

Fix the bug that can’t open at the second time if your computer doesn’t join domain and you have specified a domain controller and save the settings. It works OK now.

2016.1.21 V1.1.0.11

Fix some small bugs, add Export to CSV feature, add Get Users Feature that get users from OU, get members from Group, get all disabled users, get all locked out users, get password expiration days users. Add Test Password feature, add search user Lockout and Lastlogon status on all domain controllers. Test Password and Lockout&LastLogon feature are locked by default, if you need it please send email to me, maybe you need to pay a little to unlock it.

2016.1.21 V1.1.0.12

Fixed Test Password bug, add whencreated and LogOnTo(userworkstations) attributes, add PasswordExpireDays to Lockou&LastLogon feature. Test Password and Lockout&LastLogon feature are locked by default, if you need it please send email to me, maybe you need to pay a little to unlock it.

2016.4.30 V1.1.0.13

Fixed the bug of profiepath when including %username% in the value. Add Logon Script attribute and Password Never Expires to NewUser and Set Properties feature. Add Password Never Expires to Reset Password feature.

2016.7.16 V1.1.0.14

Fixed a small bug that can not select all via Ctrl + A on Add to Group etc. Unlock Lockout&LastLogon for free.

2016.7.23 V1.1.0.15

Fixed the bug when create New User or Set Properties to the OU path which contains special character like “/”,  also for Check User feature.

2016.12.10 V1.1.0.16

Fixed a small bug, changed the Settings desgin, can add or remove the attributes to the list and sort the attributes, so that can check, create or set user attributes more easily.

2017.10.29-v1.1.0.18

Optimize the source code, add UPN to Set Properties, change ProxyAddresses to split with “;”, add value without overwriting existed values.

2017.12.16-v1.1.0.19

Change About to check update automatically aftering opening and show if it is the latest version.
Can add new user to multiple existed groups split with semicolon ; when creating new users.
Can add multiple users to multiple groups split with semicolon ; with Add to Group feature.
Can remove multiple users from multiple groups split with semicolon ; with Remove from Group feature.
Add Report feature that can generate operation report for all users or one user.

2018.1.14 V1.1.0.20

Change ProxyAddresses to split with “^” for Check User, New User and Set Properties features according user’s requirements, add switch for appending or replacing ProxyAddresses values in Settings->SetUserAttrList.

2018.5.6 V1.1.0.21

Fixed a bug that can’t delete user contains child object.

Added samAccoutName length check when creating new users.

2018.6.18 V1.1.0.22

Added the new feature that get group list user belong to and export to csv.

2018.8.19 V1.1.0.23

Added new attribute otherTelephone and optimize some code.

2018.11.25 V1.1.0.24

Added new attributes division and info, fixed a small bug when saving logs containing “‘” in attributes.

2019.2.8 V1.1.0.25

Added get groups, contacts and computers from OU, get inactive days computers.

2019.3.3 V1.1.0.26

Added extersionAttribute14, added Scripts samples, please contact Nile to get.

2019.5.12 V1.1.0.28

Added Name(cn) attribute in New User and Set Properties, can set Name separately. if not set in New User, it will be the same to Display Name, if not set Display Name, it will be samAccontName. Changed UPN input type to full value like abc@abc.com , added new feature User Last Logon Report, can get user last logon report from specified DC.

2019.5.19 V1.1.0.29

Added display user disabled status in User Last Logon Report, added determine if has existed UPN when creating new users.

2019.6.2 V1.1.0.30

Added middle name according to user’s request.

2019.6.29 V1.1.0.31

Fixed the bug that get error when creating new user if selected UPN but not set value.

2019.7.06 V1.1.0.32

Fixed some small bugs if contains special characters in user or OU name, doesn’t load all groups by default.

2019.7.28 V1.1.0.33

Adjusted a label layout, fixed a small bug.
