## Inhalt der Live-ISO

siduction stellt auf der Live-ISO, abgesehen von nicht freier Firmware, nur DFSG-freie Software zur Verfügung. Hinweise zur Installation proprietärer Software findet sich hier im Handbuch.

Das ISO basiert ausschließlich auf zum Veröffentlichungszeitpunkt jeweils aktuellem Debian Sid, bereichert und stabilisiert durch eigene Pakete und Skripte aus den siduction-Repositories. Als Kernel wird der jeweils aktuelle Vanilla Mainline Kernel verwendet und mit Patches versehen. ACPI und DMA sind aktiviert.

Eine komplette Manifest-Datei mit der Auflistung aller installierten Programme für jede einzele Veröffentlichungs-Variante von siduction findet man auf jedem Download-Spiegelserver: ISO-Versionen, Spiegelserver, Brennen.

### Varianten der ISO

siduction bietet sechs aktuelle Images mit verschiedenen Desktopumgebungen (zwei auch ohne)) in 64-Bit als Live-ISO zum Einstieg in Debian Sid. Üblicherweise dauert eine Installation zwischen 1 und 10 Minuten, je nach Hardware.
Die Varianten sind:

1. **KDE 64 Bit** , live-ISO mit etwa 1,4 GByte:
    - umfasst neben Plasma und KDE-Frameworks eine repräsentative Auswahl der KDE Applications.  
    - Die Installation zusätzlicher Anwendungen ist ohne Probleme via apt möglich.

---

2. **Cinnamon mit 64 Bit** , live-ISO mit etwa 1,2 GByte:
     - GTK-basierter Desktop mit einer repräsentativen Auswahl an nützlicher Software.  
     - Die Installation zusätzlicher Anwendungen ist ohne Probleme via apt möglich.

---

3.  **XFCE 64 Bit** , live-ISO mit etwa 1,1 GByte:
    - umfasst eine Desktop-Umgebung mit allen Features (keine Minimalversion!) und alle Anwendungen, um sofort produktiv tätig sein zu können.
    - Der Ressourcenaufwand ist geringer als mit KDE.
---
4.  **LXQt mit 64 Bit** ,  live-ISO mit etwa 1 GByte:
     - umfasst eine Desktopumgebung mit einer Auswahl an Qt-Applikationen.  
     - Der Fußabdruck ist etwas schmaler als bei XFCE

---

5.  **Xorg mit 64 Bit** ,  live ISO mit etwa 1 GByte:
      - Ein ISO-Image mit einem Xorg-Stack und dem spartanischen Fenstermanager Fluxbox.  
      - Für Anwender, die sich ihr System nach eigenen Vorstellungen aufbauen wollen

---

6.  **NoX mit 64 Bit** ,  live-ISO mit etwa 630 MByte: 
      - Wie der Name andeutet: kein vorinstallierter Xorg-Stack

---

**32 Bit ISO's** bieten wir standardmäßig nicht mehr an.  
Wenn ein 32Bit IOS gewünscht ist, wird ein solches auf Anfrage im IRC gerne erstellt. Testen können wir ein solches ISO leider nicht.

---

### Minimale Systemanforderungen
für: KDE-Plasma, Gnome, XFCE, LXDE, LXQt, Cinnamon, Mate, Xorg und NoX

#### Prozessoranforderungen: 64Bit CPU

    AMD64
    Intel Core2
    Intel Atom 330
    jede x86-64/ EM64T fähige CPU oder neuer
    neuere 64 bit fähige AMD Sempron and Intel Pentium 4 CPUs  
    (achten Sie auf das "lm"-Flag in /proc/cpuinfo oder nutzt inxi -v3).

#### Speicheranforderungen:

    Plasma: ≥1 GByte RAM
    Cinnamon: ≥512 MByte RAM
    XFCE: ≥512 MByte RAM
    LXQT: ≥256 MByte RAM
    Xorg: ≥256 MByte RAM
    NoX: ≥128MByte RAM

    ≥4GByte Festplattenspeicher, ≥10GByte empfohlen.
#### Sonstiges:

    VGA Grafikkarte mit mindestens 640x480 Pixel Auflösung.
    optisches Laufwerk oder USB Medien.

---

## Anwendungen und Hilfsprogramme ##

Als Internetbrowser werden (je nach Variante) [Firefox](https://mozilla.org), oder [Chromium](https://chromium.woolyss.com/download/de/#linux) mitgeliefert.

Als Bürosoftware werden bei XFCE und LXDE Abiword und Gnumeric vorinstalliert. Als Dateimanager stehen unter anderem Dolphin,Thunar und PCManFM zur Verfügung.

Zur Netzwerk- und Internetkonfiguration steht Connman oder Network-Manager zur Verfügung, und für WIFI konsultiert man am besten die [WIFI-Roaming-Dokumentation](../inet-wpagui_de.md). Aus eher historischen Gründen steht auch noch [ceni](../inet-ceni_de.md) zur Konfiguration zur Verfügung

Informationen zu nicht freien Treibern findet man [hier](../nf-firm_de.htm)

Zur Partitionierung von Festplatten werden [cfdisk](../part-cfdisk_de.md) und [GParted](https://gparted.sourceforge.io/) mitgeliefert. Gparted bietet auch die Möglichkeit, die Größe von NTFS-Partitionen zu ändern.

Tools zur Systemanalyse wie [Memtest86+](http://www.memtest.org/) (ein Tool zur umfassenden Speicheranalyse) werden ebenso mitgeliefert.

Jede ISO-Variante enthält eine umfangreiche Auswahl an Anwendungen für die Befehlszeile. Eine komplette Manifest-Datei mit den installierten Programmen für jede einzele Veroffentlichungs-Variante von siduction findet man auf jedem Download-Spiegelserver: ISO-Versionen, Spiegelserver, Brennen.
Haftungsausschluss (Disclaimer)

siduction ist experimentelle Software. Benutzung auf eigene Gefahr. Das siduction-Projekt, seine Entwickler und Team-Mitglieder können unter keinen Umständen wegen Beschädigung von Hardware oder Software, verlorener Daten oder anderer direkter oder indirekter Schäden des Nutzers durch Nutzung dieser Software zur Rechenschaft gezogen werden. Wer diesen Bedingungen nicht zustimmt, darf diese Software weder verwenden noch verteilen.