# Task 1





||Evidence file (command)| What I expected|What I found| What I concluded|
|-|-|-|-|-|
|0|README|commands and lines|i did found what i expected|that there is plenty commands that i have go through|
|1|05 (systemctl --failed)|nightly-report failing|two units failed: legacy-sync and nightly-report|two leads; check which one is related to the ticket|
|2|06 (systemctl list-timers)|The timer might be dead|ast fired 09:42:01, next 09:44:01, 2 minutes apart.|Ruled out: broken timer.|
|3|09 (journalctl -u nightly-report)|First failure 14:20:01. |ailed to execute /usr/local/bin/nightly-report.sh:|The fault began at 14:20 on 9 Nov.|
|4|13 (ls -l /usr/local/bin)|Missing file|-rwxr-xr-x 1 root root 91 Nov  9 14:20 nightly-report.sh<br />|the file exists and is executable.|





ROOT CAUSE



I ASSUME nightly-report.sh was copied in on 9 Nov at 14:20 with Windows (CRLF) line endings



THE FIX 



The change is in the file on disk, so it survives a reboot. The timer needed no change. I would leave legacy-sync alone and raise it as a separate cleanup (disable it), because it is not part of this ticket.

