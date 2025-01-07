# _MDMBypassMacOS_

## Steps

1. Shutdown the device
   
2. **Initial Disk Format**
   
	1. Enter Recovery mode - 1st time
	2. Format the disk completely using disk utility
	3. Shutdown the device
    
4. **OS installation**
   
	1. Enter Recovery mode - 2nd time
	2. Install the latest available OS
	3. After the OS has been installed completely, shutdown
	4. If the machine restarts automatically and reaches the Country selection page, force shutdown the device at this stage
    
6. **Performing MDM Bypass**
	1. Enter Recovery mode - 3rd time
    
	2. Open the internet browser
		1. Goto this URL - `https://github.com/LogicRepairs/MDMBypassMacOS`
		2. Copy the following - `curl https://raw.githubusercontent.com/LogicRepairs/MDMBypassMacOS/main/mdm-autobypass.sh -o mdm-autobypass.sh && chmod +x ./mdm-autobypass.sh && ./mdm-autobypass.sh`
		3. Exit out of the browser
     
	3. Open the Utilities Menu - Terminal
		1. Paste the contents from the clipboard
		2. Follow the steps
		3. When done either type `reboot` or shutdown the device
     
4. Let the device reboot and enter the setup
   
5. **New user account creation**
   
	1. Once the boot process is complete you will have a User login that you previously created as a temp user
  	2. Login to temp user
	3. Create a new user account (Make sure it's an Admin user)
	4. Logout from the current/temporary account
	5. Login via the new username
	6. Delete the temporary account
	7. Shutdown
    
6. **Disable CSR Utility**

   
	1. Enter Recovery mode - 4th time
	3. Open the CLI - Terminal
	5. Type to disable SIP: `csrutil disable`
	7. When done either type `reboot` or restart the device
    
7. Login using the newly created username

8.  **Fix - MDM-Profile**
	1. Goto this URL - `https://github.com/LogicRepairs/MDMBypassMacOS`
	2. Copy the following - `curl https://raw.githubusercontent.com/LogicRepairs/MDMBypassMacOS/main/mdm-config.sh -o mdm-config.sh && chmod +x ./mdm-config.sh && ./mdm-config.sh`
	3. Open CLI - Terminal
		1. Paste the contents from the clipboard
		2. Follow the steps
	4. Reboot the device if performing this step only. Otherwise goto next step

9. **Fix - MDM-HostFile**
    
	1. Goto this URL - `https://github.com/LogicRepairs/MDMBypassMacOS`
	2. Copy the following - `curl https://raw.githubusercontent.com/LogicRepairs/MDMBypassMacOS/main/mdm-hostfile.sh -o mdm-hostfile.sh && chmod +x ./mdm-hostfile.sh && sudo ./mdm-hostfile.sh`
	3. Open CLI - Terminal
		1. Paste the contents from the clipboard
		2. Follow the steps
	4. Reboot the device if performing this step only. Otherwise goto next step

10. **Disable Device Enrollment Notification**
    
	1. Goto this URL - `https://github.com/LogicRepairs/MDMBypassMacOS`
	2. Copy the following - `sudo open /System/Applications/TextEdit.app /System/Library/LaunchDaemons/com.apple.ManagedClient.enroll.plist`
	3. To edit `com.apple.ManagedClient.enroll.plist`
		1. Open CLI - Terminal
		2. Paste the contents from the clipboard
		3. change
		4. `<true/>` under `<key>com.apple.ManagedClient.enroll</key>`
		5. to
		6. `<false/>`
		7. Reboot the device if performing this step only. Otherwise goto next step

12. **Reboot** the device
