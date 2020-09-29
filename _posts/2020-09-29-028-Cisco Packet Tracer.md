---
title: "Cisco Packet Tracer"
date: 2020-09-25T5:31:30-04:00
categories:
  - netzwerk
tags:
  - cisco
  - simulation
---

Cisco Packet Tracer (CPT) ist eine Netzwerksimuation, welche von Dennis Frezzo für Cisco entwickelt wurde. Er lässt die verschiedensten Geräte wie Router, Computer, Switches usw. konfigurieren. Protokolle der OSI Layer 2 bis 4 inklusive der Routing Protokolle können simuliert und analysiert werden. Packet Tracer läuft unter Mac OS, Linux und Windows. 

GSN3 ist ein anderes bekanntes Programm dieser Kategorie. Es ist eine Emulation. D.h. das was die IOS Software in der Realität kann, kann man auch in der Emulation nachspielen.  

Einer der wichtigsten Unterschiede ist, dass im Packet Router die Cisco Geräte dabei sind. Keine Images welche nachgeladen werden müssen. Was anderseits auch eine Limitation auf einiger Geräte mit sich bringt.  

## Praxis

Die Internetsuchmaschinen findet u.a. auf YouTube diverse Infos. Mir persönlich hat die YouTube [Playlist](https://www.youtube.com/playlist?list=PLhjmGqgdpbuDc3kfLDOahSQFVnUjej0e6) des Kanals "local-IT-Partner" sehr gut gefallen. In drei Videos wird von der Installation über DNS, DHCP und Routing das Thema erklärt.  

Zu beachten ist, dass die aktuelle Software Gigabit Ethernet NICs und nicht mehr Fast Ethernet (10/100) hat. D.h. man im Internet ein nicht mehr aktuelles Tutorial durchspielt und dort steht das CLI Kommando `interface fastethernet0/1`  dann ist einzugeben ìnterface GigabitEthernet0/1  

In der Konsole kann man sich den Typ der NIC mit `show ip int br`  anzeigen.

# Quellen  

1. [Cisco Networking Academy: Cisco Packet Tracer download](https://www.netacad.com/courses/packet-tracer)
2. [Cisco Networking Academy: Introduction to Packet Tracer](https://www.netacad.com/courses/packet-tracer/introduction-packet-tracer)
3. [Flackbox: Free Cisco CCNA Lab Guide](https://www.flackbox.com/cisco-ccna-lab-guide)
4. [Ultimate Guide to Packet Tracer](https://www.itprc.com/packet-tracers/)
5  [Free Cisco CCNA 200-301 lab exercises, and How to Install Packet Tracer](https://www.youtube.com/watch?v=E4XQb-xWYRU)
6. [YouTube: David Bombal - Packet Tracer: CCNA Exam labs](https://www.youtube.com/playlist?list=PLhfrWIlLOoKM3niunUBTLjOR4gMt_uR_a)

## Meta

Erstellt:		29. September 2020  
Modifiziert:	29. September 2020