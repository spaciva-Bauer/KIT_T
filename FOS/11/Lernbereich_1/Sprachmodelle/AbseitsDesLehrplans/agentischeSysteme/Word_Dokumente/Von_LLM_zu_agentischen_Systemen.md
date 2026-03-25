Von reinen Sprachmodellen zum agentischen System

Unterrichtsmaterial für das Fach KIT | Berufliche Oberschule – Ausbildungsrichtung Technik


## Stufe 1 – Das reine Sprachmodell (LLM)

Stell dir ein extrem gut trainiertes **Autovervollständigungs-System** vor. Du gibst Text ein – du bekommst Text zurück. Das war's.

```
Eingabe:  "Was ist die Hauptstadt von Frankreich?"  
Ausgabe:  "Die Hauptstadt von Frankreich ist Paris."
```

Das Modell selbst ist dabei wie ein **Gehirn ohne Hände**: Es kann denken und formulieren, aber es kann nichts anfassen, nichts ausführen, nichts nachschlagen. Es kennt nur das, was beim Training in seine Gewichte eingeflossen ist – und das hat einen **Stichtag** (sog. *Knowledge Cutoff*).

**Grenzen dieses Modells:**

- Kein Zugriff auf aktuelle Informationen

- Kann keine Dateien lesen oder erstellen

- Kann keinen Code ausführen

- Vergisst alles nach dem Gespräch (kein Gedächtnis)


## Stufe 2 – Das Modell bekommt Werkzeuge (*Tool Use*)

Der entscheidende Schritt: Man gibt dem Sprachmodell die Fähigkeit, **Werkzeuge aufzurufen**. Das funktioniert so:

Das Modell lernt, statt einer normalen Textantwort einen speziellen **Werkzeugaufruf** zu formulieren – z.B.:

```
"Ich brauche das Ergebnis von: web\_search('Aktienkurs Apple heute')"
```

Ein äußeres System (der sog. **Tool-Runner**) erkennt diesen Aufruf, führt die Suche wirklich aus, und gibt das Ergebnis zurück ans Modell. Das Modell formuliert dann seine endgültige Antwort.

Das Prinzip lässt sich auf viele Werkzeuge ausweiten:

| Werkzeug | Was es kann |
| - | - |
| web\_search | Im Internet suchen |
| read\_file | Eine Datei einlesen |
| execute\_python | Python-Code ausführen |
| write\_file | Eine Datei erstellen |


Das Modell entscheidet selbst, **welches Werkzeug wann sinnvoll ist** – genau wie ein Handwerker, der selbst greift, ob er Hammer oder Schraubenzieher braucht.


## Stufe 3 – Der Agentische Loop

Jetzt wird es richtig interessant. Ein **agentisches System** führt nicht nur einen einzelnen Werkzeugaufruf durch, sondern arbeitet in einem **Regelkreis** (*Loop*):

```
┌─────────────────────────────────────────────────────┐  
│                                                     │  
│   Ziel empfangen                                    │  
│        ↓                                            │  
│   Überlegen: Was ist der nächste sinnvolle Schritt? │  
│        ↓                                            │  
│   Werkzeug aufrufen                                 │  
│        ↓                                            │  
│   Ergebnis auswerten                                │  
│        ↓                                            │  
│   Ziel erreicht? ──── Nein ────→ (zurück zum        │  
│        │                          Überlegen)        │  
│       Ja                                            │  
│        ↓                                            │  
│   Antwort ausgeben                                  │  
└─────────────────────────────────────────────────────┘
```

Das Modell plant also **mehrstufig**: Es bricht ein komplexes Ziel in Teilschritte auf, führt diese nacheinander aus – und passt seinen Plan an, wenn ein Schritt unerwartete Ergebnisse liefert.

**Konkretes Beispiel:**

> Nutzer: *„Lies meine Excel-Datei ein, berechne den Durchschnitt aller Umsätze und erstelle einen Word-Bericht darüber."*

Das agentische System arbeitet dann selbstständig:

1. Datei einlesen → read\_file("umsaetze.xlsx")

2. Python-Code schreiben und ausführen → Durchschnitt berechnen

3. Ergebnis in Word-Dokument schreiben → create\_file("bericht.docx")

4. Fertige Datei ausgeben

Kein einzelner dieser Schritte ist dabei „Intelligenz" im klassischen Sinne – die Stärke liegt in der **Kombination von Sprachverständnis, Planung und Werkzeugnutzung**.


## Die Entwicklungsstufen im Überblick

```
Stufe 1: LLM pur  
         Text → \[Sprachmodell\] → Text  
         (passiv, kein Gedächtnis, kein Zugriff)  
  
Stufe 2: LLM + Tools  
         Text → \[Sprachmodell\] ⇄ \[Werkzeuge\] → Text  
         (kann suchen, lesen, ausführen)  
  
Stufe 3: Agentisches System  
         Ziel → \[Planen → Handeln → Beobachten → Anpassen\] → Ergebnis  
         (autonom, mehrstufig, zielorientiert)
```


## Eine hilfreiche Analogie

Stell dir einen **sehr klugen Praktikanten** vor:

- **Stufe 1:** Er sitzt in einem Raum ohne Fenster, ohne Computer, ohne Telefon. Er kann nur denken und reden – aber nichts nachschlagen oder ausführen.

- **Stufe 2:** Er bekommt einen Computer mit Internet, Python und Word. Er kann jetzt Dinge wirklich erledigen.

- **Stufe 3:** Man gibt ihm ein komplexes Projekt und er arbeitet es **selbstständig ab** – er entscheidet selbst, wann er was nachschlägt, ausführt oder erstellt, und meldet sich erst, wenn er fertig ist.


> 💡 **Merke:** Ein agentisches KI-System = Sprachmodell + Werkzeuge + autonomer Planungs-Loop. Die KI entscheidet selbst, welche Werkzeuge sie in welcher Reihenfolge einsetzt, um ein Ziel zu erreichen.

