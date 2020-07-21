---
title: "Work Notes"
date: 2020-07-21 07:13:00 -0500
categories: [hacking, tinkering, making ]
tags: [R2R, repair, legislation ]
---

Customer Requested Delay - to identify those incidents that will breach SLA due to customer request to delay us working on an incident until they are available. For example:
· Wah’s coming in office “next” week
· Users wanting to schedule a time to work on the problem after ticket will breach SLA
· Training room/desks not available to set up equipment
· Aetna ID’s not available
· New hire date past SLA breach
If the ticket is tagged, work notes MUST include email or IM copied into the incident that it is at the customer’s request.
L3-Aetna - to identify INC tickets in your queue that are waiting for an Aetna Level 3 Team (e.g. Dev Tools, application owner) to get back to you with a solution
SLA Breach Risk - Received Ticket with less than 2 hours until SLA breach or SLA already breached.
Three strike - After three contacts/strikes the ticket should be resolved and tagged with the “three strike” tag
Vendor Delay – Hardware on backorder, Kelser delay in shipping to site. Required to put Kelser ETA shipping info.
Rebuild/Reimage - When a rebuild request is required or user’s device reimaged.
Desktop Regional Admin Only Use
Chronic Issue - Used only by Regional Admin Group - – issue is chronic and needs at least a few days of monitoring. Account Lockouts, Application crashes, ETC. When L3-Aetna would not apply.
Tape Request - Tape requests. For some backups the RA’s need to request tapes for offsite. Depending on where in the process, the tapes can take a few days for retrieval.



http://netinfo.aetna.com/sitelist/site-details.asp?sitecode=ABN

http://wvmpcsaeis01.aeth.aetna.com/StatusViewer/

Single workstation by Last Logon User - Report Manager

wksAudit Reports - Report Manager

http://aetna.skccom.com/aetnaucdevices/welcome.asp

https://www.thewindowsclub.com/windows-10-sync-center

https://teams.sp16.aetna.com/sites/DentalEmployees/ToolsRef/default.aspx

 
Continue to use SIM here: --- until it goes to QA/PROD
\\wvmpswmap01\irtest\Products\SIM
 
There is an updated CAT to use this version:
\\wvmpswmap01\irtest\Products\CAT

\\wvmpswmap01\irtest

Eclipse Error 13

C:\ProgramData\Oracle\Java\javapath
is added to the Path environment variable, causing Eclipse to run using the wrong java version.
To fix the problem:
1) Right-click on Computer and choose Properties.
2) Click Advanced system settings
3) Click Environment Variables...
4) Find the Path variable in the System variables section.
5) Choose it and click Edit...
6) Find and delete the above mentioned path.
This fixed it for me. I should mention that I already have the path:
c:\Program Files\Java\jdk\bin

From <https://stackoverflow.com/questions/27019786/eclipse-java-was-started-but-returned-error-code-13> 
-vm 
c:/wherever/java/jdk1.6.0_21/jre/bin/server/jvm.dll
-vmargs... 

From <https://stackoverflow.com/questions/18609160/eclipse-returns-error-message-java-was-started-but-returned-exit-code-1> 

\\wvmpswmap01\irtest\products\Acrobat_Serialize_Fix - go into the specific subdirectory for your product (“Standard” or “Professional”).  Right-click the .bat file and “Run as administrator 

SCCM Remote Tools - https://teams.sp.aetna.com/sites/SoftwareDelivery/SCCM%20Engineering/Home.aspx

On premise mailbox "glitchy fix"

1. Type “regedit” and click “OK“.
2. Click the plus sign next to HKEY_CURRENT_USER, then navigate to the following:
	? Software
	? Microsoft
	? Office
	? 15.0
	? Outlook
	? OST
3. Right-click the “NoOST” entry on the right and click “Modify“.
4. Give it a value of “0“.
Note: Some users report that they assign this value to “3” instead of “0”.

From <https://www.technipages.com/outlook-use-cached-exchange-mode-grayed-out> 

