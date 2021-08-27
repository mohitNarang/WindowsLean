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


Source: https://stackoverflow.com/questions/62174426/how-to-permanently-disable-windows-defender-real-time-protection-with-gpo



In newer versions of Windows, Group Policy settings for Microsoft Defender are reverted back.
To prevent this, before changing them:

    Open Resource Monitor (type resmon.exe in the search box)
    Overview
    Find MsMpEng.exe in the list
    Right-click > Suspend Process

In newer versions of Windows, Tamper Protection was added.
Tamper Protection must be disabled before changing Group Policy settings, otherwise these are ignored.

    Open Windows Security (type Windows Security in the search box)
    Virus & threat protection > Virus & threat protection settings > Manage settings
    Switch Tamper Protection to Off

To permanently disable real-time protection:

    Open Local Group Policy Editor (type gpedit.msc in the search box)
    Computer Configuration > Administrative Templates > Windows Components > Microsoft Defender Antivirus > Real-time Protection
    Enable Turn off real-time protection
    Restart the computer

To permanently disable Microsoft Defender:

    Open Local Group Policy Editor (type gpedit.msc in the search box)
    Computer Configuration > Administrative Templates > Windows Components > Microsoft Defender Antivirus
    Enable Turn off Microsoft Defender Antivirus
    Restart the computer




    Regedit.exe
    HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender
    New > DWORD DisableAntiSpyware
    Set it to 1
    Reboot

If it doesn't work then one more step:

    Regedit.exe
    HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender\Real-Time Protection (create this key if not existing)
    New > DWORD DisableBehaviorMonitoring; set it to 1
    New > DWORD DisableOnAccessProtection; set it to 1
    New > DWORD DisableScanOnRealtimeEnable; set it to 1
    Reboot

You can also save the code below to disable_realtime_protection.reg and run

Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender]
"DisableAntiSpyware"=dword:00000001

[HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender\Real-Time Protection]
"DisableBehaviorMonitoring"=dword:00000001
"DisableOnAccessProtection"=dword:00000001
"DisableScanOnRealtimeEnable"=dword:00000001

