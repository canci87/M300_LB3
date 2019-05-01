Dokumentation 
=============

### Übersicht
***

* 01 - [Ziel](#01---ziel)
* 02 - [Sicherheit](#02---Sicherheit)
* 03 - [Client Konfigurieren](#03---Client-Konfigurieren)
* 04 - [Vagrant Befehle](#04---Vagrant-Befehle)
* 05 - [Vagrant Boxen](#05---Vagrant-Boxen)
* 06 - [Firewall Konfig](#06---firewall-konfig)
* 07 - [Reverse Proxy](#07---Reverse-Proxy)
* 08 - [Testfälle](#08---Testfälle)


### 01 - Ziel
***


Ich habe mir für dieses Projekt vorgenommen, einen Apache Webserver zu erstellen, welcher über Port 8080 erreichbar sein soll. Zudem soll ein Volume eingerichtet werden, so dass ich die Daten lokal erstellen und speichern kann und diese dann direkt auch im Container gespeichert sind. Natürlich muss auch die Sicherheit gewährleistet sein, die Infos dazu sind im Kapitel Sicherheit zu finden.


### 02 - Sicherheit
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

### 03 - Client konfigurieren
***


1. Git-Bash öffnen
2. Git konfigurieren mit GitHub Account
      <br>`git config --global user.name "username"`
      <br>`git config --global user.email "email"`
3. Konfiguration abgeschlossen


### 04 - Vagrant Befehle
***

* vagrant up -> startet die aktuelle VM
* vagrant destroy -> stoppt und löscht die aktuelle VM
* vagrant init "boxname" -> erstellt vagrantfile mit angegebener Box
* vagrant suspend -> stoppt die aktuelle VM
* vagrant status -> zeigt den aktuelle Status der VM an


### 05 - Vagrant Boxen
***

[Web Server][1]


[1]: https://github.com/canci87/M-300-Services/tree/master/VagrantBox/Web%20Server


### 06 - Firewall Konfig
***

Bei der Firewall wurde lediglich konfiguriert, dass für alle der Port 8080 offen ist, damit der Webserver erreicht werden kann.
<br>`sudo ufw allow 8080/tcp`


### 07 - Reverse Proxy
***

Den Reverse Proxy wollte ich eigentlich die Zusätzlichen Module von Apache, *libapache2-mod-proxy-html* und *libxml2-dev* verwenden, jedoch konnte ich beide Packete nicht herunterladen, da sie nicht gefunden wurden. Auch mit dem zusätzlichen Parameter *-y* hat es nicht funkioniert. Die Zeit reichte mir am Ende nicht mehr, um das Problem zu lösen.


### 008 - Testfälle
***

| Was wird getestet     | Erwartetes Reslutat   | Resultat  |
| :---------------------| :---------------------| :---------|
| Test FW von Host nach vm port 8080      | Curl gibt postivie Ausgabe  | Positive Ausgabe      |
| Auf Host Localhost im Browser anzeigen  | Apache start Website wird angezeigt     | Start Website wird angezeigt|

