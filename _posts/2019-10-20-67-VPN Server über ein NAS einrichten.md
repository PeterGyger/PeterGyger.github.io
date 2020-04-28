---
title: "VPN Server über ein NAS einrichten"
date: 2019-10-20T11:34:30-04:00
categories:
  - Netzwerk
tags:
  - VPN
---

Eine private Cloud sollte über verschlüsselte VPN Verbindung genutzt werden. Die Gründe sind Legion und im Internet en Mass zu finden.  
Eine Möglichkeit einen VPN Server zu Hause zu installieren ist ein NAS, das ohnehin Voraussetzung für eine eigene Cloud Lösung ist. Dieser Post geht die Schritte mit einem QNAP NAS (QVPN) durch. Als VPN Client verwende ich "Open VPN".   

## Einzelheiten auf dem QNAP NAS  

Nach dem anmelden an dem NAS (QNAP) im Suchfeld nach "VPN" ![suchen](../assets/images/69-1.png). Danach den QVPN Service installieren ("App Center"). Im Fenster "QVPN Service", links im vertikalen Menu auf "OpenVPN" klicken. Die ![Einstellungen](../assets/images/69-2.png) können übernommen werden. Einzig die Verschlüsselung ändere ich auf "AES 256-bit" das inzwischen so gut wie alle VPN Clients unterstützen. Die Einstellungen speichern über den Button "Übernehmen" am unteren Rand. Jetzt den Button "Konfigurationsdatei herunterladen" anklicken.  

Die Konfigurationsdatei "QNAPTS212.ovpn" wird nachher mit dem OpenVPN Client verwendet. Die externe IP Adresse (WAN-IP) des Routers hinter dem das NAS steht, ist in dieser Datei in der Zeile "Remote=" zu finden. D.h. wenn man von seinem Internet Service Provider eine neue IP erhält, muss diese dort eingetragen werden. Swisscom Privat Kunden haben diese Arbeit nicht. I.d.R. bleibt dort die IP über Jahre die gleiche.  

Die alternative ist ein "Dynamic DNS" Name, den man z.B. über [NoIP.com](https://www.noip.com/remote-access) erhält. Einfach beachten, dass wenn man die kostenlose Variante wählt, alle 30 Tage den Account bestätigen muss. Mir ist es daher die 24 Dollar pro Jahr wert, dass ich mir dafür nicht Zeit nehmen muss.  

Letzter Hinweis: Auf Grund der IPv4 Adressknappheit erhalten viele Kunden von Ihren ISP keine routbaren WAN-IP Adresse mehr. D.h. viele Kunden teilen sich 1 V4 Adresse, diese wird dann im Backbone des ISP in das Internet geroutet. Swisscom nennt das Verfahren ["CGNAT"](https://www.tuxone.ch/2015/12/ipv4-umstellung-auf-gcnat-bei-swisscom.html)Swisscom ist der einzige mir bekannte Anbieter, der den Kunden auf Anfrage auf eine vollwertige IP umstellt. Selbst bei den kleinsten DSL Verträgen.

## Internet-Router Weiterleitung einrichten  

Da die Standardeinstellung für Protokoll ("UDP") und Port ("1194") belassen wurden, wird die Weiterleitung dafür konfiguriert. Natürlich sollten Geräte im LAN die als Server (NAS / Printer / etc.) genutzt werden eine feste interne IP haben. Nachfolgend ein Bild wie die Einstellungen des Routers "Internet Box" der Firma Swisscom aussieht. Das NAS wird im Feld "Gerät" ausgewählt.  
![Bild](../assets/images/69-3.png)  

## Windows 10: OpenVPN Client einrichten  

Auf der ![Website](../assets/images/69-4.png) der OpenVPN Community rechts den Button auf der Linie "Windows 10 installer (NSIS)" anklicken. Die Datei kann unter 32 Bit und 64 Bit Windows installiert werden. Windows verlangt für die Installation einen Benutzer mit Administrator Rechten.  

Im Downloadverzeichnis liegt nun die Installationsdatei [openvpn-install-2.4.7-I607-Win10!](../assets/images/69-5.png)  

Die Installation kann durchgeklickt werden. Die Readme.txt sollte man lesen, technische Englisch vorausgesetzt. Danach über das Windows Menu "OpenVPN" starten. Da noch keine Konfiguration erstellt wurde, erhält man diesen [Hinweis](../assets/images/69-6.png).  Im SysTray wird nun das Icon (Monitor mit Schloss) angezeigt. Mit einem [Rechtsklick](../assets/images/69-7.png) kann nun die Konfigurationsdatei ("QNAPTS212.ovpn") geladen werden. Nach dem wegklicken der Bestätigung, kann man über einen weiteren Rechtsklick "verbinden" bzw. "trennen" anklicken, um die verschlüsselte VPN Verbindung zum NAS herzustellen.  


## Fazit  

VPN ist dank OpenVPN ein benutzerfreundlicher Netzwerkservice. Für Zugriff auf andere Netzwerke sollte es heute genauso wie HTTPS / IMAPS / etc. immer verwendet werden.  

# Quellen  

1. [QNAP: Wie wird QVPN 2.0 eingerichtet und verwendet?](https://www.qnap.com/de-de/how-to/tutorial/article/wie-wird-qvpn-2-0-eingerichtet-und-verwendet/)
2. [QNAP Turbo NAS User Manual: QVPN Service](http://docs.qnap.com/nas/4.3/cat2/en/index.html?qvpn.htm)  
3. [ThomasKrenn-Wiki: OpenVPN Grundlagen](https://www.thomas-krenn.com/de/wiki/OpenVPN_Grundlagen)  
4. [Openvpn Community Client download](https://openvpn.net/community-downloads/)
5. [Administrator.de: OpenVPN - Teil 1 - Installation, Konfiguration und erstellung der Zertifikate](https://administrator.de/wissen/openvpn-teil-1-installation-konfiguration-erstellung-zertifikate-73947.html)  
6. [Administrator.de: OpenVPN - Teil 1 - Installation, Konfiguration und erstellung der Zertifikate](https://administrator.de/wissen/openvpn-teil-1-installation-konfiguration-erstellung-zertifikate-73947.html)  
7. [Administrator.de: OpenVPN - Teil 2 - Installation, Konfiguration und erstellung der Zertifikate](https://administrator.de/wissen/openvpn-teil-2-konfiguration-74395.html)  
8. [Administrator.de: OpenVPN Server installieren auf pfSense Firewall, Mikrotik. DD-WRT oder GL.inet Router](https://administrator.de/wissen/openvpn-server-installieren-pfsense-firewall-dd-wrt-router-123285.html)  
9. [YT: QNAP: Explore QVPN 2.0: An in-depth guide for VPN server and client settings](https://www.youtube.com/watch?v=ErfHkA2jYXI)
10. [itmagazine.ch: Virtueller VPN-Router für Azure](https://www.itmagazine.ch/Artikel/70032/Virtueller_VPN-Router_fuer_Azure.html)
11. [Überblick der Anbieter von VPN Dienstleitern](https://thatoneprivacysite.net/)  

## Meta

Erstellt:		20. Oktober 2019  
Modifiziert:	20. Oktober 2019
