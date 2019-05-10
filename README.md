Dokumentation 
=============

### Übersicht
***

* 01 - [K1](#01---K1)
* 02 - [K2](#02---K2)
* 03 - [K3](#03---K3)
* 04 - [Vagrant Befehle](#04---Vagrant-Befehle)
* 05 - [Vagrant Boxen](#05---Vagrant-Boxen)
* 06 - [Firewall Konfig](#06---firewall-konfig)
* 07 - [Reverse Proxy](#07---Reverse-Proxy)
* 08 - [Testfälle](#08---Testfälle)


### 01 - K1
***


Die nötige Software, den Git-Hub Account (gitaccoutn) und den SSH-Key wurde alles bereits für LB2 installiert/erstellt.


### 02 - K2
***

### Persönlicher Wissenstand


Docker kannte ich vor diesem Modul nur ganz wenig. Mein ehemaliger Oberstift hat mir Docker zwar mal kurz erklärt, jedoch habe ich mich nie weiter darin vertieft oder arbeiten damit erledigt. Ich weiss das Container immer mehr und mehr verwendet werden, und bei alltägliche diensten wie z.B. Gmail vorkommen.
Um mein Wissenstand ein wenig aufzurüsten, habe ich vor allem zusätzlich zum Unterricht noch Youtube Videos angeschaut, welche die Grundlagen erklären.



### 03 - K3
***

## Geplante Umgebung

Für die LB3 habe ich mir vorgenommen, nichts allzu Kompliziertes zu erstellen, da ich aus meiner Sicht zu wenig Erfahrung und Wissen in diesem Bereich habe, um ein kompliziertes Projekt in dieser Zeit zu realisieren.
Das Ziel war es, als Backend eine MySQL Datenbank zu erstellen, welche dann über das Frontend, Webserver, verwaltet werden kann. Um das ganze einfacher zu testen wird ein persistentes Volume erstellt. Diverse Sicherheitsmassnahmen und ein Monitoring wird auch noch umgesetzt.

### Docker Commands

| Befehl           |Beschreibung                                                                                   |
| -----------------|:---------------------------------------------------------------------------------------------:|
| Docker run       |Startet neuen Container - Der Befehl bietet unzählige Optionen und Parameter für Konfiguration |
| Docker run -it ubuntu /bin/bash       |Startet einen Container mit einer interaktiven Shell                      |
| Docker run -d ubuntu touch /tmp/lok      |Startet einen Container im Hintergrund und legt eine Datei an          |                     
| Docker ps        |Gibt einen Überblick über alle aktuellen Container                                             | 
| Docker ps -a     |Aktive und gestoppte Container anzeigen (All)                                                  | 
| Docker container ls -q |Gibt die ID aller laufenden Container an.                                                |
| Docker images    |Gibt Liste von lokalen Images aus (Repository-Name, Tag-Name, und Grösse)                      | 
| Docker rm        |Löscht einen oder mehrere Container. Gibt ID's aller Erfolgreich gelöschten Container zurück   | 
| Docker rmi       |Löscht das angegebene Image. Diese werden durcgh ID oder Tag-Name spezifiziert.                |
| Docker start     |Startet einen oder mehrere Container, welche gestoppt wurden (Nur starten nicht erstellen).    |
| Docker stop      |Stoppt einen oder mehrere Container(Herunterfahren).                                           |
| Docker kill      |Der Container wird sofort gestoppt und anschliessend gelöscht.                                 |
| Docker logs      |Gibt die Logs für einen Container aus.                                                         |
| Docker inspect   |Gibt umfangreiche Info über Container und Image(Konfigurationen, Netzwerkeinstellungen etc.)   |
| Dokcer diff      |Gibt Änderungen am Dateisystem an, gegenüber dem Image welches verwendet wurde.                |
| Docker top       |Gibt die aktuell laufenden Prozesse an(Task Manager).                                          |
| Docker build -t "name" |Erstellt Image aus dem Dockerfile im Verzeichniss                                        |
| Docker login     |Mit Docker Credentials in dieser CLI Situng anmelden                                           |
| Docker stack ls  |Zeigts Stacks oder Apps an.                                                                    |
| Docker stack rm "appname" |Entfernt eine App.                                                                    |

### Testing

| Was wird getestet     | Erwartetes Reslutat   | Resultat  |
| :---------------------| :---------------------| :---------|
| Webserver ist erreichbar unter localhost     | Startpage vom Webserver wird angezeigt | Startpage wird korrekt angezeigt    |
| Monitoring cAdvisor ist erreichbar  | Monitoring Page wird angezeigt    | Monitoring wird angezeigt |
| Monitoring überschreitet Were nicht     | Kein Container überschreitet die vorgegebene Grenze | Vorgegebene Grenze wird eingehalten     |


