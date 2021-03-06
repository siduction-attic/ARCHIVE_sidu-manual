ANFANG   INFOBEREICH FÜR DIE AUTOREN  
Dieser Bereich ist vor der Veröffentlichung zu entfernen !!!  
**Status: RC1**

Änderungen 2020-03:
+ Entfernen der apt-get Befehle in "Die Verwaltung von Softwarepaketen" und "Aktualisierung des Systems - upgrade"
+ Entfernen von "WICHTIGE INFORMATION: ... Linux-LIVE-DVD/CD, ist sehr stark komprimiert. ... Brennen im DAO-Modus ... "
+ Hinzufügen "Download und Brennen" in Essenzielle Kapitel
+ Inhaltliche Anpassung in "Weitere Desktopumgebungen"
+ Korrektur und Aktualisierung aller Links

ENDE   INFOBEREICH FÜR DIE AUTOREN

------------------------------------------------

<div class="divider" id="welcome-quick"></div>

## siduction Kurzanleitung

siduction strebt danach, zu 100% mit Debian Sid kompatibel zu sein. Trotzdem kann siduction gegebenenfalls Pakete anbieten, welche temporär fehlerhafte Debian-Pakete ersetzen. Das Apt-Repository von siduction enthält siduction spezifische Pakete wie den siduction-Kernel, Skripte, Pakete, die wir gern nach Debian pushen würden, Hilfsprogramme und Dokumentationen.

### Essenzielle Kapitel

<warning>
Einige Kapitel des Handbuchs stellen für Nutzer, die neu bei Linux bzw. neu bei siduction sind, essenzielle Lektüre dar. Neben dieser Kurzeinführung sind das:
</warning>

