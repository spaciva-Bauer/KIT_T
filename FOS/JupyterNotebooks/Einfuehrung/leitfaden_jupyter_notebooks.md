Leitfaden: Arbeiten mit Jupyter Notebooks

> **Zielgruppe:** Schülerinnen und Schüler der Oberstufe ohne Vorerfahrung mit Jupyter Notebooks  
**Schwerpunkt:** Aufbau und Gestaltung von Notebooks

> 📓 **Übungsnotebook:** Zu diesem Leitfaden gibt es das Begleit-Notebook uebungsnotebook\_jupyter.ipynb. Es enthält geführte Übungen zu allen Abschnitten – ideal, um das Gelesene direkt auszuprobieren. Siehe auch [Abschnitt 11](#11-übungsnotebook).


## 1. Was ist ein Jupyter Notebook?

Ein Jupyter Notebook ist eine interaktive Arbeitsumgebung, die direkt im Webbrowser läuft. Es verbindet **Text**, **Bilder**, **Formeln** und **ausführbaren Code** in einem einzigen Dokument – ähnlich wie ein digitales Arbeitsheft.

Notebooks bestehen aus einzelnen **Zellen**, die nacheinander bearbeitet und ausgeführt werden können. Diese Struktur macht sie besonders geeignet für den Unterricht, da Erklärungen und Code eng miteinander verknüpft werden können.


## 2. Die Oberfläche im Überblick

Beim Öffnen eines Notebooks siehst du folgende Bereiche:

| Bereich | Beschreibung |
| - | - |
| **Menüleiste** | Zugriff auf alle Befehle (Datei, Bearbeiten, Einfügen, …) |
| **Symbolleiste** | Häufig genutzte Aktionen als Schaltflächen (Speichern, Zelle hinzufügen, Ausführen, …) |
| **Zellenbereich** | Der eigentliche Arbeitsbereich mit allen Zellen des Notebooks |
| **Kernel-Anzeige** | Zeigt oben rechts an, welche Programmiersprache aktiv ist (hier: Python) |




## 3. Zelltypen – das Herzstück des Notebooks

Jede Zelle in einem Notebook hat einen **Typ**, der bestimmt, was sie enthält und wie sie verarbeitet wird. Die zwei wichtigsten Typen sind:

### 3.1 Markdown-Zellen (Text und Formatierung)

Markdown-Zellen dienen zur **Erklärung, Dokumentation und Strukturierung**. Sie enthalten formatierten Text, der nach dem Ausführen lesbar dargestellt wird.

Den Zelltyp kannst du in der Symbolleiste über das Dropdown-Menü auswählen (Standard: „Code").

### 3.2 Code-Zellen (ausführbarer Python-Code)

Code-Zellen enthalten Python-Befehle. Nach dem Ausführen erscheint das Ergebnis direkt unterhalb der Zelle.


## 4. Markdown – Text professionell gestalten

Markdown ist eine einfache Auszeichnungssprache, mit der du Text formatieren kannst, ohne komplizierte Befehle zu kennen. Hier die wichtigsten Elemente:

### 4.1 Überschriften

```
\# Überschrift 1. Ordnung  
\#\# Überschrift 2. Ordnung  
\#\#\# Überschrift 3. Ordnung
```

Überschriften strukturieren dein Notebook in Abschnitte und Unterabschnitte. Je mehr \#-Zeichen, desto kleiner die Überschrift.


### 4.2 Textformatierung

```
\*\*fetter Text\*\*  
\*kursiver Text\*  
~~durchgestrichener Text~~  
\`Code im Fließtext\`
```

**Ergebnis:**

- **fetter Text**

- *kursiver Text*

- ~~durchgestrichener Text~~

- Code im Fließtext


### 4.3 Listen

**Ungeordnete Liste** (Aufzählung):

```
- Erster Punkt  
- Zweiter Punkt  
  - Unterpunkt (zwei Leerzeichen einrücken)
```

**Geordnete Liste** (Nummerierung):

```
1. Erster Schritt  
2. Zweiter Schritt  
3. Dritter Schritt
```


### 4.4 Trennlinien

```
---
```

Eine Zeile mit drei Bindestrichen erzeugt eine horizontale Linie, die Abschnitte optisch trennt.


### 4.5 Blockzitate

```
\> Dies ist ein hervorgehobener Hinweis oder ein Zitat.
```

> Dies ist ein hervorgehobener Hinweis oder ein Zitat.

Blockzitate eignen sich gut für wichtige Hinweise oder Aufgabenstellungen.


### 4.6 Tabellen

```
| Spalte 1 | Spalte 2 | Spalte 3 |  
|---|---|---|  
| Wert A   | Wert B   | Wert C   |  
| Wert D   | Wert E   | Wert F   |
```

**Ergebnis:**

| Spalte 1 | Spalte 2 | Spalte 3 |
| - | - | - |
| Wert A | Wert B | Wert C |
| Wert D | Wert E | Wert F |



### 4.7 Links und Bilder

```
\[Anzeigetext\](https://www.beispiel.de)  
  
!\[Bildbeschreibung\](pfad/zum/bild.png)
```


### 4.8 Mathematische Formeln (LaTeX)

Jupyter Notebooks unterstützen mathematische Formeln im LaTeX-Format:

```
Inline-Formel: $a^2 + b^2 = c^2$  
  
Abgesetzte Formel:  
$$E = mc^2$$
```



## 5. Zellen bearbeiten und ausführen

### 5.1 Eine Zelle ausführen

Es gibt mehrere Wege, eine Zelle auszuführen:

| Aktion | Tastenkürzel |
| - | - |
| Zelle ausführen, zur nächsten springen | Shift + Enter |
| Zelle ausführen, in der Zelle bleiben | Ctrl + Enter |
| Zelle ausführen, neue Zelle darunter einfügen | Alt + Enter |


> **Wichtig:** Markdown-Zellen müssen ebenfalls ausgeführt werden, damit die Formatierung sichtbar wird!

### 5.2 Bearbeitungsmodus und Navigationsmodus

Ein Notebook kennt zwei Modi:

- **Bearbeitungsmodus** (grüner Rahmen): Du kannst den Inhalt der Zelle verändern. Aktivierung durch Klick in die Zelle oder Enter.

- **Navigationsmodus** (blauer Rahmen): Du kannst zwischen Zellen navigieren und Zellenoperationen durchführen. Aktivierung durch Esc.


## 6. Zellen verwalten

Im **Navigationsmodus** stehen folgende Tastenkürzel zur Verfügung:

| Aktion | Tastenkürzel |
| - | - |
| Neue Zelle oberhalb einfügen | A |
| Neue Zelle unterhalb einfügen | B |
| Zelle löschen | D, D (zweimal drücken) |
| Zelltyp → Markdown | M |
| Zelltyp → Code | Y |
| Zelle kopieren | C |
| Zelle einfügen (darunter) | V |
| Ausführen rückgängig machen | Z |


Alternativ können alle diese Aktionen über das Menü **„Edit"** bzw. **„Insert"** ausgeführt werden.


## 7. Notebook strukturieren – Empfehlungen

Ein gut strukturiertes Notebook ist übersichtlich und leicht verständlich. Halte dich an folgende Grundsätze:

1. **Beginne mit einem Titel** (Überschrift 1. Ordnung) und einer kurzen Einleitung in einer Markdown-Zelle.

2. **Gliedere in Abschnitte** mit Überschriften 2. und 3. Ordnung.

3. **Erkläre vor dem Code:** Füge vor jeder Code-Zelle eine Markdown-Zelle ein, die beschreibt, was der folgende Code tut.

4. **Nutze Trennlinien** (---), um größere Abschnitte voneinander abzugrenzen.

5. **Führe Zellen der Reihe nach aus** – Notebooks sind für die sequenzielle Ausführung von oben nach unten gedacht.


## 8. Speichern und Exportieren

| Aktion | Beschreibung |
| - | - |
| **Speichern** | Ctrl + S oder Diskettensymbol in der Symbolleiste |
| **Autosave** | Jupyter speichert das Notebook regelmäßig automatisch |
| **Exportieren** | Über File → Download as in verschiedene Formate (z. B. PDF, HTML) |


Notebook-Dateien haben die Endung **.ipynb** und können weitergegeben und auf anderen Computern mit Jupyter geöffnet werden.


## 9. Häufige Probleme und Lösungen

| Problem | Mögliche Ursache | Lösung |
| - | - | - |
| Markdown wird nicht gerendert | Zelle nicht ausgeführt | Shift + Enter drücken |
| Zelltyp lässt sich nicht ändern | Im Bearbeitungsmodus | Esc drücken, dann M oder Y |
| Notebook reagiert nicht | Kernel hängt | Kernel → Restart im Menü |
| Änderungen gehen verloren | Nicht gespeichert | Regelmäßig Ctrl + S drücken |



## 10. Kurzreferenz: Die wichtigsten Markdown-Elemente

```
\# Titel  
\#\# Abschnitt  
\#\#\# Unterabschnitt  
  
\*\*fett\*\*   \*kursiv\*   \`Code\`  
  
- Liste       1. Nummeriert  
  
\> Hinweis/Zitat  
  
---   (Trennlinie)  
  
$Formel$   $$abgesetzte Formel$$  
  
| Spalte 1 | Spalte 2 |  
|---|---|  
| Inhalt   | Inhalt   |
```


## 11. Übungsnotebook \{\#11-übungsnotebook\}

Zum Leitfaden gehört das Begleit-Notebook **uebungsnotebook\_jupyter.ipynb**, das du von deiner Lehrperson erhältst oder herunterlädst.

### Was dich erwartet

Das Notebook ist in acht Teile gegliedert, die den Abschnitten dieses Leitfadens folgen:

| Teil | Thema |
| - | - |
| 1 | Zellen kennenlernen – Typen, Einfügen, Ausführen |
| 2 | Überschriften und Textstruktur |
| 3 | Textformatierung (fett, kursiv, Code) |
| 4 | Listen (ungeordnet, nummeriert, verschachtelt) |
| 5 | Blockzitate und Trennlinien |
| 6 | Tabellen |
| 7 | Mathematische Formeln (LaTeX) |
| 8 | Abschlussaufgabe: Mini-Notebook gestalten |


### So arbeitest du damit

1. Öffne die Datei uebungsnotebook\_jupyter.ipynb in Jupyter.

2. Lies jede Erklärungszelle und führe sie mit Shift + Enter aus.

3. Bearbeite die markierten **Übungszellen** (erkennbar am ✏️-Symbol).

4. Speichere deine Arbeit regelmäßig mit Ctrl + S.

> **Tipp:** Halte beim Bearbeiten des Notebooks den Leitfaden geöffnet – alle Syntaxbeispiele findest du in den entsprechenden Abschnitten zum Nachschlagen.


*Leitfaden erstellt für den Oberstufenunterricht · Stand: 2026*

