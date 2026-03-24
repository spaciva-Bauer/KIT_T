## Arbeitsblatt: Prompting im Unterricht

**Fach:** KIT (T) | **Jahrgangsstufe:** 11 (FOS)

**Thema:** Effiziente Kommunikation mit Large Language Models (LLMs)

### 1. Was ist ein "Prompt"?

Ein Prompt ist die Eingabeaufforderung an ein KI-System (häufig Sprachmodell). Während wir bei Suchmaschinen meist nur Schlagworte eingeben, funktioniert ein Sprachmodell wie ein **hochbegabter, aber kontextloser Assistent**. Je präziser du den Kontext beschreibst, desto besser ist das Ergebnis.

### 2. Das "R-K-A-F"-Modell

Um einen professionellen Prompt zu verfassen, hilft die Orientierung an dieser Struktur:

| **Komponente** | **Beschreibung** | **Beispiel** |
| - | - | - |
| **R**olle (Persona) | Weise der KI eine Identität zu. | "Handle als erfahrener Python-Entwickler." |
| **K**ontext | Gib Hintergrundinformationen. | "Ich lerne gerade Schleifen in der Schule." |
| **A**ufgabe | Was genau soll getan werden? | "Erkläre mir den Unterschied zwischen while und for." |
| **F**ormat | Wie soll die Ausgabe aussehen? | "Erstelle eine übersichtliche Tabelle." |


### 3. Übungsaufgaben

*Nutze dein Sprachmodell aus der ByCS (Lernplattform, Telli …), um die folgenden Aufgaben zu bearbeiten.*

**Aufgabe 1**

1. Frage das Sprachmodell ohne Kontext: *"Was ist ein Algorithmus?"*

2. Nutze nun das R-K-A-F-Modell: *"Du bist eine humorvolle Informatiklehrkraft. Als Thema des Unterrichts sollen Algorithmen behandelt werden. Erkläre einem Schüler bzw. einer Schülerin der Unterstufe, was ein Algorithmus im Alltagsbezug ist. Nutze Aufzählungszeichen."*

3. **Reflexion:** Notiere kurz den Hauptunterschied in der Qualität der Antworten.

4. Verändere nun gezielt die Rolle oder die Zielgruppe (z. B. für einen Erstklässler statt für einen Schüler der Unterstufe) und beobachte, wie sich die Antwort verändert.

|      |
| - |


**Aufgabe 2**

Überarbeite den folgenden „schlechten“ Prompt so, dass er spezifische Anforderungen enthält (z.B. Eingabe der Punkte, Gewichtung, Anzahl der Stellen im Ergebnis, HTML- oder Excel-Format usw.):

*Schlechter Prompt: "Schreib mir ein Programm für eine Notenberechnung."*


| Möglicher verbesserter Prompt:     |
| - |

**Selbstcheck: **Welche R-K-A-F-Komponenten hast du eingebaut? R ☐ K ☐ A ☐ F ☐



**Aufgabe 3: "Chain-of-Thought"**

Stell dir vor, du sollst eine komplizierte Matheaufgabe im Kopf lösen. Wenn du sofort das Endergebnis nennen musst, ist die Chance groß, dass du dich vertippst oder einen kleinen Logikfehler machst. Schreibst du aber jeden Zwischenschritt auf, bemerkst du Fehler oft selbst und kommst sicher ans Ziel. **Genau das passiert bei Chain-of-Thought!**

  
**3.1 Übung 1  
  
Der "schlechte" (direkte) Prompt:**

*"Wir planen eine Klassenfahrt für 25 Personen von München nach Berlin. Wir haben 2000 € Budget. Was ist die günstigste und umweltfreundlichste Option?"*


**Der Chain-of-Thought Prompt:**

*"Wir planen eine Klassenfahrt für 25 Personen von München nach Berlin. Wir haben 2000 € Budget. Was ist die günstigste und umweltfreundlichste Option?* **Gehe dabei Schritt für Schritt vor.**“


*Tipp: Achte darauf, wie klein der Unterschied zwischen den beiden Prompts ist – nur ein einziger Zusatz macht den Unterschied!*

Notiere kurz den Hauptunterschied in der Qualität der Antworten. Kommt das Sprachmodell zu unterschiedlichen Ergebnissen?

|       |
| - |



**3.2 Übung 2**

  
**Der "schlechte" (direkte) Prompt:**   
„Ein Bauer hat 17 Schafe. Alle außer 9 sterben. Wie viele Schafe bleiben übrig?“

1. Frage das Modell zuerst direkt nach der Antwort.

2. Verwende nun den Prompt mit der zusätzlichen Anweisung: „Analysiere das Problem Schritt für Schritt und achte genau auf die Formulierung 'Alle außer 9'.“

3. Notiere kurz den Hauptunterschied in der Qualität der Antworten. Kommt das Sprachmodell zu unterschiedlichen Ergebnissen?

|         |
| - |

**Aufgabe 4 – Transferaufgabe**

Wähle ein Thema aus einem anderen Unterrichtsfach und verfasse dazu einen vollständigen Prompt nach dem R-K-A-F-Modell. Teste ihn im Sprachmodell und halte das Ergebnis unten fest.

**Mein R-K-A-F-Prompt: **

|      |
| - |

