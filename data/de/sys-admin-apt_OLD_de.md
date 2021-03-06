# Ein kleines APT-Kochbuch # 

## Was bedeutet APT? ##

APT ist eine Abkürzung für Advanced Packaging Tool und stellt eine Sammlung von Programmen und Skripten, welche das System und den Administrator bei der Installation und Verwaltung von Debian-Paketen unterstützt.
Liste der Quellen (sources.list)

Das "APT"-System benötigt eine Konfigurationsdatei, welche Informationen über den Ort der installierbaren und aktualisierbaren Pakete beinhaltet. Im allgemeinen nennt man diese Datei sources.list. Moderne Systeme benutzen mittlerweile  modularisierte Sourcen um die Übersicht zu verbessern.

siduction stellt die Quellen in diesem Ordner bereit:  

    /etc/apt/sources.list.d/

Innerhalb dieses Verzeichnisses befinden sich standardmäßig folgende Dateien: 

    debian.list
    extra.list
    fixes.list

Dies hat den Vorteil, dass leichter automatisch aus Spiegelservern gewählt werden kann ("mirror switching"), und auch das Ergänzen oder Austauschen von Quell-Listen ist so einfacher zu gestalten.

Eigene Quell-Listen-Dateien können mit der Benennung /etc/apt/sources.list.d/*.list hinzugefügt werden. Auf einem siduction  könnte /etc/apt/sources.list.d/extra.list zum Beispiel so aussehen:

    This is the default mirror, choosen at first boot.
    # One might consider to choose the geographical nearest or the fastest      mirror.
    deb     http://packages.siduction.org/extra unstable main contrib non-free
    #d eb-src http://packages.siduction.org/extra unstable main contrib non-free

unter /etc/apt/sources.list.d/fixes.list könnte es so aussehen:

    deb      https://packages.siduction.org/fixes unstable main contrib non-free
    #deb-src https://packages.siduction.org/fixes unstable main contrib non-free

und /etc/apt/sources.list.d/debian.list enthält dann das eigentliche Debian Repo:

    # debian loadbalancer
    deb     http://deb.debian.org/debian/ unstable main contrib non-free
    # deb-src http://deb.debian.org/debian/ unstable main contrib non-free

Weitere Einträge für optionale siduction Repositories finden sich auf [siduction Repositories](https://packages.siduction.org/).

Fügt man zum Beispiel ein oder mehrere Debian Repositories hinzu, so würde dies folgender maßen aussehen:

    #Debian
    # Unstable
    deb http://ftp.us.debian.org/debian/ unstable main contrib non-free
    #deb-src http://ftp.us.debian.org/debian/ unstable main contrib non-free

    # Testing
    #deb http://ftp.us.debian.org/debian/ testing main contrib non-free
    #deb-src http://ftp.us.debian.org/debian/ testing main contrib non-free

    # Experimental
    #deb http://ftp.us.debian.org/debian/ experimental main contrib non-free
    #deb-src http://ftp.us.debian.org/debian/ experimental main contrib non-free

***ZUR BEACHTUNG:*** In diesem Beispiel wird der US-amerikanische Debian-Spiegelserver beginnend mit ftp.us verwendet. Diese Einstellung kann als root geändert werden, indem der Landes-Code angepasst wird (zum Beispiel: ftp.at, ftp.de). Die meisten Länder haben lokale Debian-Spiegelserver zur Verfügung. Dies bietet für den Anwender eine höhere Anbindungsgeschwindigkeit und spart auch Bandbreite.

[Liste der aktuell verfügbaren Debian-Server und deren Spiegelserver.](http://www.debian.org/mirrors/)

Um aktualisierte Informationen über die Pakete zu erhalten, wird eine Datenbank mit den benötigten Einträgen vorgehalten. Das Programm apt-get benutzt sie bei der Installation eines Pakets, um alle Abhängigkeiten aufzulösen und somit zu garantieren, dass die ausgewählten Pakete funktionieren. Die Erstellung bzw. Aktualisierung dieser Datenbank wird mit dem Befehl 'apt-get update' durchgeführt.

## apt-get update / apt update ##

    root@siduction# apt update
    Holen:1 http://siduction.org sid Release.gpg [189B]
    Holen:2 http://siduction.org sid Release.gpg [189B]
    Holen:3 http://siduction.org sid Release.gpg [189B]
    Holen:4 http://ftp.de.debian.org unstable Release.gpg [189B]
    Holen:5 http://siduction.org sid Release [34.1kB]
    Holen:6 http://ftp.de.debian.org unstable Release [79.6kB]
    Es wurden 404 kB in 8 s geholt (50,8 kB/s).
    Paketlisten werden gelesen... Fertig
    Abhängigkeitsbaum wird aufgebaut.
    Statusinformationen werden eingelesen.... Fertig
    Aktualisierung für 48 Pakete verfügbar. Führen Sie »apt list --upgradable« aus, um sie anzuzeigen.

## Wie installiere ich ein neues Paket? ##

Vorausgesetzt, dass die APT-Datenbank aktualisiert ist und der Name des Pakets bekannt ist, reicht folgender Befehl (weiter unten wird gezeigt, wie man ein Paket finden kann):

    root@siduction# apt install funtools
    aketlisten werden gelesen... Fertig
    Abhängigkeitsbaum wird aufgebaut.
    Statusinformationen werden eingelesen.... Fertig
    Die folgenden zusätzlichen Pakete werden installiert:
      libfuntools1 libwcstools1
    Die folgenden NEUEN Pakete werden installiert:
      funtools libfuntools1 libwcstools1
    0 aktualisiert, 3 neu installiert, 0 zu entfernen und 48 nicht aktualisiert.
    Es müssen 739 kB an Archiven heruntergeladen werden.
    Nach dieser Operation werden 2.083 kB Plattenplatz zusätzlich benutzt.
    Möchten Sie fortfahren? [J/n] j
    Holen:1 http://deb.debian.org/debian unstable/main amd64 libwcstools1 amd64 3.9.5-3 [331 kB]
    Holen:2 http://deb.debian.org/debian unstable/main amd64 libfuntools1 amd64 1.4.7-4 [231 kB]
    Holen:3 http://deb.debian.org/debian unstable/main amd64 funtools amd64 1.4.7-4 [177 kB]
    Es wurden 739 kB in 0 s geholt (1.678 kB/s).
    Vormals nicht ausgewähltes Paket libwcstools1:amd64 wird gewählt.
    (Lese Datenbank ... 279741 Dateien und Verzeichnisse sind derzeit installiert.)
    Vorbereitung zum Entpacken von .../libwcstools1_3.9.5-3_amd64.deb ...
    Entpacken von libwcstools1:amd64 (3.9.5-3) ...
    Vormals nicht ausgewähltes Paket libfuntools1:amd64 wird gewählt.
    Vorbereitung zum Entpacken von .../libfuntools1_1.4.7-4_amd64.deb ...
    Entpacken von libfuntools1:amd64 (1.4.7-4) ...
    Vormals nicht ausgewähltes Paket funtools wird gewählt.
    Vorbereitung zum Entpacken von .../funtools_1.4.7-4_amd64.deb ...
    Entpacken von funtools (1.4.7-4) ...
    libwcstools1:amd64 (3.9.5-3) wird eingerichtet ...
    libfuntools1:amd64 (1.4.7-4) wird eingerichtet ...
    funtools (1.4.7-4) wird eingerichtet ...
    Trigger für man-db (2.8.5-2) werden verarbeitet ...
    Trigger für libc-bin (2.28-8) werden verarbeitet ...
    
## Entfernen eines Pakets ##

Der nächste Befehl entfernt ein Paket. Abhängigkeiten werden nicht mit vom System entfernt:

    root@siduction# apt remove gaim
    Paketlisten werden gelesen... Fertig
    Abhängigkeitsbaum wird aufgebaut.       
    Statusinformationen werden eingelesen.... Fertig
    Die folgenden Pakete wurden automatisch installiert und werden nicht mehr benötigt:
      libfuntools1 libwcstools1
    Verwenden Sie »sudo apt autoremove«, um sie zu entfernen.
    Die folgenden Pakete werden ENTFERNT:
      funtools
    0 aktualisiert, 0 neu installiert, 1 zu entfernen und 48 nicht aktualisiert.
    Nach dieser Operation werden 505 kB Plattenplatz freigegeben.
    Möchten Sie fortfahren? [J/n] j
    (Lese Datenbank ... 279786 Dateien und Verzeichnisse sind derzeit installiert.)
    Entfernen von funtools (1.4.7-4) ...
    Trigger für man-db (2.8.5-2) werden verarbeitet ...


In dem letzten Fall werden die Konfigurationsdateien nicht vom System entfernt, sie können bei einer späteren Neuinstallation des Programmpakets (im Beispielfall gaim) wieder verwendet werden. Sollen auch die Konfigurationsdateien entfernt werden, dann wird folgender Aufruf benötigt:

    apt purge funtools

So werden auch die Konfigurationsdateien mit entfernt. Will man sehen, ob Konfigurationsdateien von bereits entfernten Programmen noch auf dem System verblieben sind, kann man ganz einfach kann man folgenden Befehl eingeben:

    dpkg -l | grep ^rc
    rc  colord                 1.4.3-3.1           amd64      system service to manage device colour profiles -- system daemon
    rc  hplip                  3.18.10+dfsg0-1     amd64      HP Linux Printing and Imaging System (HPLIP)
    rc  libsensors4:amd64      1:3.4.0-4           amd64      library to read temperature/voltage/fan sensors
    rc  sane                   1.0.14-13.1         amd64      scanner graphical frontends
    rc  sane-utils             1.0.27-3.1          amd64      API library for scanners -- utilities
    rc  systemd-coredump       240-1               amd64      tools for storing and retrieving coredumps

Die hier gelisteten Pakete wurden removed, ohne purgen.

## Downgraden/Hold eines Pakets ##

Manchmal kann es notwendig sein, auf eine frühere Version eines Pakets zurückzugreifen, da die neueste Version einen gravierenden Fehler aufweist.  

***Hold (Halten)***

    apt-mark hold paket

So beendet man den Hold eines Pakets

    apt-mark unhold paket

So sucht man nach Paketen, die auf Hold gesetzt sind:

    apt-mark showhold

Bitte bedenkt, dass hold nur eine Notfallmaßnahme ist. Man wird sich Probleme einhandeln, wenn man vergisst, einen hold wieder zeitnah aufzuheben. Das gilt umso mehr, je mehr (essentielle) Abhängigkeiten das Paket hat. Also: holds bitte nur im Notfall und schnellstmöglich wieder aufheben.

***Downgraden (Deaktualisierung)***

Debian unterstützt keinen Downgrade von Paketen. In einfachen Fällen kann das Installieren älterer Versionen gelingen, es kann aber auch spektakulär fehlschlagen. Mehr Informationen im englischsprachigen Debian-Handbuch unter dem Kapitel Emergency downgrading.

Obowhl ein Downgrade nicht unterstützt ist, kann er bei einfachen Paketen gelingen. Die Schritte für einen Downgrade werden nun am Paket kmahjongg demonstriert:

Die Quellen von Unstable werden in /etc/apt/sources.list.d/debian.list mit einem Rautezeichen "#" versehen  
Die Quellen für Testing werden /etc/apt/sources.list.d/debian.list zugefügt und und die weiteren Befehle ausgeführt:  

    apt-get update

    apt-get install kmahjongg/testing

Das nun installierte Paket wird nun vor Aktualisierungen geschützt, auf Hold gesetzt:

    apt-mark hold kmahjongg

nun werden die Quellen für Testing mit einem Rautezeichen <#> in /etc/apt/sources.list.d/debian.list versehen, während das Rautezeichen vor den Quellen für Unstable wieder entfernt werden. Nach dem Speichern der Änderungen:

    apt-get update

Wenn ein neues, fehlerfreies Paket in sid eintrifft, kann man die neueste Version wieder installieren, wenn man den "hold"-Status beendet:

    apt-mark unhold kmahjongg
    apt update
    apt install kmahjongg / apt dist-uppgrade / apt full-upgrade

## Aktualisierung des installierten Systems - dist-upgrade / full-upgrade - Überblick

Eine Aktualisierung des ganzen Systems wird mit diesem Befehl durchgeführt: dist-upgrade. Vor einer solchen Maßnahme sollten die aktuellen Upgradewarnungen auf der Hauptseite von siduction beachtet werden, um zu prüfen, ob Pakete des eigenen Systems betroffen sind. Wenn ein installiertes Paket behalten, also auf hold gesetzt werden sollte, verweisen wir auf den Abschnitt Downgrade bzw. "Hold" eines Pakets.

Ein einfaches 'apt-get upgrade / apt upgrade' von Debian Sid ist nicht empfohlen.
Wie regelmäßig soll eine Systemaktualisierung durchgeführt werden?

Eine Systemaktualisierung soll regelmäßig durchgeführt werden, alle ein bis zwei Wochen haben sich als guter Richtwert erwiesen. Auch bei monatlichen Systemaktualisierungen sollte es zu keinen nennenswerten Problemen kommen. Die Erfahrungen zeigen, dass länger als zwei, maximal drei Monate nicht zugewartet werden sollte. Besonders beachtet sollten Programmpakete werden, welche nicht aus den siduction- oder Debian-Repositorien stammen oder selbst kompiliert wurden, da diese nach einer Systemaktualisierung mittels dist-upgrade wegen Inkompatibilitäten ihre Funktionsfähigkeit verlieren können.

Nachdem die interne Datenbank aktualisiert wurde, kann man herausfinden, für welche Pakete eine neuere Version existiert (zuerst muss apt-show-versions installiert werden):

    root@siduction# apt-show-versions -u
    libpam-runtime/unstable upgradeable from 0.79-1 to 0.79-3
    passwd/unstable upgradeable from 1:4.0.12-5 to 1:4.0.12-6
    teclasat/unstable upgradeable from 0.7m02-1 to 0.7n01-1
    libpam-modules/unstable upgradeable from 0.79-1 to 0.79-3.........

Die Aktualisierung eines einzelnes Pakets (hier z. B. debtags-1.6.6.0) kann unter Berücksichtigung der Abhängigkeiten vorgenommen werden mit:

    root@siduction# apt-get install debtags-1.6.6.0
    Paketlisten werden gelesen... Fertig
    Abhängigkeitsbaum wird aufgebaut... Fertig
    Die folgenden Pakete werden ENTFERNT:
      apt-index-watcher
    Die folgenden Pakete werden aktualisiert:
      debtags
    1 aktualisiert, 0 neu installiert, 1 zu entfernen und 0 nicht aktualisiert.
    Es müssen 660kB Archive geholt werden.
    Nach dem Auspacken werden 1991kB Plattenplatz freigegeben worden sein.
    Möchtest Du fortfahren [J/n]?
    Hole:1 http://ftp.de.debian.org unstable/main debtags 1.6.6 [660kB]
    Es wurden 660kB in 1s geholt (513kB/s)
    (Lese Datenbank ... 138695 Dateien und Verzeichnisse sind derzeit installiert.)
    Entferne apt-index-watcher ...
    (Lese Datenbank ... 138692 Dateien und Verzeichnisse sind derzeit installiert.)
    Vorbereiten zum Ersetzen von debtags 1.6.2 (durch .../debtags_1.6.6_i386.deb) ...
    Entpacke Ersatz für debtags ...
    Richte debtags ein (1.6.6) ...
    Installiere neue Version der Konfigurationsdatei /etc/debtags/sources.list ...

**(Nur) Downloaden**

Eine wenig bekannte, aber großartige Möglichkeit ist die Option -d:

    apt update && apt dist-upgrade -d

-d ermöglicht, die Pakete eines dist-upgrades lokal zu speichern, ohne dass sie installiert werden. Dies kann in einer Konsole durchgeführt werden, während man in X ist. Der dist-upgrade selbst kann zu einem späteren Zeitpunkt in init 3 erfolgen. Dadurch erhält man auch die Möglichkeit, nach eventuellen Warnungen zu recherchieren und danach zu entscheiden, ob man die Aktualisierung durchführen möchte oder nicht:

    root@siduction#apt-get dist-upgrade -d
    Reading package lists... Done
    Building dependency tree
    Reading state information... Done
    Calculating upgrade... Done
    The following NEW packages will be installed:
      elinks-data
    The following packages have been kept back:
      git-core git-gui git-svn gitk icedove libmpich1.0ldbl
    The following packages will be upgraded:
      alsa-base bsdutils ceni configure-ndiswrapper debhelper
      discover1-data elinks file fuse-utils gnucash.........
    35 upgraded, 1 newly installed, 0 to remove and 6 not upgraded.
    Need to get 23.4MB of archives.
    After this operation, 594kB of additional disk space will be used.
    Möchtest Du fortfahren [J/n]?J 

J lädt die zu aktualisierenden bzw. neu zu installierenden Pakete, ohne das installierte System zu verändern.

Bitte NIEMALS eine Systemaktualisierung in der graphischen Umgebung X durchführen.
Besuche vor einer Systemaktualisierung die siduction-Homepage, um eventuelle Upgradewarnungen in Erfahrung zu bringen. Diese Warnungen sind wegen der Struktur von Debian sid/unstable notwendig, welches täglich neue Programmpakete in seine Repositorien aufnimmt.

Nach dem Download der Pakete mittels 'dist-upgrade -d' können diese jederzeit nach folgendem Muster installiert werden:

**dist-upgrade - Die einzelnen Schritte**

1. Aus der KDE-Desktopumgebung abmelden
2. In den Textmodus gehen mit Ctrl+Alt+F1
3. Einloggen als root

und dann folgende Befehle ausführen:

    init 3
    apt-get update
    apt-get dist-upgrade
    apt-get clean
    init 5 && exit

Bitte NIEMALS eine Systemaktualisierung mit einem Programm wie synaptic, adept oder kpackage durchführen!

:::warning
**Warnhinweis:**  
Eine Systemaktualisierung, die nicht im Runlevel 3 (init 3) durchgeführt wird, kann große, nicht unterstützbare Probleme mit sich bringen!
:::

---

**Gründe, warum man nur apt-get für eine Systemaktualisierung verwenden soll**

Paketmanager wie adept, synaptic und kpackage können nicht immer die umfassenden Änderungen in Sid (Änderungen von Abhängigkeiten, Benennungskonventionen, Skripten u.a.) korrekt auflösen. Dies sind keine Fehler in diesen Programmen oder Fehler der Entwickler.

Dies sind exzellente Programme für eine Installation von Debian stable, aber sie sind nicht angepasst an die besonderen Aufgaben der dynamischen Distribution Debian Sid.

Diese Programme können sich sehr gut dazu eignen, Programme zu suchen, aber zum Installieren, Löschen und zum Durchführen einer Systemaktualisierung soll apt-get verwendet werden.

Paketmanager wie adept, synaptic und kpackage sind - technisch gesprochen - nicht-deterministisch. Bei Verwendung einer dynamischen Distribution wie Debian Sid unter Hinzunahme von Drittrepositorien, deren Qualität nicht vom Debian-Team getestet sein kann, kann eine Systemaktualisierung zur Katastrophe führen, da diese Paketmanager durch automatische Lösungsversuche falsche Entscheidungen treffen können.

Weiterhin ist zu beachten, dass ALLE GUI-Paketmanager in X ausgeführt werden müssen, und Systemaktualisierungen in X (oder selbst ein ohnehin nicht empfohlenes 'apt-get upgrade') werden früher oder später dazu führen, dass man sein System irreversibel beschädigt hat.

Im Gegensatz dazu führt apt-get ausschließlich das durch, was angefragt ist. Bei unvollständigen Abhängigkeiten in Sid, sprich: wenn das System bricht (dies kann in Sid bei Strukturänderungen vorkommen), können die Ursachen genau festgestellt und dadurch repariert oder umgangen werden. Das eigene System "bricht" nicht. Falls also eine Systemaktualisierung dem Gefühl nach das halbe System löschen möchte, überlässt apt-get dem Administrator die Entscheidung, was zu tun ist, und handelt nicht eigenmächtig.

Dies ist der Grund, warum Debian-Builds apt-get nutzen und nicht andere Paketmanager.

**Mit apt-cache nach Programmpaketen suchen**

Ein sehr nützlicher Befehl im APT-System ist apt-cache, damit werden die APT-Datenbank durchsucht und Informationen über die Pakete ausgegeben; z. B. die Liste aller Pakete, die "siduction" und "manual" enthalten oder ansprechen, erhält man durch folgenden Befehl:

    $ apt-cache search bluewater-manual
    .......
    bluewater-manual-common - the official bluewater-manual - common files
    bluewater-manual-es - the official Spanish bluewater-manual
    bluewater-manual-de - the official German bluewater-manual
    bluewater-manual-el - the official Greek bluewater-manual
    bluewater-manual-pt-br - the official Brazilian Portuguese bluewater-manual
    bluewater-manual-en - the official English bluewater-manual

Möchte man mehr Informationen über die aktuellen Versionen eines Pakets, dann benutzt man:

    $ apt-cache show bluewater-manual-de
    Package: bluewater-manual-de
    Priority: optional
    Section: doc
    Installed-Size: 1096
    Maintainer: Kel Modderman <kel@otaku42.de>
    Architecture: all
    Source: bluewater-manual
    Version: 00.00.2010.08.14-1
    Depends: bluewater-manual-common
    Filename: pool/main/s/bluewater-manual/bluewater-manual-de_00.00.2010.08.14-1_all.deb
    Size: 388860
    MD5sum: e73f66e8dc90c57e764411a099d45ebc
    SHA1: a0a63fa991cab09e4422f26fdb0c4c5ac7b27bdd
    SHA256: e177819755f0d04cfe7c455e2bd4257063b7bb5521af6df7d7dd3b30727b2bb2
    Description: the official en bluewater-manual
     This manual is divided into common sections, for example, .......

Alle installierbaren Versionen des Pakets (abhängig von der sources.list) können folgendermaßen aufgelistet werden:

    $ apt-cache policy bluewater-manual-de
    bluewater-manual-de:
      Installiert:(keine)
      Mögliche Pakete:00.00.2010.08.14-1
      Versions-Tabelle:
         00.00.2010.08.14-1 0
            500 http://siduction.org sid/main Packages


**Graphisches Paketsuchprogramm "packagesearch"**

    apt-get update
    apt-get install packagesearch

Nach dem ersten Start von packagesearch muss in Packagesearch>Preferences apt-get gewählt werden.

Bitte benutze Packagesearch nicht zur Installation von Dateien/Paketen sondern nur als eine graphische Suchmaschine. Das Upgraden und die Neuinstallation von Dateien ohne vorheriges Beenden von X kann Probleme verursachen. Bitte lese dazu Ein neues Paket installieren.

Beim ersten Start kann auch ein Infofenster das Fehlen von deborphan bemängeln. Die Informationen von deborphan bitte mit größter Vorsicht verwenden.

Folgende Suchkriterien stehen zur Auswahl:

+ pattern (allgemeine Suchanfrage)
+ tags (Suche basierend auf debtags, einem neuen System, Debian-Pakete zu kategorisieren)
+ files (Dateinamen)
+ installed status (Installationsstatus)
+ orphaned packages (verwaiste Pakete)

Zusätzlich werden viele Informationen zu den Debian-Paketen angeboten, so auch welche Dateien in einem Paket geschnürt sind. Weitere ausführliche Informationen zur Verwendung von packagesearch findet man unter Help>Contents. Derzeit ist die Benutzerführung von packagesearch ausschließlich Englisch.

**Eine vollständige Beschreibung des APT-Systems findet man in Debians APT-HOWTO**

Page last revised 15/01/2012 1545 UTC
