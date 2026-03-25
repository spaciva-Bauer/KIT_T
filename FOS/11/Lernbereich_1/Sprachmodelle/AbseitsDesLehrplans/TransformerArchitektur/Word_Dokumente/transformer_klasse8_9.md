# Wie denkt eine KI? – Der Transformer einfach erklärt

> **Zielgruppe:** Gymnasium Bayern, Klasse 8–9  
> **Fächer:** Informatik, Natur und Technik (NuT), fächerübergreifend  
> **Voraussetzungen:** Grundlegende Computerkenntnisse, Koordinatensystem aus dem Mathematikunterricht

---

## Inhaltsverzeichnis

1. [Was ist eigentlich eine KI?](#1-was-ist-eigentlich-eine-ki)
2. [Was ist ein Transformer?](#2-was-ist-ein-transformer)
3. [Schritt 1: Sprache in Zahlen umwandeln – Tokenisierung](#3-schritt-1-sprache-in-zahlen-umwandeln--tokenisierung)
4. [Schritt 2: Bedeutung als Zahlenvektor – Embeddings](#4-schritt-2-bedeutung-als-zahlenvektor--embeddings)
5. [Schritt 3: Die Reihenfolge kennen – Positional Encoding](#5-schritt-3-die-reihenfolge-kennen--positional-encoding)
6. [Schritt 4: Aufmerksamkeit – Was gehört zusammen?](#6-schritt-4-aufmerksamkeit--was-gehört-zusammen)
7. [Schritt 5: Mehrere Blickwinkel gleichzeitig](#7-schritt-5-mehrere-blickwinkel-gleichzeitig)
8. [Schritt 6: Wissen verarbeiten](#8-schritt-6-wissen-verarbeiten)
9. [Wie lernt die KI überhaupt?](#9-wie-lernt-die-ki-überhaupt)
10. [Bekannte KI-Modelle und was sie können](#10-bekannte-ki-modelle-und-was-sie-können)
11. [Was kann ein Transformer (noch) nicht?](#11-was-kann-ein-transformer-noch-nicht)
12. [Zusammenfassung – Das Wichtigste auf einen Blick](#12-zusammenfassung--das-wichtigste-auf-einen-blick)
13. [Aufgaben und Experimente](#13-aufgaben-und-experimente)

---

## 1. Was ist eigentlich eine KI?

Wenn du ChatGPT oder einen anderen KI-Assistenten fragst: *„Was ist die Hauptstadt von Frankreich?"* – bekommst du sofort die Antwort: *„Paris."* Aber wie weiß die KI das? Hat sie nachgedacht? Hat sie in einem Buch nachgeschlagen?

**Die kurze Antwort:** Nein. Eine KI rechnet. Sie erkennt Muster in riesigen Mengen von Text, die sie während des Trainings gesehen hat – und nutzt diese Muster, um Antworten zu erzeugen.

### Was KI ist – und was nicht

| KI **kann**... | KI **kann nicht**... |
|----------------|----------------------|
| Muster in Daten erkennen | Wirklich „denken" oder „verstehen" |
| Texte schreiben und übersetzen | Bewusst lügen oder eine Meinung haben |
| Bilder beschreiben | Gefühle empfinden |
| Fragen beantworten | Garantiert die Wahrheit sagen |

> **Merke:** KI ist kein Zauberer und kein Mensch – sie ist ein sehr cleveres Rechenprogramm.

---

## 2. Was ist ein Transformer?

Ein **Transformer** ist eine besondere Bauweise eines künstlichen neuronalen Netzes. Man kann ihn sich wie ein sehr ausgeklügeltes Textverarbeitungsprogramm vorstellen, das aus riesigen Mengen an Text gelernt hat.

Das Wort „Transformer" hat hier **nichts** mit den bekannten Robotern aus dem Kino zu tun – es kommt aus der Mathematik und beschreibt, wie der Text umgeformt (transformiert) wird.

### Wann wurde er erfunden?

Im Jahr **2017** haben Forscher bei Google einen Aufsatz mit dem Titel *„Attention Is All You Need"* (dt.: *„Aufmerksamkeit ist alles, was du brauchst"*) veröffentlicht. Seitdem ist der Transformer die Grundlage fast aller modernen KI-Sprachprogramme – zum Beispiel:

- **ChatGPT** (von OpenAI)
- **Claude** (von Anthropic)
- **Gemini** (von Google)

### Der große Überblick

Stell dir vor, du gibst der KI den Satz: *„Übersetze ins Englische: Die Katze schläft."*

Dann passiert folgendes (vereinfacht):

```
Du tippst:  "Die Katze schläft."
               ↓
        Text wird in Zahlencodes zerlegt
               ↓
        Jeder Code bekommt eine "Bedeutungs-Koordinate"
               ↓
        Die KI berechnet, welche Wörter zusammengehören
               ↓
        Die KI erzeugt die Antwort Stück für Stück
               ↓
Die KI antwortet: "The cat is sleeping."
```

In den nächsten Abschnitten schauen wir uns jeden dieser Schritte genauer an!

---

## 3. Schritt 1: Sprache in Zahlen umwandeln – Tokenisierung

Computer können nur mit Zahlen arbeiten – keinen Buchstaben, keine Wörter, nur Zahlen. Deshalb muss der Text zuerst in Zahlen umgewandelt werden.

### Was ist ein Token?

Ein **Token** ist ein kleines Textstück. Das kann ein ganzes Wort sein, aber auch nur ein Teil eines Wortes. Schau dir das Beispiel an:

```
Text:    "Hausaufgaben sind manchmal schwierig."

Tokens:  ["Haus", "auf", "gaben", " sind", " manchmal", " schwierig", "."]

Zahlen:  [ 4821,   342,   917,    253,      8841,         2019,        12 ]
```

Jeder Token bekommt eine **eindeutige Zahl** – ähnlich wie eine Ausweisnummer. Die KI hat eine riesige Tabelle mit Tausenden solcher Nummern (das **Vokabular**). Moderne KI-Modelle kennen bis zu 100.000 verschiedene Tokens!

### Warum nicht einfach ganze Wörter?

Stell dir vor, jemand schreibt das Fantasiewort „Superultraflauschig". Dieses Wort steht in keiner Tabelle! Wenn die KI Text in kleinere Stücke zerlegt, kann sie aber trotzdem damit umgehen:

```
"Superultraflauschig" → ["Super", "ultra", "flausch", "ig"]
```

Jedes Teilstück ist bekannt – zusammen ergibt es das neue Wort.

> 🔍 **Ausprobieren:** Gehe auf [platform.openai.com/tokenizer](https://platform.openai.com/tokenizer) und gib deinen eigenen Namen ein. Wie viele Tokens besteht er aus?

---

## 4. Schritt 2: Bedeutung als Zahlenvektor – Embeddings

Eine Zahl wie „4821" sagt noch nichts über die Bedeutung eines Wortes aus. Die Zahl für „Hund" könnte genauso gut neben der Zahl für „Rakete" liegen – das wäre sinnlos.

Deshalb wird jede Token-Nummer in einen sogenannten **Embedding-Vektor** umgewandelt: eine Liste von Zahlen, die die **Bedeutung** des Wortes beschreibt.

### Bedeutung als Punkt im Raum

Stell dir vor, du hast einen Koordinatenraum – aber statt 2 Achsen (x und y) hat er hunderte von Achsen. Jedes Wort ist ein Punkt in diesem Raum.

Das Besondere: Wörter mit ähnlicher Bedeutung liegen **nah beieinander**, Wörter mit unterschiedlicher Bedeutung **weit auseinander**.

```
Vereinfachtes Beispiel mit nur 2 Dimensionen:

        ↑ Lebewesen
        |
"Hund"  •  "Katze"
        |
"Vogel" •
        |
--------+----------→ Hat Flügel
        |
"Auto"  •    "Zug" •
        |
```

In diesem Beispiel liegen „Hund" und „Katze" nah beieinander (beide Tiere, keine Flügel). „Vogel" liegt weiter oben (Tier mit Flügeln). „Auto" und „Zug" liegen in einer ganz anderen Ecke.

### Eine berühmte Rechenaufgabe

Bei gut trainierten Embeddings kann man sogar rechnen:

```
"König"  −  "Mann"  +  "Frau"  ≈  "Königin"
```

Das bedeutet: Der Unterschied zwischen König und Mann ist der gleiche wie der Unterschied zwischen Königin und Frau – die KI hat diese Beziehung automatisch beim Training gelernt!

> **Hinweis für den Unterricht:** Diese Embeddings lernt die KI selbst – niemand hat ihr gesagt, was „ähnlich" bedeutet. Sie hat es aus Millionen von Texten herausgefunden.

---

## 5. Schritt 3: Die Reihenfolge kennen – Positional Encoding

Jetzt gibt es ein Problem: Die KI liest nicht Wort für Wort, sondern verarbeitet alle Wörter **gleichzeitig**. Dann verliert sie aber die Information, welches Wort wo stand!

Schau dir diese beiden Sätze an:

```
"Der Hund beißt den Mann."
"Der Mann beißt den Hund."
```

Die gleichen Wörter – aber völlig unterschiedliche Bedeutungen! Die Reihenfolge ist also sehr wichtig.

### Die Lösung: Eine Positionsnummer hinzufügen

Jeder Token-Vektor bekommt eine kleine **Positionsinformation** hinzugefügt – eine Art „Platznummer" im Satz.

```
Token 1: "Der"   → Bedeutungsvektor  +  Position 1
Token 2: "Hund"  → Bedeutungsvektor  +  Position 2
Token 3: "beißt" → Bedeutungsvektor  +  Position 3
...
```

So weiß die KI: Token 2 kam an zweiter Stelle. Das ist einfach, aber sehr wichtig!

> **Analogie:** Stell dir vor, du bekommst ein Puzzle in einem Beutel. Alle Teile sind da, aber ohne Nummerierung weißt du nicht, welches Teil wohin gehört. Die Positionsnummer ist wie ein Aufkleber auf jedem Puzzleteil: „Ich gehöre an Stelle 7."

---

## 6. Schritt 4: Aufmerksamkeit – Was gehört zusammen?

Jetzt kommt das spannendste und wichtigste Konzept des Transformers: die **Attention** (auf Deutsch: Aufmerksamkeit).

### Ein Rätsel zum Einstieg

Lies diesen Satz: *„Die Schülerin, die gerade angekommen war, legte ihre Tasche ab."*

Auf wen bezieht sich „ihre"? Natürlich auf die Schülerin! Aber woher weißt du das? Du hast automatisch erkannt, dass „ihre" und „Schülerin" zusammengehören – obwohl sie nicht nebeneinanderstehen.

Genau das macht die KI mit Attention: Sie berechnet für jedes Wort, **welche anderen Wörter im Satz für seine Bedeutung wichtig sind**.

### Das Prinzip: Suchen und Finden

Für jedes Wort berechnet die KI drei Dinge:

```
QUERY (Q)  → "Wonach suche ich?"    (Die Suchanfrage)
KEY   (K)  → "Was biete ich an?"    (Das Schlagwort)
VALUE (V)  → "Was ist mein Inhalt?" (Die eigentliche Info)
```

**Stell dir eine Bibliothek vor:**

- Du hast eine **Suchanfrage** (Query): „Ich suche etwas über Tiere."
- Jedes Buch hat ein **Schlagwort** (Key) auf dem Rücken: „Biologie", „Tiere", „Physik", ...
- Wenn Suchanfrage und Schlagwort gut passen → hohes Attention-Gewicht
- Dann bekommst du den **Inhalt** (Value) des Buches

```
Beispiel:
Satz: "Der Fluss war ruhig und die Bank schön."

"Bank" fragt (Query):  "Was beschreibt mich näher?"
"Fluss" antwortet (Key): "Ich! Wir sind beide am Wasser."
"schön" antwortet (Key): "Ich auch! Ich beschreibe Bank."

→ "Bank" = wahrscheinlich eine Sitzbank am Fluss, nicht eine Bank mit Geld!
```

Die KI berechnet für jedes Wort, welche anderen Wörter am wichtigsten sind – und fasst diese Informationen dann zusammen.

### Attention als Tabelle

Das Ergebnis der Attention-Berechnung kann man als Tabelle darstellen. Jede Zahl zeigt, wie stark ein Wort auf ein anderes „aufmerksam" ist (0 = gar nicht, 1 = sehr stark):

```
         "Die"  "Bank"  "am"   "Fluss"  "ist"  "schön"
"Bank"  [ 0.05,  0.20,  0.15,   0.35,   0.05,   0.20 ]
                                 ↑
                    "Bank" schaut am stärksten auf "Fluss"
```

---

## 7. Schritt 5: Mehrere Blickwinkel gleichzeitig

Ein einziger Attention-Mechanismus kann immer nur **eine Art von Beziehung** auf einmal erkennen. Deshalb führt die KI die Attention-Berechnung mehrmals parallel durch – mit unterschiedlichen „Brillen".

### Die Brillen-Analogie

Stell dir vor, du liest einen Text mit verschiedenen Brillen:

- 🔵 **Brille 1** achtet auf grammatikalische Beziehungen: Wer macht was?
- 🟢 **Brille 2** achtet auf Bedeutungsähnlichkeiten: Welche Wörter bedeuten Ähnliches?
- 🔴 **Brille 3** achtet auf Pronomen: Auf wen bezieht sich „er", „sie", „es"?
- 🟡 **Brille 4** achtet auf Zeitformen: Was ist Vergangenheit, was Gegenwart?

Jede „Brille" ist ein **Attention-Kopf** (englisch: Head). Moderne KI-Modelle haben oft 8, 16 oder sogar 96 solcher Köpfe gleichzeitig.

```
Alle Attention-Köpfe arbeiten gleichzeitig
    ↓
Ergebnisse werden zusammengeführt
    ↓
Ein verfeinertes Gesamtbild des Textes
```

Das heißt im Englischen **Multi-Head Attention** – Aufmerksamkeit mit mehreren Köpfen.

---

## 8. Schritt 6: Wissen verarbeiten

Nach der Attention-Berechnung hat jedes Wort einen neuen Vektor, der **kontextbewusst** ist – es weiß jetzt, in welchem Zusammenhang es steht.

Dieser Vektor wird dann durch ein kleines, klassisches neuronales Netz geschickt – das sogenannte **Feed-Forward-Netzwerk**. Es verarbeitet die gesammelten Informationen und bereitet sie für die nächste Schicht vor.

### Das Schichten-Prinzip

Ein Transformer-Modell besteht nicht aus einem einzigen Attention-Block, sondern aus vielen übereinandergestapelten Schichten:

```
Eingabe
  ↓
[Schicht 1: Attention + Feed-Forward]
  ↓
[Schicht 2: Attention + Feed-Forward]
  ↓
[Schicht 3: Attention + Feed-Forward]
  ↓
 ... (bis zu 96 oder mehr Schichten!)
  ↓
Ausgabe
```

Jede Schicht verfeinert das Verständnis des Textes ein bisschen mehr – ähnlich wie beim Malen, wo man zuerst eine grobe Skizze macht und sie dann immer detaillierter ausarbeitet.

> **Wusstest du?** Große Modelle wie GPT-4 haben über 100 solcher Schichten und Milliarden von Parametern (lernbaren Zahlen). Würde man all diese Zahlen ausdrucken, bräuchte man tausende Bücher.

---

## 9. Wie lernt die KI überhaupt?

Bis jetzt haben wir beschrieben, wie ein fertiger Transformer funktioniert. Aber wie kommt er zu seinem Wissen?

### Das Training: Lückentext im Riesenmaßstab

Die KI trainiert auf einem riesigen Textkorpus – Bücher, Webseiten, Artikel, Wikis, ... – und lernt eine einfache Aufgabe:

> **„Welches Wort kommt als nächstes?"**

```
Text:  "Die Sonne scheint und der Himmel ist ___"

KI-Vorhersage:  "blau"  (wahrscheinlichste Fortsetzung)
Richtige Antwort: "blau"  ✅  → keine Anpassung nötig

Andere Vorhersage: "grün"  ❌  → KI-Gewichte werden angepasst
```

Dieser Vorgang wird **Milliarden von Mal** wiederholt – auf riesigen Textmengen. Nach und nach lernt die KI, welche Wörter in welchen Zusammenhängen wahrscheinlich kommen.

### Wie werden Fehler korrigiert?

Wenn die KI falsch liegt, wird die Stärke der Verbindungen zwischen den Rechenschritten leicht angepasst – ähnlich wie du beim Lernen deine Notizen verbessert oder Fehler in Aufgaben korrigierst.

Dieser Vorgang heißt **Backpropagation** (Rückwärtsdurchlauf): Der Fehler wird rückwärts durch das Netzwerk „zurückgeschickt" und alle Gewichte werden ein winziges Bisschen verbessert.

### Wie lange dauert das Training?

Das Training großer KI-Modelle dauert **Wochen oder Monate** – auf Tausenden von leistungsstarken Spezialcomputern (GPUs). Das kostet enorm viel Strom und ist sehr teuer.

```
Trainingstext: Hunderte Milliarden Wörter
               (ca. so viel, wie ein Mensch in 300.000 Jahren lesen würde)
Trainingszeit: Mehrere Wochen auf tausenden Computern
Parameter:     Milliarden von lernbaren Zahlen
```

### Nach dem Training: Feinabstimmung

Nachdem die KI auf dem riesigen Textkorpus vortrainiert wurde, wird sie noch speziell auf hilfreiche Antworten **feinabgestimmt** – zum Beispiel, indem Menschen verschiedene Antworten miteinander vergleichen und sagen, welche besser ist.

---

## 10. Bekannte KI-Modelle und was sie können

| Modell | Entwickler | Besonderheit |
|--------|-----------|--------------|
| **ChatGPT / GPT-4** | OpenAI | Sehr bekannt, kann auch Bilder verstehen |
| **Claude** | Anthropic | Fokus auf Sicherheit und Ehrlichkeit |
| **Gemini** | Google | Integriert in Google-Produkte |
| **BERT** | Google | Gut für Text-Verständnis, nicht für Generieren |
| **LLaMA** | Meta | Quellcode frei zugänglich (Open Source) |

### Für was werden Transformer eingesetzt?

- **Texte schreiben:** Aufsätze, E-Mails, Geschichten, Code
- **Übersetzen:** Zwischen fast allen Sprachen der Welt
- **Zusammenfassen:** Lange Texte auf das Wesentliche kürzen
- **Fragen beantworten:** Faktisches Wissen abrufen (mit Vorsicht!)
- **Code generieren:** Programme schreiben und Fehler finden
- **Medizin:** Krankheitsbilder aus Texten analysieren

---

## 11. Was kann ein Transformer (noch) nicht?

KI-Modelle sind beeindruckend – aber sie haben auch klare Grenzen:

### 🚫 Halluzinationen

KI-Modelle erfinden manchmal Fakten, die falsch oder komplett ausgedacht sind – aber trotzdem sehr überzeugend klingen. Das nennt man **Halluzination**.

```
Frage: "Wer hat den Roman 'Die Katzenjagd' geschrieben?"
KI:    "Der Roman 'Die Katzenjagd' wurde 1923 von Friedrich Müller geschrieben."

Problem: Dieser Roman und dieser Autor existieren gar nicht!
```

**Tipp:** Wichtige Informationen immer in einer echten Quelle nachprüfen!

### 🚫 Kein echtes Verstehen

Die KI versteht Sätze nicht wirklich – sie erkennt Muster. Das merkt man bei Aufgaben, die echtes logisches Denken erfordern:

```
Aufgabe: "Lisa ist größer als Tom. Tom ist größer als Anna.
          Wer ist am kleinsten?"

Für Menschen: Klar – Anna!
Für KI: Muss Muster aus Training finden. Gelingt mal gut, mal nicht.
```

### 🚫 Kein Gedächtnis zwischen Gesprächen

Wenn du ein neues Gespräch mit einer KI anfängst, erinnert sie sich nicht an das letzte. Jedes Gespräch beginnt „von vorne".

### 🚫 Wissen hat ein Ablaufdatum

Die KI wurde bis zu einem bestimmten Zeitpunkt trainiert. Was danach passiert ist, weiß sie nicht.

---

## 12. Zusammenfassung – Das Wichtigste auf einen Blick

```
WIE EIN TRANSFORMER FUNKTIONIERT

Schritt 1 – TOKENISIERUNG
  Text wird in kleine Teilstücke (Tokens) zerlegt
  Jedes Token bekommt eine Zahl-ID

Schritt 2 – EMBEDDING
  Jede Zahl-ID wird in einen Bedeutungsvektor umgewandelt
  Ähnliche Wörter → ähnliche Vektoren

Schritt 3 – POSITIONAL ENCODING
  Jeder Vektor bekommt eine "Platznummer" im Satz

Schritt 4 – SELF-ATTENTION ⭐ (Das Herzstück!)
  Für jedes Wort wird berechnet: Welche anderen Wörter sind wichtig?
  Query, Key, Value → Attention-Gewichte → gewichtete Zusammenfassung

Schritt 5 – MULTI-HEAD ATTENTION
  Mehrere Attention-Berechnungen gleichzeitig (verschiedene "Brillen")

Schritt 6 – FEED-FORWARD-NETZWERK
  Wissen wird weiterverarbeitet und verdichtet

→ Das alles wiederholt sich in vielen Schichten übereinander!

TRAINING
  Aufgabe: "Welches Wort kommt als nächstes?"
  Milliarden von Wiederholungen → Fehler werden korrigiert
  Resultat: Ein Modell mit Milliarden gelernter Zahlen (Gewichte)
```

---

## 13. Aufgaben und Experimente

### 🟢 Leichte Aufgaben

**Aufgabe 1 – Tokenizer ausprobieren**  
Gehe auf [platform.openai.com/tokenizer](https://platform.openai.com/tokenizer) und probiere folgendes aus:
- Gib das Wort „Donaudampfschifffahrtsgesellschaft" ein. In wie viele Tokens wird es zerlegt?
- Gib „Hund" und „Dog" ein. Bekommst du die gleiche Anzahl von Tokens?
- Was fällt dir bei deutschen Wörtern im Vergleich zu englischen auf?

**Aufgabe 2 – Attention im Alltag**  
Lies den Satz: *„Der alte Mann, der jeden Tag durch den Park spazierte, verlor seinen Hut."*  
Welche Wörter gehören zusammen? Zeichne Verbindungslinien zwischen Wörtern, die sich inhaltlich aufeinander beziehen!

**Aufgabe 3 – Halluzinationen testen**  
Stelle einer KI (z. B. ChatGPT oder Claude) folgende Frage: *„Welche Bücher hat der Autor Max Mustermann geschrieben?"*  
Was antwortet die KI? Ist die Antwort korrekt?

---

### 🟡 Mittlere Aufgaben

**Aufgabe 4 – Bedeutungs-Koordinaten**  
Zeichne ein Koordinatensystem mit zwei Achsen deiner Wahl (z. B. „lebt im Wasser / lebt an Land" und „ist ein Tier / ist eine Pflanze"). Platziere folgende Wörter im Koordinatensystem: *Delfin, Eiche, Adler, Hai, Tannenbaum, Pinguin.*

**Aufgabe 5 – Reihenfolge ist wichtig**  
Schreibe 5 eigene Beispielsätze, bei denen die Reihenfolge der Wörter die Bedeutung komplett verändert. Warum ist Positional Encoding also so wichtig?

**Aufgabe 6 – Grenzen der KI**  
Stelle einer KI eine Rechenaufgabe, die logisches Denken erfordert, z. B.: *„Ich habe 3 rote und 5 blaue Socken in einer Schublade. Wie viele Socken muss ich mindestens herausziehen, um sicher ein Paar gleicher Farbe zu haben?"*  
Beantwortet die KI die Frage richtig? Teste mehrere Aufgaben dieser Art.

---

### 🔴 Schwierige Aufgaben (für Schnelle)

**Aufgabe 7 – Selbst ein Mini-Embedding bauen**  
Wähle 6 Wörter und ordne ihnen jeweils zwei Eigenschaften zu (z. B. „Tier: ja/nein" und „kann fliegen: ja/nein"). Stelle das Ergebnis als Tabelle und als Diagramm dar. Was fällt dir auf, wenn du die Punkte im Koordinatensystem verbindest?

**Aufgabe 8 – Vergleich von KI-Modellen**  
Stelle dieselbe Frage drei verschiedenen KI-Modellen (z. B. ChatGPT, Claude, Gemini). Vergleiche die Antworten:  
- Welche Antwort ist am ausführlichsten?  
- Welche Antwort klingt am überzeugendsten?  
- Welche Antwort ist am korrektesten (nachgeprüft mit einer anderen Quelle)?

---

### 💬 Diskussionsfragen für die Klasse

1. Stell dir vor, dein Lehrer weiß nicht, ob ein Aufsatz von dir oder von einer KI geschrieben wurde. Ist das ein Problem? Warum (nicht)?
2. KI-Modelle lernen aus Texten im Internet – auch aus Texten, die falsch oder beleidigend sind. Was könnte dabei schiefgehen?
3. Das Training eines großen KI-Modells verbraucht so viel Strom wie eine kleine Stadt in einem Monat. Ist das vertretbar? Was sollte man abwägen?
4. Wenn eine KI eine falsche Information liefert und jemand Schaden dadurch nimmt – wer ist verantwortlich? Der Nutzer, das Unternehmen, die KI?

---

> 📚 **Möchtest du mehr wissen?**  
> Schau dir die weiterführende Dokumentation an: *Transformer – Vertiefung für Lehrkräfte und Interessierte*  
> Dort findest du die Mathematik hinter den Konzepten, die du hier kennengelernt hast.

---

*Dokument erstellt für den Einsatz im Informatikunterricht, Gymnasium Bayern, Klasse 8–9.*
