﻿---
title: "Windows Netzwerkfunktion Peer to Peer"
date: 2020-07-11T5:31:30-04:00
categories:
  - windows
tags:
  - netzwerk
  - grundlagen
---

## Um was geht es?

Computer ("Knoten") in einem "Peer to Peer" (P2P) Netzwerk stellen sich gegenseitig die Resourcen (Daten, Dienste, Hardware, etc.) zur Verfügung. Im Gegensatz zum Client/Server Ansatz, wo ein Server Resourcen zur Verfügung stellt und die Clients diese nutzen. Diese Form des Netzwerkes wurde in den 90er Jahren mit den (illegalen) Tauschbörsen wie Napster, Lime, Mule, etc. populär. Nahezu jedes Betriebssystem hat diese Funktion dabei. Und auch aktuelle Software wie Bitcoin setzt darauf. 

Computer mit dem Betriebsystem Windows 10 kann man über die Netzwerktechnologie "Active Directory" verbinden. Das bedingt jedoch ein zusätzliches Gerät, welches als Server diese Aufgabe übernimmt. Darauf wird eine spezielle Windows Variante ("Server") installiert.  

Für wenige Computer hat Windows von Beginn an eine andere Netzwerktechnologie dabei gehabt: ["Peer to Peer"](https://www.itwissen.info/Peer-to-Peer-Netz-peer-to-peer-network-P2P.html).  Windows kennt das seit der Version 3.1 ("Windows für Workgroups"). Im Peer to Peer Netzwerk muss jeder Zugriff von anderen Computern "händisch" autorisiert werden. Später kam eine Windows Server Version auf den Markt mit mit dem Konzept von [PDC / BDC](https://www.itprotoday.com/windows-8/understanding-pdcs-and-bdcs) arbeitete.  

Die Arbeitsgruppe alias Workgroup alias Heimnetzgruppe (ab Windows 7) spielt(e) dabei eine zentrale Rolle. D.h. die Geräte finden sich über den einheitlichen Arbeitsgruppen Namen und ihren individuellen Computernamen (max 15 Zeichen). Erfahrungswert: Computernamen sollten nicht ausschliesslich aus Ziffern bestehen. Mit der Version 1803 von Windows 10 wurde dieses Konzept fallen gelassen.  

## Basiswissen

Das Windows P2P besteht aus drei Elementen:  
- Freigaben (Verzeichnisse, Drucker, Netzwerkresoucen)  
- Benutzern  
- Berechtigungennn  

Die "Berechtigungen" finden auf zwei unabhängigen Technologien statt:  
* SMB (Netzwerk) die Freigabe Berechtigung  
* NTFS (Dateiebene: Ein Verzeichnis ist auch eine Datei) - Lese / Schreibrechte  

Die Komplexität ist die Mutter der Fehler. Daher sollten Freigaben auf der Dateiebene nur für Verzeichnisse gemacht werden. Nicht für einzelne Dateien.  

Jede Freigabe muss beide Ebenen berücksichtigen. Ein universelles Prinzip in der IT besagt, dass wenn sich die Konfiguration dieser zwei Ebenen widerspricht, wird die stärkere Einschränkung wirksam werden. Ein anderes Prinzip im Zusammenhang mit Gruppen und Berechtigungen heisst "AGDLP" bzw. seit ein paar Jahren IGDLA  

AGDLP: Account => Global Group => Domain Local Group => Permission  
"Neu:"  
IGDLA: Identity => Global Group => Domain Local Group => Access  

Das grundlegende Benutzer / Berechtigungssystem von [Linux](https://de.wikibooks.org/wiki/Linux-Praxisbuch/_Benutzer-_und_Berechtigungskonzepte) und Windows ist ähnlich aufgebaut. Kennt man eines, versteht man das andere schnell.

Ob die Geräte über WLAN oder Lan (Ethernet) mit dem Router verbunden sind, spielt keine Rolle. In Windows 10 kann man seit längerem auch [Software Updates "Peer to Peer"](https://www.windowspro.de/wolfgang-sommergut/windows-10-update-delivery-optimization-gpos-konfigurieren) verteilen.

### NetBIOS

Klarstellung: NetBios ist eine API. Kein Netzwerkprotokoll.  
Umgangssprachlich und abhängig vom Kontext wird es als Netzwerkprotokoll definiert. Ist ein Akronym und steht für "Network Basic Input Output System". Wurde in den 80er Jahren von IBM entwickelt. Ziel war es, lokale Computer zu verbinden.  

Anders als die heute gängigen Netzwerktechnologien, werden keine Pakete (OSI Ebene 3) verwendet. Stattdessen implementiert NetBIOS Funktionen zur [Namensauflösung](https://de.wikipedia.org/wiki/Namensaufl%C3%B6sung), [paket](https://de.wikipedia.org/wiki/Paketvermittlung)- und [verbindungsorientierten](https://www.airnet.de/cr1-gfe/de/html/InfoAustKomp_learningObject36.xml) Kommunikation.  

### NetBIOS Frames Protocol ("NBF")  

Korrekt: "NetBIOS über IEEE 802.2 LLC" - kommuniziert mit der Darstellungschicht (NetBIOS) und der Sicherungsschicht (LLC) über MAC-ID (OSI Ebene 2). Nicht routingfähig. Die Identifizierung der Quell- und Zielcomputer erfolgt nur per Hostname. Dieser Hostname ist unter Windows der „Computername“.   

### NetBEUI ("NetBIOS Extended User Interface")  

Einfaches, selbst konfigurierendes, nicht routbares Protokoll.

### NetBIOS over TCP/IP ("NBT", "NetBT")   

Definiert in den RFC 1001 und 1002.

### WINS (Windows Internet Name Server)  

Die Microsoft-Implementierung eines NetBIOS Name Servers  

### SMB

Die "Peer to Peer" Funktion setzte ursprünglich das Protokoll SMB sowie den daraus aufbauenden Dienst "Computer Browser". Nachdem SMB Version 1 als veraltet und unsicher eingestuft wurde, stellte man auf "Function Discovery Provider Host" (Deutsch: Funktionssuchanbieter-Host) um. D.h. dieser Dienst muss gestartet sein. Die zweite Voraussetzung ist die aktivierte ["Netzwerkerkennung"  ](https://thomasknoefel.de/konfigurieren-der-netzwerkerkennung-in-windows-10/). Dieses nutzt das Protokoll "WS-DISCOVERY".  

**SMB Version 1 sollte unbedingt ausgeschaltet bleiben. Das Sicherheitsrisiko ist sehr hoch**  

## Arbeitsgruppe / Heimnetzgruppe  

Diese Arbeitsgruppen existieren nur auf dem lokalen Computer. Genauer in der Security Accounts Manager (SAM) Datenbank.  

Mit der Windows 10 Version 1803 wurden die Heimnetzgruppen aus Windows [entfernt](https://support.microsoft.com/de-de/help/4091368/windows-10-homegroup-removed). Dennoch können [Drucker](https://support.microsoft.com/de-de/help/4089224/windows-10-share-network-printer) und [Dateien](https://support.microsoft.com/de-de/help/4027674/windows-10-share-files-in-file-explorer) trotzdem freigebben werden.  

[Dieses](https://www.youtube.com/watch?v=uNeo7O6ImAo) Video (HOW TO HOMEGROUP WITHOUT HOMEGROUP in Windows 10) des YouTube Kanals "Alternative Tech Reports" zeigt Schritt für Schritt wie man mehrere lokale Windows 10 Computer mit Freigaben vernetzt.  

Wenn man im lokalen Netzwerk noch Windows Versionen vor 10 (8.1 / 8 / 7) im Einsatz hat müssen dort die Arbeitsgruppen gelöscht werden. Folgende Dienste sollten in den alten Windows Versionen auf verzögerter Start gestellt sein:
* Funktion Anbieter Host
* Funktion Reccourcenveröffentlichung
* Netzwerkverbindungen
* UPnP-Geräte-Host
* Peer Name Resolution-Protokoll
* Peer-Netzwerk-Gruppenzuordnung
* Peernetzwerkidentitäts-Manager

## Shell: CMD  

Diese Funktionen setzen i.d.R. eine Shell mit Administrator Berechtigungen voraus.  

net file - Zeigt die Dateien auf dem eigenen Computer an, auf die von anderen zugegriffen wird  

![net files](/image/17-2.png)  

net share - [Zeigt die Shares (freigegebene Ordner) an](https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/hh750728(v=ws.11)).  

net share namederneuenfreigabe=C:\Users\bofh\Prj_Baerengraben - Verzeichnis "Prj_Baerengraben" unter dem Namen namederneuenfreigabe erstellt  

net use x: \\computername\freigabenname - Laufwerk X: für das Verzeichnis \\computername\freigabenname mounten  

[net localgroup](https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/cc725622(v=ws.11)) zeigt die lokalen Arbeitsgruppen an. Diese [Website](https://www.colorconsole.de/console/de/112.htm) erklärt das in deutscher Sprache.  

[whoami /groups](https://www.der-windows-papst.de/wp-content/uploads/2014/09/Windows-7-Whoami.pdf) zeigt den angemeldeten Benutzer (Token) und seine Gruppen an. Die verlinkte Websites geht tiefer in den mächtigen Befehl "whoami" ein.  

fsmgt.msc - Freigaben anzeigen / verwalten  

compmgmt.msc - ![Computermanagement Konsole](/image/17-1.png)  

## Shell: Powershell  

Laufwerk (NTFS) Berechtigungen [anzeigen](https://www.colorconsole.de/PS_Windows/de/Get-Acl.htm)  
[Praxistipp:](https://www.windowspro.de/tipp/dateirechte-anzeigen-auf-kommandozeile-powershell) Ausgabe der ACL des aktuellen Ordners mit Unterordnern:  

''Get-ChildItem <Path-to-query> -Recurse | where-object {($_.PsIsContainer)} | Get-ACL | Format-List | Out-File <Out-File-Path>\<Out-File>.txt''  

Computer zu einer Workgroup [hinzufügen](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.management/add-computer?view=powershell-5.1)  

Computer aus einer Workgroup [entfernen](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.management/remove-computer?view=powershell-5.1)  

## Troubleshooting  

1. Netzwerkverbindung 

## Abschliessend

Seit "Windows as a Service" muss man auf Überraschungen / Änderungen gefasst sein. Wolfgang Sommergut beschreibt in diesem [Artikel](https://www.windowspro.de/wolfgang-sommergut/gpos-fuer-windows-10-1607-excel-tabelle-einstellungen-fuer-enterprise-wufb) einen Sachverhalt mit GPO und Softwareverteilung (P2P).  

## Quellen  

1. [JOCHEN DINGER: Das Potential von Peer-to-Peer-Netzen und -Systemen : Architekturen, Robustheit und rechtliche Verortung](https://www.ksp.kit.edu/9783866443273)

2. [MS Docs: Peer-to-Peer-Netzwerkszenarien](https://docs.microsoft.com/de-de/dotnet/framework/network-programming/peer-to-peer-networking-scenarios)

3. [MS Docs: NetBIOS-Based Transports](https://docs.microsoft.com/en-us/openspecs/windows_protocols/ms-cifs/1430ebe9-2ad0-4763-b14f-c720338e0482)  

4. [support.microsoft.com: Vergleich von Windows NT-Netzwerkprotokolle](https://support.microsoft.com/de-ch/help/128233/comparison-of-windows-nt-network-protocols)  

5. [MS Docs: SMBv1 is not installed by default in Windows 10 version 1709, Windows Server version 1709 and later versions](https://docs.microsoft.com/en-nz/windows-server/storage/file-server/troubleshoot/smbv1-not-installed-by-default-in-windows)  

6. [HomeGroup from start to finish](https://support.microsoft.com/en-us/help/17145/windows-homegroup-from-start-to-finish)  

7. [YT: HOW TO HOMEGROUP WITHOUT HOMEGROUP in Windows 10](https://www.youtube.com/watch?v=uNeo7O6ImAo)  

8. [Linux:ZUGRIFF AUF NETZWERKVERZEICHNISSE MIT NAUTILUS](https://kofler.info/zugriff-auf-netzwerkverzeichnisse-mit-nautilus/)  

9. [MS Docs: Net services commands](https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-xp/bb490949(v=technet.10))

10. [faq-o-matic.net:Datei- und Freigabeberechtigungen in Windows](https://www.faq-o-matic.net/2015/12/28/datei-und-freigabeberechtigungen-in-windows/)  

11. [Active Directory – What is IGDLA & UGDLA?](https://theknowledgehound.home.blog/2020/04/12/active-directory-what-is-igdla-ugdla/)  

12. [Using Group Nesting Strategy](https://blogs.msmvps.com/acefekay/2012/01/06/using-group-nesting-strategy-ad-best-practices-for-group-strategy/)




## Meta

Erstellt:	18. Juli 2020  
Modifiziert:	24. Juli 2020