To build AetnaUSB boot media on a Windows 10 machine, the device needs to be added to a specific OU in ADHelp Workstation Management. If you look up a given device in ADHelp, at the top you should see the list of different OUs near the top of the entry and can select “Workstations/Windows10/StandardWks/BTG-Unencrypted” and click Move. It’ll take a bit of time (and maybe a policy update/reboot) for the change to propagate, but after that you should be able to log in as ZZid to that machine, go to \\wseng\buildfiles\ and use the aetnausb.exe in either AetnaUSB (for Win7 sticks) or AetnaUSB – Win10 Only (for Win10 sticks) to image your boot media. 

If a task sequence says Installing in Software Center but isn’t actually installing (as confirmed by checking the smsts.log file), you can use the steps below to resolve the issue…
 
·         From a command prompt, type WBEMTEST and then hit Enter
·         Click the Connect button, type root\ccm\SoftMgmtAgent in the Namespace field and then click the Connect button again
·         Click the Enum Classes button, click Recursive and then click the OK button
·         Double click CCM_TSExecutionRequest then click the Instances button
·         Highlight the running instance and then click the Delete button
·         Click the Close button three times to close all open windows
·         Click the Exit button to close WBEMTEST
·         Restart the CCMEXEC service
 
After taking those actions, the task sequence should change status in Software Center at which point you can run it again (it will likely change to Failed but may change to Available).  Please give that a try and let me know if you encounter any issues or have any questions.  Thanks.
 


Dism /Online /Cleanup-Image /CheckHealth
Dism /Online /Cleanup-Image /RestoreHealth

From <https://www.tenforums.com/tutorials/7808-use-dism-repair-windows-10-image.html> 

PC will not wake from hibernation

Go to:
Device Manager
Expand Universal Serial Bus Controllers
Right click USB Root Hub (xHCI)
Click on Properties
Click on Power Management
Untick 'Allow the computer to turn off this device to save power'

From <https://answers.microsoft.com/en-us/windows/forum/all/my-computer-wont-wake-up-from-hibernation-in/59046caf-6774-4086-8408-2ff7fa13a134> 


\\wseng\Updates\Add-XPSViewer-Win10-1809\XPS-Viewer1809.cmd

Please have the techs send them to the address to below and include the TASK # in the Ref. 2 field on the label. 

 
Let us know if you have any questions.
 


How to Delete the SIP Profile
1. Close Skype for Business (SfB) or Lync completely by right-clicking the SfB / Lync icon in the Windows System Tray and selecting Exit.
2. Open Windows Explorer and navigate to the folder that corresponds to the SfB / Lync client version that is installed
• Lync 2010: %UserProfile%\AppData\Local\Microsoft\Communicator
• Lync 2013: %UserProfile%\AppData\Local\Microsoft\Office\15.0\Lync
• Skype for Business: %UserProfile%\AppData\Local\Microsoft\Office\16.0\Lync
1. Delete the sip_username directory that matches the sip address of the user experiencing the issues.  This directory will be rebuilt when the SfB / Lync client is restarted the next time.
2. Restart the computer
3. Restart the Lync client

From <https://www.msdigest.net/2016/01/delete-the-skype-for-business-lync-sip-profile/> 


"Are you having problems printing from Outlook? Try deleting the OutlPrnt file – it's kept in C:\Users\%username%\AppData\Roaming\Microsoft\Outlook in Windows 7 and newer.  This file holds information about print configurations and customizations."
Steps:
1.  Open a new Windows Explorer window.
2.  Type or paste this into the address bar:   %appdata%\Microsoft\outlook 
3.  Press ENTER
4.  Find the file named OutlPrnt and delete it.
5.  Restart Outlook.

From <https://answers.microsoft.com/en-us/msoffice/forum/all/outlook-2019-print-preview-is-not-availble/8659156a-ad4c-4ae9-8b36-4815432da00c?page=2> 


Uninstall the SCCM client:
Sign in with your ZZ ID.  Run the following command:
C:\Windows\ccmsetup\ccmsetup.exe /uninstall
Wait several minutes for the process to complete.  
If you open taskmgr you can see ccmsetup.exe running, when it is no longer running in Task Manager you can proceed.
_________________________________________________________________________________
Rebuild WMI:
Sign is with your ZZ ID. Run the following command:
\\WVMP-DSS-001\_Tools\WMIRebuild\WMI_Win7.cmd
After completion you will get message to hit any key to continue.
_________________________________________________________________________________
Reinstall the SCCM client:
Run the following command:
\\MIDPSCCMDBCAS\SMSClient\ccmsetup.exe /skipprereq:silverlight.exe SMSSITECODE=AUTO
 
