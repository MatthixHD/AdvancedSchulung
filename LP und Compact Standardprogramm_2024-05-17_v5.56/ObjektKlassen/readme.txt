Steuerung PNS ObjektKlassen:

Verwendung in anderen Projekten (Abh�ngigkeiten):

FGV PNS Steuerung.vi ... h�lt "das" SteuerungsObjekt - verwendet in VI Modbus KOMM.vi

PNS.lvlib
- Aktionen FGV Istwerte.ctl ... um "schreiben" erweitern (Cluster mit Regler/UsrVal/Alarm)
- FGV PNS Istwerte.vi ... DatenTypen (input, output, init) aus SteuerungsObjekt nehmen, Adressarithmetik in Alarme und Regler deaktivieren, schreiben Cluster input (richtiger Anschluss!) 
- FGV Grenzwerte PNS.vi ... bleibt
- Loopkennung.vi ... um "schreiben" erweitert (TypDef Aktionen FGV Loopkennung.vi verwenden) 
    mit Cluster (Loops/Ger�tetype) input  (Ger�tetypenErkennung in SteuerungsObjekt!; �berlegung [Adressarithmetik] auch durch "Anweisungscode nach Zustand setzen.vi" ersetzen ?)
- Komm Modbus.lvlib
  - FGV Modbus Kommunikation (OO).vi ... Input und Output f�r SteuerungsObjekt (statt Verbindungs ID)... FGV Grenzwerte, Istwerte und Loopkennung werden weiter verwendet ... 
    Adressen und Modbus Aufrufe jetzt im SteuerungsObjekt (Interface: Kommunikation UsrVal/Alarm/Regler/Lopkennung/Geraetekennung.vi sowie
       lesen: Interface/Istwerte als Cluster.vi, Loopkennung als Cluster.vi
       schreiben: Protected/Datenzugriff/Anweisungscode schreiben.vi, Grenzwerte PNS schreiben.vi (eventuell in Interface heausziehen ?)
    (wenn auf FGV Modbus Kommunikation OO.vi umbenannt muss auch der Aufruf in VI Modbus KOMM.vi und VI Anlagengrenzwerte PNS.vi ersetzt werden !)
    (x: Eception Codes, Aktuelle Adressen f�r Schreiben, Adressen lesen entfallen)
    (x: Ist mit Soll vergleichen ... jetzt im Interface Kommunikation)
  - VI Modbus KOMM.vi ... um "initialisieren" f�r erstamliges Erzeugen der ObjektInstanz in FGV PNS Steuerung.vi erweitert 
  x Adressen Filtern.vi ... jetzt der ObjektSubKlasse mit den jeweiligen Adressen
  x Adressen.vi ... jetzt pro SteuerungsType in der jeweiligen ObjektSubKlasse
  x Ist mit Soll vergleichen.vi ... jetzt pro SteuerungsType in der jeweiligen ObjektSubKlasse
  x Lesen.vi ... jetzt mit der Modbus Referenz gekapselt im SteuerungsObjekt
  x Schreiben.vi ... jetzt mit der Modbus Referenz gekapselt im SteuerungsObjekt
  x MB Kommunikation.vi ... jetzt mit der Modbus Referenz gekapselt im SteuerungsObjekt
  - Modbus TypDef.lvlib
    x Regler.ctl  ... jetzt gekapselt und einheitlich im SteuerungsObjekt
      (wird in FGV PNS Istwerte.vi und Diagnose.vi [Ist mit Soll vergleichen.vi entf�llt] verwendet und muss dort druch die entsprechende TypDef des SteuerungsObjektes in protected/TypDef ersetzt werden)
    x Alarme.ctl  ... jetzt gekapselt und einheitlich  im SteuerungsObjekt
      (wird in FGV PNS Istwerte.vi und Diagnose.vi [Ist mit Soll vergleichen.vi entf�llt] verwendet und muss dort druch die entsprechende TypDef des SteuerungsObjektes in protected/TypDef ersetzt werden)
    x Adressen lesen.ctl  ... jetzt und einheitlich  gekapselt im SteuerungsObjekt
    x Adressen schreiben.ctl  ... jetzt und einheitlich  gekapselt im SteuerungsObjekt

- Stoerungen.lvlib / Stoerungen (193-256) - PNS.vi ... Regler Namen im Cluster neu aufschl�sseln ... PV -> Istwert �ndern (mehrmals) !
    Array Index von 11 -> 6 �ndern f�r UsrVal -> ERR. 199 (Druckluft St�rung .. wie im VI Anlagengrenzwerte PNS.vi) !!!
- VisBx Anzewige.vi ... ebenfalls die Namen neu aufschl�sseln (PV -> Istwert)
- Aufrufe von Loppkennung.vi ... Aktion neue Konstante bilden (Probleme mit Nummerierung)
  
Tipps: bei alten Projekten kann die Sprachverwaltung.lvlib fehlen ... protected/Loops ermitteln.vi ruft 2 VIs daraus auf (deaktivieren und durchverbinden!)

RIW
(2018-02-16)

###############################################
BugFixes:

2018.02.19 Buchstaben vertauscht bei "Ist mit Soll vergleichen UsrVal.vi (UrsVal) ... daher Vererbung nicht erfolgt!
2018.02.19 Index Anschl�sse nach Kopieren weg in Ist mit Soll vergleichen Regler.vi bei Schneider (mini8 schon vorher ausgebessert)
2018.02.19 VI Anlagengrenzwerte PNS.vi AWC Ist wird falsch angezeigt (-1 entfernt) und Druckluft Fehler auch (Index von 11 auf 6 !)

###############################################
Known Bugs(Featuers):

2018.02.19 bei AutoDetection TCP LAN Kabel umstecken Mini8 Schneider bleiben die Grenzwewrte und Ger�tetype in der Maske bzw. Grenzwerte werden 0 ... Maske neu starten erforderlich !???
###############################################

2018.03.20
�nderungen in der Objektklasse:
Wir lassen daher die �nderung im VI �Ist mit Soll vergleichen Regler.vi� auf der selben Adressreihe wie im Adressen.vi � aber den �SP1� statt �Zielsollwerten� !!!
Das Initialisieren der Alarm Adressen vor der FOR Schleife im VI �Ist mit Soll vergleichen Alarme.vi� f�r mini8 bleibt (in der Schneider Variante war es bereits vorhanden).
Und dazu kommt die Erweiterung der Objektklasse um die tats�chliche Loopkennung zus�tzlich zu den Loopnamen f�r folgendes:

Folgende Iden von FUM habe ich zus�tzlich im VI �VI Anlagengrenzwerte PNS.vi� und �FGV Modbus Kommunikation OO.vi� eingebaut: 
PNS Grenzwerte f�r �Reserve� Loops werden ausgegraut und deaktiviert,
der maximale Loop Count im FGV Modbus Kommunikation wird herunter geschraubt � Reserve Loops brauchen nicht mit abgefragt werden, dadurch wird die Kommunikation schneller 
(bis zum letzten nicht Reserve Loop, wenn dazwischen welche reserviert wurden schon).

Ist das �VI Anlagengrenzwerte PNS.vi� aktiv, wird es nach dem Initialisieren (Case Nr. 12) neu gestartet (�ber Bildwechsel Aufruf wie aus dem Menu � das Diagnosefenster geht dann auch mit).

Dadurch ist jetzt ein Plug&Play von unterschiedlichen und unterschiedliche konfigurierten VFS m�glich.

###############################################
2018.03.21 
Seriennummer f�r Schneier Steuerung aus Ger�tekennung ermitteln und in PNS Anlagengrenzwerte.vi anzeigen ...
###############################################
###############################################
2018.03.26
Ger�tekennung hinzugef�gt f�r schnelleres ermiteln unterschiedlicher VisBx PNS Bilder ...
###############################################


Let wire and node
gently flow into a world
of class and method.

� LabVOOP