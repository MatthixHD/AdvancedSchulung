Habe für Versa Backup und NMS Update Manager und cRIO Update Manager erst nur eine bedingte Deaktivierung für die Implementierung gemacht,
beginne aber grerade im NMS (später auch Versa) diese druch eine automatische Erkennung zur  Laufzeit zu ersetzen:

NMS "Update Manager":

Aktionen FTP WebDAV.ctl ... erkennen, lesen
1) FGV FTP WebDAV.vi ... gibt Enum FTP WebDAV.ctl zurück und verwendet "cRIO Test ftp webDAV installed.vi"

3) 2) Enum FTP WebDAV.ctl ... nix, ftp, webDAV

4) cRIO Test ftp webDAV installed.vi ... liegt noch im "Update cRIO"

Error Code siehe M:\PT\Technik\Software\Dokumentation Module\ErrorLogHistory SysLog\Error Codes.txt 
5562 ... no FileService available (ftp, webDAV)

5) Show Folder Helper.vi ... zeigt Ordner jetzt wieder im Windows Explorer (ab Win 10 kommt sonst der Web Browser!)

6) Datei speichern auf cRio.vi ... Speichert ein Array von Dateinamen vom PC auf die cRIO.
ftp ode webDAV (je nach FGV FTP WebDAV.vi Ausgang).

Sowohl für webDAV als auch ftp genügt diese URL/Pfad Notation:
home/lvuser/natinst/bin/ oder c/KonfigIAG/
(vorne kein / notwendig, hinten schon ! - ftp ist das egal, bei webDAV wird http://IP/files/ intern voran gestellt)

riw - 2019-02-22

7) Daten speichern auf PC.vi ... Speichert ein Array von Dateinamen von der cRIO auf den PC.
ftp ode webDAV (je nach FGV FTP WebDAV.vi Ausgang).

Sowohl für webDAV als auch ftp genügt diese URL/Pfad Notation:
home/lvuser/natinst/bin/ oder c/KonfigIAG/
(vorne kein / notwendig, hinten schon ! - ftp ist das egal, bei webDAV wird http://IP/files/ intern voran gestellt)

für Versa (Beispiel BMW) siehe:
M:\PT\Technik\Software\Dokumentation Module\FTP-WebDAV\readme.txt
M:\PT\Technik\Software\Dokumentation Module\FTP-WebDAV\Einbauanleitung.txt

