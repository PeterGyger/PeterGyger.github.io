---  
title: "Markdown und Tabelle - Unterseite HTML ohne CSS"
date:  2020-06-21T5:34:30-04:00
categories:  
  - netzwerk  
tags:  
  - markdown  
  - tipp
---  

## HTML Tabelle in Markdown einbetten  

Unter Quellen Punkt 3 erläutert der Erfinder von Markdown - John Gruber - auf seiner Website Daringfireball, wie weit die Unterstützung von HTML / CSS in Markdown geht. VS Code kann den HTML Code in einer Markdown Datei nicht prüfen. D.h. wenn Fehler auftreten, kopiere ich den HTML Teil in eine HTML Datei und debuge sie mit VS Code.  

HTML kennt abschliessend folgende Elemente für eine Tabelle:  
- table (die Tabelle selbst)  
- caption (die Tabellenüberschrift)  
- thead, tbody, tfoot (Zeilengruppen)  
- colgroup, col (Spaltengruppen)  
- tr (Tabellenzeilen)  
- th / td (Tabellenzellen)  

Der Zebralook der Beispiele entsteht dadurch, dass weiter unten über CSS der TR Tag entsprechend konfiguriert wurde. Natürlich wirkt sich der Code auf alle TR Tags in diesem Dokument aus.  

### Beispiel 1: *Eine einfache HTML Tabelle*  

Die Titel der Spalten (First / Second / ...) werden von Markdown automatisch dunkel eingefärbt, wenn man das HTML Tag "th" verwendet.  

#### Code 

 ```
\<table>  
  \<tr>  
    \<th>First</th>  
    \<th>Second</th>  
    \<th>Third</th>  
    \<th>Fourth</th>  
  \</tr>  
  \<tr>  
    \<td>  Content Cell</td>  
    \<td>  Content Cell</td>  
    \<td>  Content Cell</td>  
    \<td>  Content Cell</td>  
  \</tr>  
  \<tr>  
    \<td>  Content Cell</td>  
    \<td>  Content Cell</td>  
    \<td>  Content Cell</td>  
    \<td>  Content Cell</td>  
  \</tr>  
  \<tr>  
    \<td>  Content Cell</td>  
    \<td>  Content Cell</td>  
    \<td>  Content Cell</td>  
    \<td>  Content Cell</td>  
  \</tr>  
  \<tr>  
    \<td>  Content Cell</td>  
    \<td>  Content Cell</td>  
    \<td>  Content Cell</td>  
    \<td>  Content Cell</td>  
  \</tr>  
\</table>  
 ```

#### Ausgabe  

<table>
  <tr>
    <th>First </th>
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


### Beispiel 2: *Eine HTML Tabelle zusätzlich mit den Elementen "Kopf", "Inhalt" und "Fuss"*  

#### Code 

 ```
\<table>  
    \<thead>  
        \<tr>  
          \<th>Head</th>  
        \</tr>  
    \</thead>  
    \<tbody>  
        \<tr>  
          \<td>Content Cell</td>  
          \<td>Content Cell</td>  
          \<td>Content Cell</td>  
          \<td>Content Cell</td>  
        \</tr>  
    \</tbody>  
    \<tfoot>  
        \<tr>  
          \<td>Foot</td>  
        \</tr>  
    \</tfoot>  
\</table>  
 ```

#### Ausgabe  

<table>  
    <thead>  
        <tr>  
          <th>Head</th>  
        </tr>  
    </thead>  
    <tbody>  
        <tr>  
          <td>Content Cell</td>  
          <td>Content Cell</td>  
          <td>Content Cell</td>  
          <td>Content Cell</td>  
        </tr>  
    </tbody>  
    <tfoot>  
        <tr>  
          <td>Foot</td>  
        </tr>  
    </tfoot>  
</table>  


### Beispiel 3:  *Mit dem Element "colspan" können Zellen zu einer zusammengefasst werden*  

#### Code  
 
 ```
\<table>  
    \<thead>  
        \<tr>  
          \<th>Head</th>  
        \</tr>  
    \</thead>  
    \<tbody>  
        \<tr>  
          \<td colspan="3">Content Cell 1</td>  
          \<td>Content Cell 4</td>  
        \</tr>  
    \</tbody>  
    \<tfoot>  
        \<tr>  
          \<td>Foot</td>  
        \</tr>  
    \</tfoot>  
\</table>  
 ```

#### Ausgabe  

<table>  
    <thead>  
        <tr>  
          <th>Head</th>  
        </tr>  
    </thead>  
    <tbody>
        <tr>  
          <td>Content Cell</td>  
          <td>Content Cell</td>  
          <td>Content Cell</td>  
          <td>Content Cell</td>  
        </tr>    
        <tr>  
          <td colspan="3">Content Cell 1</td>  
          <td>Content Cell 4</td>  
        </tr>  
    </tbody>  
    <tfoot>  
        <tr>  
          <td>Foot</td>  
        </tr>  
    </tfoot>  
</table>  

### Beispiel 4: Mit dem Element "rowspan" können Spalten zusammengefasst werden.  

#### Code 

 ```
\<table>  
    \<thead>  
        \<tr>  
          \<th>Head\</th>  
        </tr>  
    \</thead>  
    \<tbody>
        \<tr>  
          \<td rowspan="2">Content Cell Row 1\</td>  
          \<td>Content Cell</td>  
          \<td>Content Cell</td>  
          \<td>Content Cell</td>  
        \</tr>  
        \<tr>  
          \<td>Content Cell</td>  
          \<td>Content Cell</td>  
          \<td>Content Cell</td>  
          \<td>Content Cell</td>  
        \</tr>    
    \</tbody>  
    \<tfoot>  
        \<tr>  
          \<td>Foot</td>  
        \</tr>  
    \</tfoot>  
\</table>  
 ```

#### Ausgabe

<table>  
    <thead>  
        <tr>  
          <th>Head</th>  
        </tr>  
    </thead>  
    <tbody>
        <tr>  
          <td rowspan="2">Content Cell Row 1</td>  
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
    </tbody>  
    <tfoot>  
        <tr>  
          <td>Foot</td>  
        </tr>  
    </tfoot>  
</table>  


[Markdown HTML Tabelle - Hauptseite](http://www.petergyger.net/netzwerk/014-markdown-tabellen-erstellen/)

## Meta

Version:    1.5
Erstellt:		21. April 2019  
Modifiziert:	10. September 2020
