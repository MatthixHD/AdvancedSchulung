SysLog einbauen:

0) jetzt auch die bedingte Deaktivierung im Projekt für WebDAV (wie im Backup Modul) notwendig !

1) "Bitte Warten.vi" auf ablaufinvariant mit gemeinsamer Kopie setzen !

2) Menupunkt im system Menu: "System Log" zum Starten der halbdurchsichtigen "System Log Status" Anzeige
und natürlich im Main.vi bei den Menupunkten ...

3) Im Main.vi ganz am Anfang die Varaible zum Starten des Browsers mit "history button ref" setzen ... und initialisieren

4) die SysLog Loop im Main einfügen (mit dem "Bitte Warten" drinnen ...)

5) auf der cRIO Seite "Daten zu cRIO.vi" in dem die "Daten speichern" (mit dem "Bitte Warten") ausgewertet werden,
alle cases der Bildschimre, die nicht benutzt werden entfernen - ein "Standard" case nur mit dem SysLog Flash erstellen,
und in den anderen (Anlagengrenzwerte, Erweiterte Konfig) das SysLog Flash hinzufügen ...

6) auf der cRIO Seite die SoftWare Versionsnummer hinzufügen - und im SysLog Eintrag anzeigen ...

7) auf der PC Seite die Projektnummer, Seriennummer und SoftWare Version ...

8) überall, wo ein Eintrag sinnvoll / notwendig ist, den SysLog Eintrag aufrufen, geistreisch beschriftn und insofern wichtig, mit Werten ergänzen ...
dazu Fehler, Warnung (nur auf PC Seite) oder Info richtig setzen - und ob der nur für uns intern PWL 9) angezeigt wreden soll, oder immer ...

have some fun