---  
title: "Markdown und Tabelle  "
date:  2020-06-21T5:34:30-04:00
categories:  
  - netzwerk  
tags:  
  - markdown  
  - tipp
---  

## Um was geht es?

Mit der Auszeichnungssrpache Markdown (GitHub) habe ich verschiedene Möglichkeiten Tabellen darzustellen. Optisch bietet Markdown wenig Möglichkeiten. Aber mit den W3C Sprachen (HTML / CSS) erreiche ich sehr viel mehr. Etwas Webdesign für Markdown.  

## 1. Markdown pur

Die Code Beispiele sind aus der GitHub Markdown Hilfe  

### Beispiel 1   

#### Code  

```
| First Header  | Second Header | Third Header  | Fourth Header |
| ------------- | ------------- | ------------- | ------------- |
| Content Cell  | Content Cell  | Content Cell  | Content Cell  |
| Content Cell  | Content Cell  | Content Cell  | Content Cell  |
| Content Cell  | Content Cell  | Content Cell  | Content Cell  |
| Content Cell  | Content Cell  | Content Cell  | Content Cell  |
```

#### Ausgabe  

| First Header | Second Header | Third Header | Fourth Header |
| ------------ | ------------- | ------------ | ------------- |
| Content Cell | Content Cell  | Content Cell | Content Cell  |
| Content Cell | Content Cell  | Content Cell | Content Cell  |
| Content Cell | Content Cell  | Content Cell | Content Cell  |
| Content Cell | Content Cell  | Content Cell | Content Cell  |

Der Titel einer Spalte wird durch Bindestriche von den Zellen mit Daten getrennt. Drei Bindestriche sind das Minium. Die Spaltenbreite wird automatisch gesetzt.  

### Beispiel 2  

#### Code  

 ```
\| First Header  | Second Header | Third Header  | Fourth Header |  
\| --- | --- | --- | --- |  
\| Content Cell  | Content Cell  | Content Cell  | Content Cell  |  
 ```

#### Ausgabe  

| First Header | Second Header | Third Header | Fourth Header |
| ------------ | ------------- | ------------ | ------------- |
| Content Cell | Content Cell  | Content Cell | Content Cell  |

