# Windows Kiosk Setup Memento
Instructions to setup a standalone Windows machine for kiosk or installation purposes. This is a work in progress!

## Dedicated User Account

* Create new user account with lusrmgr.msc. 
* Check "Password never expires". If computer is in a secure location, just leave the password blank (use caution).
* Right-click user and go to "Member of" tab. Add it to admins group.
* Log into new user and say no to everything!

## Task Scheduler

* Schedule whatever should be started at boot
* Leave a delay because Windows still does a bunch of stuff after it has officially started

## Power

* Go to Power & Sleep settings and make sure the computer never sleeps (high performance)

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

* Install remote control application such as [UltraVNC](https://uvnc.com) (if you can reach the machine directly by IP)
  * Configure access 
* Install TeamViewer, LogMeIn or AnyDesk for access through firewalls

## Startup Programs

* Open Task Manager > Startup Tab
* Disable all unneeded programs (Cortana, Windows Security Notification Icon, Java Update Scheduler, etc.)


## Time Zone

* Set the right timezone for the location.

## Windows Defender

* Disable it!
* 
## Auto-login

## Daily reboot



## File Explorer

* Control Panel > File Explorer Options > View tab 
  * Check Always Show Menus
  * Check Show hidden Files, Folders and Drives
  * Check Hide Empty Drives
  * Uncheck Hide extensions for known file types

## USB POwer Management

* Start > Device Manager > Universal Serial Bus Controllers
* Doubleclick on each USB Root Hub heading
* Click on Power Management Tab and uncheck “Allow the Computer to turn off this device to save power"

## More: 

* https://derivative.ca/community-post/show-machine-setup-permanent-and-temporary-art-installations-windows-10/63572
* https://github.com/brangerbriz/up-4evr-windows-10
