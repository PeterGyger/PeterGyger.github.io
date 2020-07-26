---
title: "Internetspeed und Firewall"
date: 2019-06-20T15:34:30-04:00
categories:
  - netzwerk
tags:
  - hardware
  - firewall
---

Eine Binsenwahrheit: Die vom Anwender erlebte Internetgeschwindigkeit ist das Resultat des Zusammenspiels verschiedener Bestandteile. Der Anschluss in der Wand ist der "Demarcation Point", wo die Zuständigkeit des ISP endet. Hier ist die Rede davon, was danach kommt.  

# Problem  

Ein Anschluss wurde von DSL (VDSL) auf Glasfaser (FTTH) umgestellt. Entsprechend den Möglichkeiten wurde der Vertrag mit dem ISP geändert, so dass man die 1 GB (up / down) nutzen konnte. Die Geschwindigkeit war danach effektiv besser als vorher. Jedoch weit ab, von dem was man mit dem Vertrag und der Technik erreichen kann. Reprodzierbar auf 3 Computern über hochwertige CAT6a Ethernetkabel getestet.  

# Lösung  

Die Firewall war der Flaschenhals. Nachdem alle Netzwerkbestandteile im LAN geprüft waren, ergab das Datenblatt des nicht mehr so frischen und eher günstigen Firewall das die Leistung auf 300 MBit limitiert war. Der Zuriff ohne Firewall bestätigte den Sachverhalt. Ärgerlich, dass ich nicht am Anfang auch die Firewall in Betracht gezogen habe. Mir war nicht bewusst, dass auch dieser Aspekt der Wirkungskette zu einem Flaschenhals werden kann.  

## Meta

Erstellt:		20. Juni 2019  
Modifiziert:	20. Juni 2019  
