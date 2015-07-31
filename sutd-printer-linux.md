Guide for Installation of Fuji Xerox Printer on Ubuntu 14.04 LTS
=========
> Document Version: 1.0

1. Open web browser and go to `http://localhost:631`, and select `Administration` Tab. Then click `Add Printer`.
![webpage01][webpage01]

2. Then type in username and password of your system account.
![webpage02][webpage02]
> Note: your **linux account** is required, not university account.

3. Choose `Windows Printer via SAMBA` from `Other Network Printers`.
![webpage03][webpage03]

4. Input `smb://192.168.100.80/FujiXerox_BW` on the **Connection** address, and then click `continue`.
![webpage04][webpage04]

5. Provide a **Name** for the printer and click `continue`.
![webpage05][webpage05]

6. Select `(Fuji Xerox)` from **Make** and click `continue`. 
![webpage06][webpage06]

7. Click `Add Printer`.
![webpage07][webpage07]

8. Then set default options for the printer.
![webpage08][webpage08]

9. Click the printer name, and then `Set As Server Default`.
![webpage09][webpage09]

10. Print a test file from your computer and then click the printer icon on task bar. 
![screenshot01][screenshot01]
	+ **Right Click** the file and select `Authenticate`. 
	+ Input Username: `SUTD1\studentID` and password
	+ Checked `Remember Password` option

11. **Done**

<!-- Links -->

[webpage01]: figures/sutd-printer-linux/webpage01.png "webpage"
[webpage02]: figures/sutd-printer-linux/webpage02.png "webpage"
[webpage03]: figures/sutd-printer-linux/webpage03.png "webpage"
[webpage04]: figures/sutd-printer-linux/webpage04.png "webpage"
[webpage05]: figures/sutd-printer-linux/webpage05.png "webpage"
[webpage06]: figures/sutd-printer-linux/webpage06.png "webpage"
[webpage07]: figures/sutd-printer-linux/webpage07.png "webpage"
[webpage08]: figures/sutd-printer-linux/webpage08.png "webpage"
[webpage09]: figures/sutd-printer-linux/webpage09.png "webpage"
[screenshot01]: figures/sutd-printer-linux/screenshot01.png "screenshot"

> By Sibo Song (sibo_song@mymail.sutd.edu.sg)