Wait 20 minutes after you see ccmsetup.exe is no longer running in taskmgr. You should now see ccmexec.exerun running.

netsh int ip reset c:\resetlog.txt  

Avaya not connecting

Open a PDF file
Using Word , you can now open and edit a PDF file. You'll do so as you would any other file. To open a PDF file using Word , do the following:
1. Click the File menu and choose Open from the left pane. Or, click the Open icon on the Quick Access Toolbar (QAT) if you've added it (click the QAT toolbar drop-down and check Open to add it).
2. At this point, you can use Recent Documents or your system's folder structure to find the PDF you want to open. Word will display PDF files in its lists, so you won't have to specify the PDF format to see those files (Figure B).
Figure B
3. Select the file and click Open.
4. When Word displays the informational dialog (Figure C), click OK.
Figure C
5. If Word displays the Protected View bar at the top of the document, click Enable Editing.
6. Figure D shows the results of opening a previously blank PDF file and adding a bit of text. If you open this file using Adobe Reader (Adobe's free viewer), you can't edit the file. To edit the file, you'd need Adobe Acrobat, which is a pricey piece of software.
Figure D
Using Word , you can open and edit the file as you would any other Word file (sort of). As I mentioned earlier, not every format and feature will transfer perfectly, so you'll want to check the document carefully before saving your changes. I offer more specific advice below, but your own experiences will serve your best.

·         Launch Administrative powershell window  
		·         Type the following:  
			·         \\wseng\Updates\Pending\Fix-PhotosApp\Fix-PhotosApp.ps1  



1. Copy contents of \\wseng\HARDWARE\Pending\1909\DELL\5400 to C:\Temp (This is approx 6 GB, so better to do this before contacting the end user if possible)
2. Open a CMD prompt as an Administrator and issue the command PNPUTIL /add-driver C:\Temp\Drivers\*.inf /subdirs /install
3. Suspend Bitlocker
4. Run C:\Temp\BIOS\Latitude5400.exe to update the BIOS 
Choose the option to restart the system at the end of the BIOS Update

\\wseng\PERIPHERAL

1) Cleaned Teams cache as instructed by Microsoft

Fully exit the Microsoft Teams desktop client. To do this, either right click Teams from the Icon Tray and select ‘Quit’, or run Task Manager and fully kill the process.  
• Go to File Explorer, and type in %appdata%\Microsoft\teams.  
• Once in the directory, you’ll see a few of the following folders:  
• From within ‘Application Cache’, go to Cache and delete any of the files in the Cache location.  
• %appdata%\Microsoft\teams\application cache\cache  
• From within ‘Blob_storage’, delete any files that are located in here if any.
• %appdata%\Microsoft\teams\blob_storage  
• From within ‘Cache’, delete all files.
• %appdata%\Microsoft\teams\Cache  
• From within ‘databases’, delete all files.
• %appdata%\Microsoft\teams\databases  
• From within ‘GPUCache’, delete all files.
• %appdata%\Microsoft\teams\GPUcache  
• From within ‘IndexedDB’, delete the .db file.
• %appdata%\Microsoft\teams\IndexedDB  
• From within ‘Local Storage’, delete all files.
• %appdata%\Microsoft\teams\Local Storage  
• Lastly, from within ‘tmp’, delete any file.
• %appdata%\Microsoft\teams\tmp  

From <https://answers.microsoft.com/en-us/msoffice/forum/all/microsoft-teams-status-is-stuck-on-out-of-office/4382c885-f2bb-4987-a739-9f519c3ddc7c?page=5> 


Delete the folder <C:\Program Files\3mhis> then delete any 3M folders in C:\Windows\CCMCache After they are deleted you can install from Software Manager in RTS and it will download and install




Yes for my user the whole thing was that the install worked for the PDS install but any time she would open the case and then click on the button to open a file it would close the app.  And uninstalling and reinstalling office didn’t work and profile rebuild didn’t work.  So I had to 
 
