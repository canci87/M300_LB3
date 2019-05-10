Dokumentation 
=============

### Übersicht
***

* 01 - [K1](#01---K1)
* 02 - [K2](#02---K2)
* 03 - [K3](#03---K3)
* 04 - [K4](#04---K4)
* 05 - [K5](#05---K5)


### 01 - K1
***


Die nötige Software, den Git-Hub Account (gitaccoutn) und den SSH-Key wurde alles bereits für LB2 installiert/erstellt.


### 02 - K2
***

### Persönlicher Wissenstand


Docker kannte ich vor diesem Modul nur ganz wenig. Mein ehemaliger Oberstift hat mir Docker zwar mal kurz erklärt, jedoch habe ich mich nie weiter darin vertieft oder arbeiten damit erledigt. Ich weiss das Container immer mehr und mehr verwendet werden, und bei alltägliche diensten wie z.B. Gmail vorkommen.
Um mein Wissenstand ein wenig aufzurüsten, habe ich vor allem zusätzlich zum Unterricht noch Youtube Videos angeschaut, welche die Grundlagen erklären.





***

### Geplante Umgebung

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


### 04 - K4
***

Um die Sicherheit der Container und des Systems zu gewährleisten, muss man noch ein paar Schritte vornehmen. 

**User setzen** <br>
Damit man im Container selbst nicht mit dem Root account arbeiten muss, sollte man bei der Erstellung eines Containers immer einen weiteren Benutzer mit weniger Rechten erstellen. 

```Shell
    $ RUN groupadd -r user_grp && useradd -r -g user_grp user
    $ USER user
```
Mit der USER Anweisung wechselt man zum gewünschtem User.

**Ports** <br>
Ein Container sollte immer nur die Ports geöffnet haben, die auch wirklich benötigt werden. Die geöffneten Ports sollten zudem auch nur für andere Container erreichbar sein.

**LOGs** <br>
Falls man keine Argumente definiert oder Zusatz Software verwendet, protokolliert Docker alles was an STDOUT und STDERR gesendet wird.

Die Logs können dann über den Befehl `docker logs` abgerufen werden.

**Monitoring**<br>
Damit man bescheid weiss wie es um die Ressourcen steht und ob etwas knapp ist, wird noch eine Monitoring Software benötigt.
Dafür verwende ich cAdvisor. Praktisch an dieser Software ist, dass sie auch als Container verwendet werden kann.


### 05 - K5
***

### Wissenszuwachs

Ich konnte im Verlauf dieser Arbeit sehr viel neues lernen, vorallem das Prinzip um Docker herum. Einfache Container sind für mich kein Problem und somit kann ich auch eine kleine und einfache Container Infra aufbauen. Auch in der LB2 habe ich sehr viel gelernt, vorallem weil ich Docker sowie auch Vagrant noch nie benutzt habe und auch nur sehr wenig davon gehört habe.

### Reflexion

Anfangs fiel es mir recht schwer, mich mit Docker und auch Github zurecht zu finden. Dies hat meine anfangs Motivation ein wenig in den Keller geschossen, da es ohne Erfolge auch keinen Spass macht. Als ich mir dann jedoch hilfe in der Klasse und auch im Geschäft holte und so die ersten Erfolge verzeichnen konnte, wurde die Motivation immer grösser. Was ich ein wenig müsahm fand, ist das Dokumentieren mit dem mark Down editor. Mit der Zeit ging das jedoch auch immer besser. Im grossen und ganze fand ich das Modul sher interessant und auch die Unterlagen sowie der Unterricht spannend.