Text kann auch als Block formatiert werden. Dafür verwendet man [Gravis](https://de.wikipedia.org/wiki/Gravis_(Typografie)#Darstellung_auf_dem_Computer): `  
Das Beispiel aus der GitHub Hilfedatei:

![NoText](../image/14-1.png)  

Markierungsmöglichkeiten sind dieselben wie in Markdown allgemein. * für kursiv, ** für fett, kann man auch kombinieren. Details dazu stehen in der [GitHub Helpdatei](https://help.github.com/en/articles/basic-writing-and-formatting-syntax#styling-text).

## HTML Tabelle in Markdown einbetten  

[Markdown HTML Tabelle - Unterseite](http://www.petergyger.net/netzwerk/014a-markdown-tabellen-erstellen-BSP/)

##   HTML mit CSS

Tabellen sollten mit CSS formatiert werden. Folgende HTML Attribute werden z.B. nicht mehr von HTML5 unterstützt:  
* bgcolor → CSS: background-color
* border → CSS: border
* cellpadding → CSS:padding
* cellspacing → CSS: border-spacing
* frame → CSS: border
* rules → CSS: border
* summary → Zusammenfassung_des_Tabelleninhalts 
* width

Die einzelnen HTML Elemente werden am einfachsten mit Klassen formatiert. "Klasse" kann man sich als Vorlage vorstellen, auf die im HTML Element verwiesen wird.  
Die einzelnen Tags können aber auch direkt formatiert werden. In dem Beispiel 1 wird der Zebra Look der Tabelle über das formatieren des Tags "TR" erreicht.  Der Tag "tr" wird hier zweifach definiert, was für einen CSS Laien verwirrend macht. Unter dem Strich geht es in diesem Post primär darum zu zeigen, was mit HTML und CSS in einer Markdown Datei erreichdet werden kann.  

Dieses CSS Verfahren wird [Pseudoklasse](https://wiki.selfhtml.org/wiki/CSS/Selektoren/Pseudoklasse) genannt. Das hier verwendete Element "nth-child" mit dem Wert "odd" kann man z.B. auf der [Mozilla Website](https://developer.mozilla.org/de/docs/Web/CSS/:nth-child) nachlesen. Im Beispeil unten hat es im CSS Abschnitt \<style type="text/css"> eine CSS Klasse namens ".zahl". Damit kann eine HTML Aufzählung (Tag OL / UL) über den Befehl \list-style anders formatiert werden. Dieser CSS [Artikel](https://css-tricks.com/almanac/properties/l/list-style/) listet die verschiedenen Möglichkeiten auf, wie Listen anders dargestellt werden können. Um eine Liste absteigend zu nummerieren und die Ziffern mit einer führenden Null (01 / 02 / etc.) mit der oben definierten CSS Klasse "zahl" darzustellen, muss das ol tag so aussehen:  

 ```\<ol reversed="reversed" class="zahl" > ```

Wenn der Google Font ["Space Mono"](https://google-webfonts-helper.herokuapp.com/fonts/space-mono?subsets=latin) initialisiert wurde, kann ich für die Aufzählung auch diese Schrift definieren:  

 ```\style="font-family: 'Space Mono';" ```

Die CSS Angaben sind hierarchisch organisiert. Grundlegende Angaben die für das ganze Repository ("Jeckyl Now" Build) gelten, stehen in der Datei "style.css". Diese werden ggf. überschrieben, wenn ich in einer MD Datei (Blogpost) zum gleichen HTML Tag Angaben mache. Kug (Kurz und gut): Wenn in der Datei "style.css" steht, dass der Tag H1 (Titel) grün sein soll, jedoch in einer MD Datei H1 ist rot definiert ist, dann wird in dieser Datei der Titel in rot angezeigt.  

Dasselbe gilt, wenn ich zu einem einzelnen Tag eine CSS Anweisung setze. Diese wird die globale und auch die CSS Anweisungen in der Datei selber überschreiben. Da die Stlye.css anhand der Endung als W3C (HTML / CSS / etc.) Datei von VS Code erkannt wird, kann ich dort auch mit den integrierten Tools und Modulen arbeiten. Z.B. um einen Farbcode auszuwählen.  
![NoText](../image/14-2.png)  

Die CSS Klasse die im Beispiel angegeben ist, wirkt für die nachfolgenden Beispiele weiter. D.h. der farbige Hintergrund der Titelzeile in Beispiel 2 und nachfolgend wird durch die CSS Befehle in Beispiel 1 bewirkt.  

### Beispiel 1  

#### Code

 ```
\<style type="text/css">  
      th {
        background-color: #666; 
        color: #fff;
      }
      tr {
        background-color: #fffbf0;
        color: #000;
      }
      tr:nth-child(odd) {
        background-color: #e4ebf2 ;
      }
      .zahl {
  list-style: square inside;
}      
\</style>  
\<table>  
  \<tr>  
    \<th>First </th>  
    \<th>Second</th>  
    \<th>Third</th>  
    \<th>Fourth</th>  
  \</tr>  
  \<tr>  
    \<td>Content Cell</td>  
    \<td>Content Cell</td>  
    \<td>Content Cell</td>  
    \<td>Content Cell</td>  
  \</tr>  
  \<tr>  
    \<td></td>  
    \<td></td>  
    \<td></td>  
    \<td></td>  
  \</tr>  
  \<tr>  
    \<td></td>  
    \<td></td>  
    \<td></td>  
    \<td></td>  
  \</tr>  
  \<tr>  
    \<td></td>  
    \<td></td>  
    \<td></td>  
    \<td></td>  
  \</tr>  
\</table>  
 ```

#### Ausgabe

<style type="text/css">
      table {width: 95%;}
      th {
        background-color: #666; 
        color: #fff;
      }
      tr {
        background-color: #fffbf0;
        color: #000;
      }
      tr:nth-child(odd) {
        background-color: #e4ebf2 ;
      }
      .zahl {
        list-style: square inside;
      }      
</style>
<table>
  <tr>
    <th>First</th>
    <th>Second</th>
    <th>Third</th>
    <th>Fourth</th>
  </tr>
  <tr>
    <td>Content Cell</td>
    <td>Content Cell</td>
    <td>Content Cell</td>
    <td>Content Cell</td>
  </tr>
  <tr>
    <td>Content Cell</td>
    <td>Content Cell</td>
    <td>Content Cell</td>
    <td>Content Cell</td>
  </tr>
</table>  

### Beispiel 2 Colspan mit individueller Breite der Spalten  

#### Code  

 ```
\<table style="border-collapse: collapse;" border="0"><colgroup><col style="width: 42px;" /><col style="width: 561px;" /><col style="width: 111px;" /><col style="width: 75px;" /><col style="width: 75px;" /><col style="width: 75px;" /></colgroup>  
    \<tr style="height: 21px;">  
        \<td>1</td>  
        \<td>2</td>  
        \<td>3</td>  
        \<td>4</td>  
        \<td>5</td>  
        \<td>6</td>  
    \</tr>  
    \<tr style="height: 21px;">  
        \<td></td>  
        \<td>Acer</td>  
        \<td>Asus</td>  
        \<td>Dell</td>  
        \<td>Huawei</td>  
        \<td>Thinkpad</td>  
    \</tr>  
\</table>  
 ```

#### Ausgabe   

<table style="border-collapse: collapse;" border="0"><colgroup><col style="width: 42px;" /><col style="width: 561px;" /><col style="width: 111px;" /><col style="width: 75px;" /><col style="width: 75px;" /><col style="width: 75px;" /></colgroup>
    <tr style="height: 21px;">
        <td>1</td>
        <td>2</td>
        <td>3</td>
        <td>4</td>
        <td>5</td>
        <td>6</td>
    </tr>
    <tr style="height: 21px;">
        <td></td>
        <td>Acer</td>
        <td>Asus</td>
        <td>Dell</td>
        <td>Huawei</td>
        <td>Thinkpad</td>
    </tr> 
</table>

### Beispiel 3: Tabellenzellen direkt formatiert

#### Code  

 ```
\<table>  
\<tbody valign="top">  
    \<tr style="height: 21px;">  
        \<td style="padding-left: 5px; padding-right: 5px; border-top: none; border-left: none; border-bottom: solid 1.0pt; border-right: none;"> </td>  
        \<td style="padding-left: 5px; padding-right: 5px; border-top: none; border-left: none; border-bottom: solid 1.0pt; border-right: none;" valign="bottom">Klang</td>  
        \<td style="padding-left: 5px; padding-right: 5px; border-top: none; border-left: none; border-bottom: solid 1.0pt; border-right: none;" valign="bottom">Pynyin</td>  
        \<td style="padding-left: 5px; padding-right: 5px; border-top: none; border-left: none; border-bottom: solid 1.0pt; border-right: none;" valign="bottom">traditionell</td>  
        \<td style="padding-left: 5px; padding-right: 5px; border-top: none; border-left: none; border-bottom: solid 1.0pt; border-right: none;" valign="bottom">simpel</td>  
        \<td style="padding-left: 5px; padding-right: 5px; border-top: none; border-left: none; border-bottom: solid 1.0pt; border-right: none;" valign="bottom">Zeichen</td>  
    \</tr>  
    \<tr style="height: 21px;">  
        \<td style="padding-left: 5px; padding-right: 5px; border-top: none; border-left: none; border-bottom: none; border-right: solid 0.5pt;">1</td>  
        \<td style="padding-left: 5px; padding-right: 5px; border-top: none; border-left: none; border-bottom: none; border-right: solid 0.5pt;" valign="bottom"><a href="https://de.wikipedia.org/wiki/T%C3%B6ne_des_Hochchinesischen">Hoch</a></td>  
        \<td style="padding-left: 5px; padding-right: 5px; border-top: none; border-left: none; border-bottom: none; border-right: solid 0.5pt;" valign="bottom">dì yī shēng</td>  
        \<td style="padding-left: 5px; padding-right: 5px; border-top: none; border-left: none; border-bottom: none; border-right: solid 0.5pt;" valign="bottom">第一聲</td>  
        \<td style="padding-left: 5px; padding-right: 5px; border-top: none; border-left: none; border-bottom: none; border-right: solid 0.5pt;" valign="bottom">第一声</td>  
        \<td style="padding-left: 5px; padding-right: 5px; border: none;" valign="bottom">¯</td>  
    \</tr>  
\</tbody>  
\</table>  
 ```
 
#### Ausgabe   

<table>
<tbody valign="top">
    <tr style="height: 21px;">
        <td style="padding-left: 5px; padding-right: 5px; border-top: none; border-left: none; border-bottom: solid 1.0pt; border-right: none;"> </td>
        <td style="padding-left: 5px; padding-right: 5px; border-top: none; border-left: none; border-bottom: solid 1.0pt; border-right: none;" valign="bottom">Klang</td>
        <td style="padding-left: 5px; padding-right: 5px; border-top: none; border-left: none; border-bottom: solid 1.0pt; border-right: none;" valign="bottom">Pynyin</td>
        <td style="padding-left: 5px; padding-right: 5px; border-top: none; border-left: none; border-bottom: solid 1.0pt; border-right: none;" valign="bottom">traditionell</td>
        <td style="padding-left: 5px; padding-right: 5px; border-top: none; border-left: none; border-bottom: solid 1.0pt; border-right: none;" valign="bottom">simpel</td>
        <td style="padding-left: 5px; padding-right: 5px; border-top: none; border-left: none; border-bottom: solid 1.0pt; border-right: none;" valign="bottom">Zeichen</td>
    </tr>
    <tr style="height: 21px;">
        <td style="padding-left: 5px; padding-right: 5px; border-top: none; border-left: none; border-bottom: none; border-right: solid 0.5pt;">1</td>
        <td style="padding-left: 5px; padding-right: 5px; border-top: none; border-left: none; border-bottom: none; border-right: solid 0.5pt;" valign="bottom"><a href="https://de.wikipedia.org/wiki/T%C3%B6ne_des_Hochchinesischen">Hoch</a></td>
        <td style="padding-left: 5px; padding-right: 5px; border-top: none; border-left: none; border-bottom: none; border-right: solid 0.5pt;" valign="bottom">dì yī shēng</td>
        <td style="padding-left: 5px; padding-right: 5px; border-top: none; border-left: none; border-bottom: none; border-right: solid 0.5pt;" valign="bottom">第一聲</td>
        <td style="padding-left: 5px; padding-right: 5px; border-top: none; border-left: none; border-bottom: none; border-right: solid 0.5pt;" valign="bottom">第一声</td>
        <td style="padding-left: 5px; padding-right: 5px; border: none;" valign="bottom">¯</td>
    </tr>
</tbody>
</table>  

### Beispiel 4

Die Hintergrund Farbe kann man auch mit dem Befehl "rgba" festlegen. Diese Farbe ist transparent. Farbdefinitionen über RGB bestehen ja aus den drei Werten (Red / Green / Blue). Der vierte Wert des RGBA Befehls definiert den Alphakanal. Dieser definiert die Deckkraft der 3 Farbwerte.  
Details hier auf ["css-tricks.com"](https://css-tricks.com/rgba-browser-support/)  

#### Code  

 ```
<style type="text/css">
    table {
        font-family: 'Cascadia Code', 'Fira Code', Consolas, 'Courier New', Courier, monospace;
        font-size: 13px;
        white-space: nowrap;
    }

    thead th {
        background-color: rgba(255, 165, 0, 0.62)
    }

    tbody tr td {
        background-color: #f7f7f7
    }
</style>
<table>
    <thead>
        <tr>
            <th>Spalte Eins</th>
            <th>Spalte Zwei</th>
            <th>Spalte Drei</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td rowspan="2">Class<br>Zeile 1 </td>
            <td>brown fox jumps over the lazy dog</td>
            <td>Franz jagt im komplett verwahrlosten Taxi quer durch Bayern</td>
        </tr>
        <tr>
            <td>brown fox jumps over the lazy dog</td>
            <td>Franz jagt im komplett verwahrlosten Taxi quer durch Bayern</td>
        </tr>
        <tr>
            <td rowspan="2">Class<br>Zeile 2 </td>
            <td>brown fox jumps over the lazy dog</td>
            <td>Franz jagt im komplett verwahrlosten Taxi quer durch Bayern</td>
        </tr>
        <tr>
            <td>brown fox jumps over the lazy dog</td>
            <td>Franz jagt im komplett verwahrlosten Taxi quer durch Bayern</td>
        </tr>
        <tr>
            <td rowspan="2">Class<br>Zeile 3 </td>
            <td>brown fox jumps over the lazy dog</td>
            <td>Franz jagt im komplett verwahrlosten Taxi quer durch Bayern</td>
        </tr>
        <tr>
            <td>brown fox jumps over the lazy dog</td>
            <td>Franz jagt im komplett verwahrlosten Taxi quer durch Bayern</td>
        </tr>
    </tbody>
</table>
```

#### Ausgabe   

<table>
    <thead>
        <tr>
            <th>Spalte Eins</th>
            <th>Spalte Zwei</th>
            <th>Spalte Drei</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td rowspan="2">Class<br>Zeile 1 </td>
            <td>brown fox jumps over the lazy dog</td>
            <td>Franz jagt im komplett verwahrlosten Taxi quer durch Bayern</td>
        </tr>
        <tr>
            <td>brown fox jumps over the lazy dog</td>
            <td>Franz jagt im komplett verwahrlosten Taxi quer durch Bayern</td>
        </tr>
        <tr>
            <td rowspan="2">Class<br>Zeile 2 </td>
            <td>brown fox jumps over the lazy dog</td>
            <td>Franz jagt im komplett verwahrlosten Taxi quer durch Bayern</td>
        </tr>
        <tr>
            <td>brown fox jumps over the lazy dog</td>
            <td>Franz jagt im komplett verwahrlosten Taxi quer durch Bayern</td>
        </tr>
        <tr>
            <td rowspan="2">Class<br>Zeile 3 </td>
            <td>brown fox jumps over the lazy dog</td>
            <td>Franz jagt im komplett verwahrlosten Taxi quer durch Bayern</td>
        </tr>
        <tr>
            <td>brown fox jumps over the lazy dog</td>
            <td>Franz jagt im komplett verwahrlosten Taxi quer durch Bayern</td>
        </tr>
    </tbody>
</table>

HSLA ist eine weitere Variante

<style type="text/css">
  td {
        background-color: hsla(120, 100%, 50%, 0.25);
    }
</style> 
<table>
    <tr>
        <td>brown fox jumps over the lazy dog</td>
        <td>Franz jagt im komplett verwahrlosten Taxi quer durch Bayern</td>
    </tr>
</table>

## Formatierung Text ohne Tabelle

Die ["Utility Classes"](https://mmistakes.github.io/minimal-mistakes/docs/utility-classes/) von Kramedown werden aktuell in keinem meiner Browser interpretiert. Ausgenomen die Textausrichtung. Hier eine Auswahl zum selber testen.

**Text ausrichten**  

Transform text with capitalization classes via HTML:

<p class="lowercase">Lowercased text.</p>
<p class="uppercase">Uppercased text.</p>
<p class="capitalize">Capitalized text.</p>
<p class="truncate">Truncated text.</p>
<p class="small">Small text.</p>

Or with Kramdown:

Franz jagt im komplett verwahrlosten Taxi quer durch Bayern
{: .text-lowercase}

Franz jagt im komplett verwahrlosten Taxi quer durch Bayern
{: .text-uppercase}

Franz jagt im komplett verwahrlosten Taxi quer durch Bayern
{: .text-capitalize}

**Textformatierung**  

Franz jagt im komplett verwahrlosten Taxi quer durch Bayern
{: .text-left}

Franz jagt im komplett verwahrlosten Taxi quer durch Bayern
{: .text-center}

Franz jagt im komplett verwahrlosten Taxi quer durch Bayern
{: .text-right}

Franz jagt im komplett verwahrlosten Taxi quer durch Bayern
{: .text-justify}

Franz jagt im komplett verwahrlosten Taxi quer durch Bayern
{: .text-nowrap}

**Buttons**  

```<a href="#" class="btn btn--primary">Link Text</a>```  
<a href="#" class="btn btn--primary">Link Text</a>  

```<a href="#" class="btn btn--success">Link Text</a>```    
<a href="#" class="btn btn--success">Link Text</a>  

```<a href="#" class="btn btn--warning">Link Text</a>```    
<a href="#" class="btn btn--warning">Link Text</a>  

```<a href="#" class="btn btn--danger">Link Text</a>```    
<a href="#" class="btn btn--danger">Link Text</a>  

```<a href="#" class="btn btn--info	">Link Text</a>```    
<a href="#" class="btn btn--info	">Link Text</a>  

```<a href="#" class="btn btn--inverse">Link Text</a>```  
<a href="#" class="btn btn--inverse">Link Text</a>  

```<a href="#" class="btn btn--light-outline">Link Text</a>```  
<a href="#" class="btn btn--light-outline">Link Text</a>  

**Mit der Notice Class können verschiedenfarbige Hintergrundfarbe festgelegt werden. Was mir mit CSS nicht gelang**  

Franz jagt im komplett verwahrlosten Taxi quer durch Bayern
{: .notice}

Franz jagt im komplett verwahrlosten Taxi quer durch Bayern
{: .notice--primary}

Franz jagt im komplett verwahrlosten Taxi quer durch Bayern
{: .notice--info}

Franz jagt im komplett verwahrlosten Taxi quer durch Bayern
{: .notice--warning}

Franz jagt im komplett verwahrlosten Taxi quer durch Bayern
{: .notice--success}

Franz jagt im komplett verwahrlosten Taxi quer durch Bayern
{: .notice--danger}


## Fazit

Mit dem ["HTML Table Style Generator"](http://tablestyler.com) von Eli Geske können auch "nicht Webentwickler" wie ich sich schöne CSS Tabellen Design zusammen klicken. Danke an dieser Stelle an Eli Geske für den tollen Webservice!  

Mit der Auszeichnungssrpache Markdown (GitHub) habe ich verschiedene Möglichkeiten Tabellen darzustellen. Optisch bietet Markdown wenig Möglichkeiten. Aber mit den W3C Sprachen (HTML / CSS) erreiche ich sehr viel mehr. Etwas Webdesign für Markdown.  

# Quellen  

1. [GitHub Help:  Organizing information with tables](https://help.github.com/en/articles/organizing-information-with-tables)  

2. [GitHub Help:  Organizing information with tables](https://help.github.com/en/articles/basic-writing-and-formatting-syntax)  

3. [Daringfireball.net:HTML](https://daringfireball.net/projects/markdown/syntax#html)  

4. [Tables Online Generator](https://www.tablesgenerator.com/html_tables)  

5. [SelfHTML Aufbau einer Tabelle](https://wiki.selfhtml.org/wiki/HTML/Tabellen/Aufbau_einer_Tabelle)  

6. [css-tricks.com: A Complete Guide to the Table Element](https://css-tricks.com/complete-guide-table-element/)  

7. [W3C Markdown Syntax](https://www.w3.org/community/markdown/wiki/Syntax)  

8. [TU-Dresden: Markdown - Eine Übersicht - Tabellen](https://elvis.inf.tu-dresden.de/wiki/index.php/Markdown_-_Eine_%C3%9Cbersicht#Fett-_und_Kursivdarstellung)  


## Meta

Erstellt:		          21. Juni 2020  
Modifiziert:	        8. September 2020  

