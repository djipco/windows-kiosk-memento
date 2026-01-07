# Windows Kiosk Setup Memento

This is my own checklist to set up a standalone Windows machine for installations that should run uninterrupted for long periods of time. This is still a work in progress!

## Dedicated User Account

I usually create a dedicated user account for each project. This allows me to start with a blank slate and tweak the settings for each project individually.

* Create new user account with **lusrmgr.msc**
* Check "Password never expires". If computer is in a secure location, just leave the password blank (use caution). Alternatively, use auto-login (see below).
* Right-click user and go to "Member of" tab. Add it to admins group (if appropriate).
* Log into new user and say no to every goddamn prompt!

## Language

If your project will travel to various parts of the world, it's probably safer to set the dedicated account to use **English** as its language. This will make it easier for a majority of people to help you troubleshoot the project if the need arises. You can do that in the **Time & Language** section of the settings.

## Task Scheduler

You can use the task scheduler to start whatever appropriate program. This can also be used to run a custom .bat file.

* Schedule whatever should be started at boot
* Leave a delay because Windows still does a bunch of stuff after it has officially started
* You can also use AutoHotKey for more advanced scripting

## Power

* Go to Power & Sleep settings and make sure the computer never sleeps (high performance)

## System Sounds

It might be appropriate to disable system sounds. You can do that by going to the **Sound** control panel and selecting "No sound" as the Sound Scheme. You can also uncheck "Play Windows Startup Sound".

![sound2](https://github.com/djipco/windows-kiosk-memento/assets/3246696/73d63fdf-d624-41cb-bcc1-1c76348215c1)

## Notifications

* [Use group policy to hide notifications](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-defender-security-center/wdsc-hide-notifications#use-group-policy-to-hide-all-notifications)

## Windows Updates

* Disable automatic updates with Group Policy
  * Start > gpedit.msc
  *  Computer Configuration > Administrative Templates > Windows Components > Windows Update
*  Double-click the Configure Automatic Updates policy on the right side.
*  Check Disable to turn off the Policy

#### Windows Pro, Enterprise and Education

* [Disable Windows update through Group Policy](https://www.easeus.com/backup-recovery/how-to-stop-windows-10-from-automatically-update.html#part2)

#### Windows Home

[Disable Windows update through the registry](https://www.easeus.com/backup-recovery/how-to-stop-windows-10-from-automatically-update.html#part4)

## Remote Control

* Install remote control application such as RustDesk and configure access

## Startup Programs

* Open Task Manager > Startup Tab
* Disable all unneeded programs (Cortana, Windows Security Notification Icon, Java Update Scheduler, etc.)

## Time Zone

* Set the right timezone for the location.

## Windows Defender

* Disable it! (considering that the machine is properly isolated)

## Auto-login

## Daily reboot

This may or may not be appropriate. It may allow the installation to simply recover without having to intervene.

## File Explorer

* Control Panel > File Explorer Options > View tab 
  * Check Always Show Menus
  * Check Show hidden Files, Folders and Drives
  * Check Hide Empty Drives
  * Uncheck Hide extensions for known file types

## USB Power Management

* Start > Device Manager > Universal Serial Bus Controllers
* Doubleclick on each USB Root Hub heading
* Click on Power Management Tab and uncheck “Allow the Computer to turn off this device to save power"

## Automatic Startup Repair
In Windows 11, if the computer was not properly shut down, it is very likely that on the next boot you will be presented with the Automatic Startup Repair screen (pale blue). This prevents the computer from continuing to boot. To disable it:
```
bcdedit /set {default} recoveryenabled No
bcdedit /set {default} bootstatuspolicy ignoreallfailures
```

## Boot When Powered On

Must BIOS software can be set so that the computer boots when power comes back. Enable that.

## More: 

* https://derivative.ca/community-post/show-machine-setup-permanent-and-temporary-art-installations-windows-10/63572
* https://github.com/brangerbriz/up-4evr-windows-10
* https://learn.microsoft.com/en-us/windows/configuration/kiosk-prepare
