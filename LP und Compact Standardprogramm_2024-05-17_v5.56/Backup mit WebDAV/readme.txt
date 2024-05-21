zum Einbinden in Versa Projekte (braucht FGV System Konstanten (Seriennummer), VI Shut Down etc. ... ggf. Anschlüsse anpassen)

WebDAV VIs durch im Projekt - Bedingte Deaktivierungen "WebDAV", dann kann man auf Knopfdruck zwischen FTP und WebDAV gewechselt werden !

(Die FTP VI's "Namen cRIO Daten.vi" und "Daten speichern auf PC.vi" sind ebenfalls noch drinnen ... habe ich jetzt gelöscht)

…\Seiten\FT-IR\Get Spectra\FTIR Diag.ctl … als ENUM ist notwendig ... wenn das ein RING ist, dann eine Kopie davon als ENUM machen,
und in Backup/FTIR_Dialog_ScreenShots.vi ersetzen !!!

(habe den Dialog jetzt vom MOA übernommen mit den Skalierungseinstellungen und dem Ring +  Enum Kopie ... )

Zum signalisierenden Fernsteuern der Graphikauswahl im FTIR_Dialog ist das VI ...Allgemein/Vi Element.vi notwendig !

SysLog wird jetzt ebenfalls mit ins Backup kopiert (bedingt aktiviert !) ... der cRIO Teil ist sowieso im KonfigIAG.

Doppelcklick auf die Liste der BackUp's funktioniert jetzt auch, wenn Leerzeichen in Ordnernamen sind (Pfad stat String angehängt).


Backup zurück spielen ist noch offen ... für cRIO möglich (mit reboot wenn Baustein funktioniert), beim PC müsste ein eigenes .exe gemacht werden (Versa schliessen und anderes aufrufen ?!) ?!

Hinweis: alle Konfig Files gehen dann mit (falls kaputt geworden sinnvoll) ?

SysLog Eintrag fehlt auch noch ...

riw 05.0.2019