Uninstall office, run all those scrubbers then wipe the profile, then reinstall office 2016, reboot and install the Semi-Annual Channel, reboot and then the user could login and it works.
 
Here are two more tickets that Guy Hempel worked on that had slightly diff issues but this procedure fixed.
INC5783804 & INC5788483

The fix is to uninstall Office but there are a few extra steps.
	1. Uninstall Office from Control Panel
	2. Uninstall from Software Manager if there.
	3. Then run the Office Scrubbers. They get downloaded into C:\Windows\CCMCache. But are not always there unless Office has recently been installed. If they are not there I have a copy of them on my VM (WDAAS6302-A2407) in the C:\ZCO\OfficeScrub folder. Copy these to the local device and run each one top to bottom.
	4. After the scrubbers have been run delete the Microsoft Office folders in C:\Program Files and C:\Program Files (86)
	5. Install the version of Office needed from SIM and reboot computer.

 https://appstore.aetna.com/Product/Details/74872

Access database engine
Clearing Skype for Business Cache in Windows
	1. Log out of Skype for Business
	2. Delete any sign-in information
	3. Exit Skype for Business
	4. Navigate to Users > [Your Username] > AppData > Local > Microsoft > Office > 15.0 > Lync
	5. Delete the sip_profileName folder
	6. Delete all files in Tracing folder.  Do not delete the folder itself
	7. Navigate to Users > [Your Username] > AppData > Local > Microsoft > Office > 16.0 > Lync
	8. Delete the sip_profileName folder
	9. Delete all files in Tracing folder.  Do not delete the folder itself
Open the command prompt and run ipconfig /flushdns


if that headset is an Evolve 60 it should work with skype and Avaya one-X.  If it's not, you can give Jabra tech support a call at 800-327-2230


plantronics support:  800-544-4660 opt 2 then opt 1

DisplayPort to DisplayPort Multi-Monitor Splitter - 2-Port MST Hub
Use this adapter to connect two independent displays to a single DP 1.2 port
Product ID: MSTDP122DP

Dell 5480 Laptop Travel – Dell 65 Watt
Docking Station – 130 Watt


Option 2: Disable alert for multiple accounts
When you have multiple accounts configured and want to disable alerts for multiple accounts, then you need to create the following rule:
1. Open the Rules and Alerts dialog:
	§ Outlook 2003 and Outlook 2007
Tools-> Rules and Alerts… (press OK if you get an HTTP warning)
	§ Outlook 2010, Outlook 2013 and Outlook 2016
File->  button: Manage Rules & Alerts
2. When you see the “Apply changes to this folder” drop down list at the top, make sure that the account for which you want to see alerts is selected here.

3. Button New Rule…
4. Select “Start from a blank rule” and verify that “Check messages when they arrive” or “Apply rule on message I receive” is selected.
5. Press Next to go to the Conditions screen.
6. Select:  through the specified account
7. At the bottom, click on “specified” and then select the account for which you want to see the alert.
You can only select one account here but if you want to see the alert for multiple accounts, don’t worry, we’ll get to that later.
8. Press Next.
9. Select the action “display a Desktop Alert”.
10. Press Finish to complete the rule.
The entire rule will now read as follows:

Windows Vista – Windows 10
C:\Users\username\AppData\Local\Google\Chrome\User Data\Default
1. Within the Default folder should be another folder called Extensions. If you click that, you should see a folder for each Chrome extensions. As you can see from the screen snap below, the folder names are cryptic.



Method 1:

I would suggest you to un-plug all external devices, except the keyboard and mouse, then try to boot the computer.

Method 2:

I would suggest you to try performing Startup Repair using Windows 8 installation media from Windows Recovery Environment (WinRE) and check.

To perform Startup repair on your computer, follow these steps:

a. Insert the media such as (USB or DVD) and restart your computer.

b. Press F12 key (typically this is F12, but it can differ between computer manufacturers) and choose the drive that you inserted the installation media into.

c. Once the Windows Setup window appears, follow these steps:

d. Click next and select Repair your computer.

e. You will then see a blue screen and an option to choose. Choose the option Troubleshoot and select advanced options.

f. You may choose StartupRepair from Advanced boot option.

