### Dieser Zweig beinhaltet meine Änderungen und zusätzliche Features für den RF1000 3D Drucker, basiert auf der offiziellen RF.01.11 Firmware von [https://github.com/RF1000/Repetier-Firmware](https://github.com/RF1000/Repetier-Firmware)


### Zusätzliche Features
* Filamentload Funktion per Gcode M4001 S[delta F-Wert]
* Erlaube ZMinEndschalter beim nächsten G1 Zx Befehl zu überfahren per Gcode M4031 

### Will ich auch haben
Falls du diese Features für deine RF.01.11 Firmware nutzen willst, reicht es aus folgende Dateien aus dem RF1000 Ordner zu ersetzen:
* Communication.cpp
* Communication.h
*  RF.cpp
*  motion.h


### Feature Beschreibung:

##### Gcode M4001 S[delta F-Wert] ; Filamentload Funktion
Der Extruder befördert das Filament in 1mm Schritten solange in das Hotend bis der F-Wert (Messzellen, DMS) den angegebenen delta Wert überschreitet. Funktioniert nur bei aufgeheizten Hotend.

Anwendungsbeispiel im Slicer Startcode:  
...  
M400 ; warte bis alle Bewegungen abgeschlossen  
M4001 S1000 ; Filamentload Funktion bis delta F-Wert > 1000  
M400 ; warte bis alle Bewegungen abgeschlossen  
...  

##### Gcode M4031 ; Erlaube ZMinEndschalter zu überfahren
Dieser Gcode erlaubt der Firmware beim nächsten G1 Zx Befehl den ZMinEndschalter zu überfahren. Weitere nachfolgende G1 Zx Befehle die das Heizbett nach oben fahren werden sofort bei erreichen des ZMinEndschalters gestoppt.  
Hintergrund:  
Bisher war es nicht möglich eine geringere Höhe im 1. Layer anzufahren als die Höhe der "Startline" im Slicer-Startcode.

Anwendungsbeispiel im Slicer Startcode:  
...  
M400 ; warte bis alle Bewegungen abgeschlossen  
M4031 ; erlaube ZMinEndschalter beim naechsten G1 Zx zu ueberfahren.  
...  


#### Versionsstand RF.01.11.X-4 (04.01.2016)

#### Changelog
siehe changelog-X4r3.txt
