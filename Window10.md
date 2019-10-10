### Disabling UAC notifications [r1]

1) Open Control Panel and make your way to User Accounts and Family Safety\User Accounts (You could also open the start menu and type "UAC")

2) From here you should just drag the slider to the bottom to disable it.

### Run A Silent Batch Script [r2]
```
nircmd elevatecmd exec hide [path to .bat file]
```

### Enable or Disable Screen Edge Swipe in Windows 10 [r3]
#### Disable_Screen_Edge_Swipe.reg
```
Windows Registry Editor Version 5.00

; Created by: Shawn Brink
; Created on: April 26th 2016
; Tutorial: http://www.tenforums.com/tutorials/48507-edge-swipe-screen-enable-disable-windows-10-a.html


[HKEY_CURRENT_USER\SOFTWARE\Policies\Microsoft\Windows\EdgeUI]
"AllowEdgeSwipe"=-

[HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\EdgeUI]
"AllowEdgeSwipe"=dword:00000000
```

### Enable and disable fast startup on Windows 10[r4]
1. Goto Control Panel
2. Click Choose what the power buttons do.
3. Click Change settings that are currently unavailable.

4. Click Choose what the power buttons do. Click Change settings that are currently unavailable.
5. Click Turn on fast startup (recommended) so that the checkmark disappears.
6. Click Save changes.

### Task Monitoring / Task restart batch scripts
```
@echo off

SET IMG_NAME=xxx.exe
SET THE_EXE=C:\path\to\exe\%IMG_NAME%

taskkill /f /fi "status eq not responding"
tasklist /nh /fi "imagename eq %IMG_NAME%" | find /i "%IMG_NAME%" > nul || (start %THE_EXE%)

echo "cron job (StartIFNotRun) run at %date% %time%" >> C:\log\debug.log


timeout 10

echo 'set the task to the top'
C:\path\to\nircmdc.exe win settopmost title "some title" 1


```

[r1]: https://superuser.com/questions/1191650/why-is-windows-10-always-asking-for-administrator-permission-to-move-files
[r2]: https://www.raymond.cc/blog/hidden-start-runs-batch-files-silently-without-flickering-console/
[r3]: https://www.tenforums.com/tutorials/48507-enable-disable-edge-swipe-screen-windows-10-a.html
[r4]: https://www.windowscentral.com/how-disable-windows-10-fast-startup