g. Follow the on-screen instructions to complete the Startup Repair.

Method 3: If automatic repair fails, you may try to repair them using these commands through Command Prompt under Advanced Options. Follow the steps:

a. After you boot your computer using Windows 8 installation media, a black screen appears with gray text Press any key to boot from CD or DVD. Press any key.
b) Select the correct time and Keyboard type. 
c) Click Repair your computer in the lower left corner.
d) Select Troubleshoot from Choose an option screen.
e) Click Advanced options in Troubleshoot screen.

f) Click on command Prompt.

g) Type these following commands and hit enter after each line of command:

Bootrec /fixmbr

Bootrec /fixboot

Bootrec /scanos

Bootrec /rebuildbcd

Restart the computer and check the issue.

Use this article to attach as solution to Incidents for both PC Hardware Lockups/Freezing and Blue Screens as appropriate:
NOTE: This solution should NOT be used for:
	• Application lockups/freezing.  Search for appropriate application article instead.
	• VMs or for Virtual. Search for appropriate Virtualization article instead.
 
PC Hardware Lockups/Freezing: 
	1. If issue resolved with a hard boot or other troubleshooting steps, simply use this article as solution to attach to incident
	2. If not resolved, search for an article related to the PC model, i.e., HP 705, Tiny, Lenovo 715, HP 640, Lenovo T450, Dell 5470, etc.  If article found, it may address specific lockup or boot failures.
	3. Follow normal troubleshooting procedures.
 
Blue Screens:  If a customer calls in with Blue Screen of Death (BSOD):
	• Capture the full Stop code in the ticket, include at what point the BSOD occurred, at bootup or in Windows. If the BSOD occurred within Windows, also include the program the customer was working in at the time of the blue screen.
	• If the customer hasn't already rebooted the machine, have them reboot to see if the problem clears.
		? If the problem clears with a reboot and this is the first report of the blue screen, update the ticket with all information above and close the ticket.
		? If the problem clears with a reboot and this blue screen has been reported multiple times, update the ticket with all information above and assign ticket to Desktop Support
		? If the reboot results in another bluescreen, assign ticket to Desktop Support
 
For Desktop Support only:
This document is used as a tool for help identifying blue screens. You should also check the event viewer on the machines to make sure there are no obvious signs such as bad blocks.
Error Msg: 0x000000F4 - CRITICAL_OBJECT_TERMINATION
Resolution: Bad system board/CPU, Try a Shell Swap
 
Error Msg: 0x0000007E - SYSTEM_THREAD_EXCEPTION_NOT_HANDLED
Resolution: unknown/Bad system board/CPU ?
 
Error Msg: 0x00000024 - NTFS_FILE_SYSTEM
Resolution: File system issue. Decrypt drive, run chkdsk, WSBackup data, replace drive.
 
Error Msg: 0x000000ED - UNMOUNTABLE_BOOT_VOLUME
Resolution: Bad harddrive, Corrupt File system. Decrypt drive, WSBackup data, replace drive.
 
Error Msg: 0x00000050 - PAGE_FAULT_IN_NONPAGED_AREA
Resolution: This is usually bad memory.
Notes: Memory can also be in a swap file (Virtual) and possible video memory
 
Error Msg: C0000218 (Registry File Failure)
Resolution: Boot into Recovery Console, run chkdsk /p. Or boot into Windows PE and run chkdsk /f
 
Error Msg: 0x00000077 - KERNEL_STACK_INPAGE_ERROR
Resolution: Bad hard drive, replace hard drive
 
Additional troubleshooting steps can be found here:
 
https://support.microsoft.com/en-us/help/17074/windows-7-resolving-stop-blue-screen-errors

From <https://aetnaprod1.service-now.com/kb_view.do?sysparm_article=KB0012593&sysparm_rank=33&sysparm_tsqueryId=815307c5db8e7b08f0269ae8db96196c

Ensure bios is uptodate and settings set according to Aetna settings.
Run SFC, GPUpdate, log off. 
Log back in reset the virtual memory to 12000
Run IE Dr., reboot. 
Lastly if you have the time run chkdsk with the "R" switch, if time is an issue use the "F" switch-not as effective but may resolve
 

