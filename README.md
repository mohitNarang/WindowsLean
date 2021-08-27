# WindowsLean
Remove unwanted crap from windows to make it faster

# Disable Windows defender
Disabling Windows Defender using the Local Group Policy Editor

If you're running Windows 10 Pro, Enterprise, or Education, you can use the Local Group Policy Editor to disable Windows Defender Antivirus on your computer permanently by taking the following steps:

    open the Local Group Policy Editor
    browse to Computer Configuration > Administrative Templates > Windows Components > Windows Defender Antivirus
    on the right pane of the Local Group Policy Editor window, double-click the Turn off Windows Defender Antivirus policy
    select the Enabled option to disable Windows Defender
    click Apply and then click OK; restart the computer to apply the change. 

Disabling Windows Defender using the Registry Editor

if you're running Windows 10 Home, you won't have access to the Local Group Policy Editor. However, you can modify the registry to permanently disable the default antivirus by taking the following steps

    open the Windows Registry Editor and browse to HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender
    if you don't see the DisableAntiSpyware value on the right pane of the Registry Editor's window, right-click the Windows Defender key, select New and click on DWORD (32-bit) Value
    name the newly created value DisableAntiSpyware and press Enter
    double-click the newly created value and set its value to 1
    click OK and restart the computer to apply the change 