+ [Terminal/Konsole](term-konsole_de.md#term-kon)  - Beschreibt, wie ein Terminal und der su-Befehl zu nutzen sind.

+ [Partitionieren der Festplatte](part-gparted_de.md#partition)  - Beschreibt, wie eine Festplatte partitioniert werden kann. 

+ [siduction ISO herunterladen und DVD brennen](cd-dl-burning_de.md)  - Beschreibt den Download, die Prüfung und das Brennen einer siduction ISO auf DVD.

+ [Installation auf einer Festplatte](hd-install_de.md#install-prep)  - Beschreibt, wie siduction auf einer Festplatte installiert wird.

+ [Installation auf USB-Geräte](hd-install-opts_de.md#usb-hd)  - Beschreibt, wie siduction auf USB-stick/SD/Flash-Card installiert wird.

+ [Installation auf USB-Stick/SD von einem anderen System](hd-ins-opts-oos_de.md#raw-usb)  - Beschreibt, wie siduction von einem anderen System auf einen USB-Stick bzw. SD/Flash-Card geschrieben werden kann.

+ [Nicht freie Treiber, Firmware und Quellen](gpu_de.md#foss-xorg)  - Beschreibt, wie Softwarequellen adaptiert und nicht freie Firmwares installiert werden können.

+ [Internetverbindung](inet-ceni_de.md#netcardconfig)  - Beschreibt, wie man sich mit dem Internet verbinden kann.

+ [Paketmanager und Systemaktualisierung](sys-admin-apt_de.md#apt-cook)  - Beschreibt, wie neue Software installiert und das System aktualisiert werden kann.

### Zur Stabilität von Debian Sid

'Sid' ist der Name des Unstable-Repositories von Debian. Debian Sid wird regelmäßig mit neuen Softwarepaketen beschickt, wodurch diese Debian-Distribution sehr zeitnah die neuesten Versionen der jeweiligen Programme enthält. Dies bedeutet aber auch, dass zwischen einer Veröffentlichung im Upstream (von den Softwareentwicklern) und der Verteilung in Debian Sid weniger Zeit ist, um die Pakete zu testen.

### Der siduction-Kernel

Der Linux-Kernel von siduction ist optimiert, um folgende Ziele zu erreichen: Problembehebung, erweiterte und aktualisierte Funktionen, Leistungsoptimierung, höhere Stabilität. Basis ist immer der aktuelle Kernel von [http://www.kernel.org/](https://www.kernel.org/) . 

### Die Verwaltung von Softwarepaketen

siduction richtet sich nach den Debian-Regeln bezüglich der Paketestruktur und verwendet apt und dpkg für das Management der Softwarepakete. Die Repositorien von Debian und siduction befinden sich in `/etc/sources.list.d/*` 

Debian Sid enthält mehr als 20.000 Programmpakete, womit die Chancen, ein für eine Aufgabe geeignetes Programm zu finden, sehr gut stehen. Wie man Programmpakete sucht, ist hier beschrieben:  
[Programmsuche mit apt-cache bzw. apt](sys-admin-apt_de.md#apt-cache)  
oder mit  
[GUI-Paketsuche mit packagesearch](sys-admin-apt_de.md#gui-pacsea) .

Ein Programmpaket wird mit diesem Befehl installiert:

~~~
apt install <Paketname>
~~~
 
Siehe auch: [Neue Pakete installieren](sys-admin-apt_de.md#apt-install) .

Die Repositorien von Debian Sid werden in der Regel viermal am Tag mit aktualisierten bzw. neuen Softwarepaketen beschickt. Zur schnellen Verwaltung der Pakete wird eine lokale Datenbank verwendet. Der Befehl

~~~
apt update
~~~

ist vor jeder Neuinstallation eines Softwarepakets notwendig, um die lokale Datenbank mit dem Softwareangebot der Repositorien zu synchronisieren.

### Die Nutzung anderer auf Debian basierender Repositorien, Quellen und RPMs

Installationen aus Quellcode sind nicht unterstützt. Empfohlen ist eine Kompilierung als User (nicht als root) und die Platzierung der Anwendung im Home-Verzeichnis, ohne dass sie ins System installiert wird. Die Verwendung von  *checkinstall*  zum Erzeugen von DEB-Paketen sollte auf die rein private Nutzung beschränkt bleiben. Konvertierungsprogramme für RPM-Pakete wie  *alien*  sind nicht empfohlen.

Andere bekannte (und weniger bekannte) Distributionen, die auf Debian basieren, erstellen neue, von Debian verschieden strukturierte Pakete und verwenden oft andere Verzeichnisse, in denen bei der Installation Programme, Skripte und Dateien abgelegt werden, als Debian. Dies kann zu instabilen Systemen führen. Manche Pakete lassen sich wegen nicht auflösbarer Abhängigkeiten, unterschiedlicher Benennungskonventionen oder unterschiedlicher Versionierung überhaupt nicht installieren. Eine unterschiedliche Version von glibc zum Beispiel kann dazu führen, dass kein Programm lauffähig ist.

Aus diesem Grund sollen die Repositorien von Debian benutzt werden, um die benötigten Softwarepakete zu installieren. Andere Softwarequellen können nur schwer oder gar nicht von siduction unterstützt werden. Darunter fallen auch Pakete und PPAs von Ubuntu.

### Aktualisierung des Systems - upgrade

Ein upgrade ist nur bei beendetem Grafikserver X durchzuführen. Um den Grafikserver zu beenden, gibt man als **root** den Befehl

~~~
init 3
~~~

in eine Konsole ein. Danach sind Systemaktualisierungen sicher durchführbar. Zuerst die lokale Paketdatenbank auffrischen mit

~~~
apt update
~~~ 

dann mit einer der beiden Varianten das System aktualisieren.

~~~
apt upgrade
apt full-upgrade
~~~

Anschließend startet man mit folgendem Befehl wieder die graphische Oberfläche:

~~~
init 5
~~~
 
**apt full-upgrade** ist das empfohlene Verfahren, um eine siduction-Installation auf den neuesten Stand zu bringen. Ausführlicher wird das hier beschrieben:  
[Aktualisierung eines installierten Systems - full-upgrade](sys-admin-apt_de.md#apt-upgrade).

### Konfiguration von Netzwerken

'Ceni'  ist ein Skript zur schnellen Konfiguration von Netzwerkkarten (Ethernet und drahtlos). Drahtlose Netzwerke werden von dem Skript gescannt, man kann die Verschlüsselungsmethoden WEP und WPA wählen und die Backends  **`wireless-tools`**  bzw.  **`wpasupplicant`**  zur Konfiguration drahtloser Netzwerke verwenden. Die Ethernet-Konfiguration erfolgt bei Verwendung eines DHCP-Servers am Router (dynamische Zuweisung einer IP-Adresse) automatisch, aber auch die Möglichkeit eines manuellen Setups (von Netmasks bis Nameserver) ist mit diesem Skript gegeben.

Der Startbefehl in der Konsole ist `Ceni`  oder `ceni` . Falls das Skript nicht vorhanden ist, installiert man es mit:

~~~
apt install ceni
~~~

Mehr Informationen unter [Internet und Netzwerk - Ceni](inet-ceni_de.md#netcardconfig) 

### Runlevels - Ziel-Unit

Standardmäßig bootet siduction in die graphische Oberfläche (außer NoX).  
Die Konfiguration der Runlevel ist im Kapitel [siduction-Runlevels - Ziel-Unit](sys-admin-gen_de.md#ziel-unit) beschrieben.

### Weitere Desktopumgebungen

Plasma, Gnome, Xfce, LXQt, Cinnamon und Xorg werden von siduction ausgeliefert.

### Hilfe im IRC und im Forum

Hilfe gibt es jederzeit im IRC bzw. im Forum von siduction.

+ Mehr dazu im Kapitel [Wo es Hilfe gibt](help_de.md#help-gen) .

+ [Mit diesem Link kannst Du den IRC sofort in Deinem Browser aufrufen](https://webchat.oftc.net/) : gib dazu einen frei gewählten Nicknamen ein und betritt den Channel #siduction-de.


<div id="rev">Page last revised by akli, 12/05/2020</div>

