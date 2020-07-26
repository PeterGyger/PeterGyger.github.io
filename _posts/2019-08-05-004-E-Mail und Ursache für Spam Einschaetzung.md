---
title: "E-Mail und Ursache für Spam Einschätzung"
date: 2019-08-05T15:34:30-04:00
categories:
  - netzwerk
tags:
  - email
  - sicherheit
---

Ein neuer E-Mail Kontakt meldete zurück, dass meine E-Mails in seinem Spamordner abgelegt werden. Im Betreff mit dem Stichwort "Spam" gekennzeichnet. Auf allen Geräten

## Vorgehen

Der E-Mail Header wertete ich mit dem Online Service von [MXToolbox.com](https://mxtoolbox.com/EmailHeaders.aspx](https://mxtoolbox.com/EmailHeaders.aspx) aus.  
Das Feld X-Spam-Flag hat den Wert "Yes". Andernfalls wird es nicht im Header eingetragen. Dieses Feld erhielt den Wert "Yes", weil der Score (Anzahl Verdachtsmomente) zu hoch war:  
' Content analysis details: (7.3 points, 5.0 required)  

Das Feld "X-Spam-Report" lieferte den ausführlichen, textuellen Hinweis für den Grund:  

``
Spam detection software, running on the system "mail-spamd0x.xxxx.lan", has identified this incoming email as possible spam. If you have any questions, see the administrator of that system for details. Content analysis details: (7.3 points, 5.0 required) pts rule name description ---- ---------------------- -------------------------------------------------- -0.0 RCVD_IN_xxxxx_NONE RBL: Sender listed at http://www.xxxxx.org/, no trust [aaa.bbb.ccc.dddd listed in list.xxxxx.xxxxx] 0.1 URIBL_SBL_A Contains URL's A record listed in the Spamhaus SBL blocklist [URIs: domain.net] 5.0 URIBL_SBL Contains an URL's NS IP listed in the Spamhaus SBL blocklist [URIs: domain.net] 0.0 SPF_NONE SPF: sender does not publish an SPF Record 0.0 SPF_HELO_NONE SPF: HELO does not publish an SPF Record 0.0 HTML_IMAGE_RATIO_08 BODY: HTML has a low ratio of text to image area 0.0 HTML_MESSAGE BODY: HTML included in message 1.0 HTML_IMAGE_ONLY_16 BODY: HTML: images with 1200-1600 bytes of words 0.1 KAM_LAZY_DOMAIN_SECURITY Sending domain does not have any anti-forgery methods 1.0 T_REMOTE_IMAGE Message contains an external image 
`` 

Der Schlüsselsatz lautet hier "A record listed in the Spamhaus SBL blocklist". Danach folgt "NS IP listed in the Spamhaus SBL blocklist". NS seht für Name Server. D.h. der Name Server (DNS) der Quell IP in der E-Mail ist auf der SBL-Liste von Spamhaus.org. Spamhaus hat neben der normalen Blackliste zwei zusätzliche:  
* ["The Policy Block List" (PBL)](https://www.spamhaus.org/pbl/)  
* ["Spamhaus Block List" (SBL)](https://www.spamhaus.org/sbl/)  

Es hat noch eine dritte Liste, diese ist jedoch nicht relevant (XBL (Spamhaus Exploits Block List)). Diese können über das sogenannte [ZEN Paket](https://www.spamhaus.org/zen/) eingesetzt werden.  

Man nimmt die IP Adresse aus dem Mail-Header (Feld "X-Originating-Ip") und prüft über den [Heise Webservice](https://www.heise.de/netze/tools/spam-listen/), ob sie auf einer der verschiedenen Blacklists aufgeführt ist. Diesen "Lookup" mit der IP kann auch direkt auf [Spamhaus.org] (https://www.spamhaus.org/lookup/) gemacht werden, da Spamhaus.org einer der grossen Firmen ist. Dort können die Listen PBL / SBL können nur mit einer IP geprüft werden.  

Die Abkürzung geht wieder über einen Webservice von MXToolbox.com namens ["Blacklist"](https://mxtoolbox.com/blacklists.aspx). Dort steht bei einem der drei NS eine rote Marierung und in der Spalte "Blacklist" steht "Spamhaus ZEN". 

Hinweis:  
1. Felder im E-Mail Header, welche nicht zum Standard (RFC 5322) gehören, beginnen mit dem Prefix "X-". Definiert über RFC 822, Punkt  "4.7.4.  EXTENSION-FIELD".  
2. In seiner DNS Zone ein [SPF (Sender Policy Framework)](https://de.wikipedia.org/wiki/Sender_Policy_Framework) Record einzurichten, soll eine effiziente Prävention sein, dass man nicht auf eine Blacklist gesetzt wird.

### Fazit

Das Problem ist meinem Hoster gemeldet. Mal sehen wie lange es dauert.


## Quellen

* [FAQ: E-Mail-Header lesen und verstehen](https://th-h.de/net/usenet/faqs/headerfaq/)
* [E-Mail Header Definition RFC 5322](https://tools.ietf.org/html/rfc5322)
* [Standard for ARPA Internet Text Messages RFC 822](https://tools.ietf.org/html/rfc822)
* [Erklärung wie ein Spamfilter funktioniert -EN)](https://campus.barracuda.com/product/cloudgenfirewall/doc/48202698/spam-filter/)
* [Internet E-mail address format (RFC 822) explained ](http://jkorpela.fi/rfc/822addr.html)
* [Spam tagging explained](https://community.jisc.ac.uk/library/janet-services-documentation/spam-tagging-explained)
* [litmus.com: How does each spam filter score emails?](https://help.litmus.com/article/205-how-does-each-spam-filter-score-emails)  

## Meta

Erstellt:		5. August 2019
Modifiziert:	5. August 2019
