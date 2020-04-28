---
title: "Windows Funktionsupdate 1903"
date: 2019-07-27T15:34:30-04:00
categories:
  - Windows
tags:
  - Betriebssytem
  - Update
---

Dieses Wochenende  mehrere Win 10 Installationen auf die Version 1903 angehoben.  
Neue Funktionen wie "Sandbox" sind die Highlights. Aber auch Kleinigkeiten wie Im Task-Manager festzulegen, welche Registerkarte beim Start sichtbar sein soll sind toll ("Optionen/Standardregisterkarte festlegen").  
Das auf der Systempartition für Windows freier Speicherplatz (7% wenn nicht anders eingestellt) reserviert wird, ist sicher eine kontrovers diskutierte Funktion.

## Troubleshooting 

Zwei Geräte hatten das RST (Rapid-Storage-Technik) Problem. Die Lösung von MS - RST Treiber aktualisieren - hat nicht funktioniert

Lösung war:  
1. RST deinstallieren
2. Neustart
3. Treiberdatei "iastora.sys" umbennen  
4.  Neustart
5. Funktionsupdate durchführen  
6. RST installieren

Zuerst auf der Website von BeepingComputer gesehen: "Windows 10 1903 Update Blocked by Old Intel Rapid Storage Drivers"


## Fazit

Ende gut, alles gut.

# Quellen  

[What's new in Windows 10, version 1903 IT Pro content](https://docs.microsoft.com/en-us/windows/whats-new/whats-new-windows-10-version-1903)  

[Updating to Windows 10, version 1903 on devices with certain versions of Intel® Rapid Storage Technology (Intel® RST) drivers](https://support.microsoft.com/de-ch/help/4514156/updating-to-windows-10-version-1903-on-devices-with-certain-versions-o)  

[Windows 10 1903 Update Blocked by Old Intel Rapid Storage Drivers](https://www.bleepingcomputer.com/news/microsoft/windows-10-1903-update-blocked-by-old-intel-rapid-storage-drivers/)  

[Intel® Rapid-Storage-Technik (Intel® RST) Benutzeroberfläche und Treiber ](https://downloadcenter.intel.com/de/download/28966/Intel-Rapid-Storage-Technik-Intel-RST-Benutzeroberfl-che-und-Treiber?product=55005)  

## Meta

Erstellt:		27. Juli 2019  
Modifiziert:	27. Juli 2019
