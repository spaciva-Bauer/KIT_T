## Arbeitsblatt: Prompt Engineering – Fortgeschrittene Interaktionsstrategien

**Fach:** KIT (T) | **Jahrgangsstufe:** 11 (FOS)

**Thema:** Dialoge führen, Ergebnisse verfeinern und Aufgaben strukturieren

| **Lernziele** Nach diesem Arbeitsblatt könnt ihr: - **Iteratives Prompting** einsetzen, um Ergebnisse durch gezielte Folgeprompts schrittweise zu verbessern - **Self-Reflection-Prompts** formulieren, damit das Sprachmodell die eigene Antwort kritisch überprüft und korrigiert - **Task Decomposition** anwenden, um komplexe Aufgaben in klar definierte Teilschritte zu zerlegen und nacheinander abzuarbeiten |
| - |


---

### A. Iteratives Prompting (Prompt Refinement)

| *„Ein Sprachmodell ist kein Automat, der auf Knopfdruck perfekte Ergebnisse liefert – es ist ein Gesprächspartner. Wer gezielt nachfragt und Feedback gibt, erhält deutlich bessere Ergebnisse als jemand, der einmalig einen langen Prompt schreibt und hofft."* |
| - |

**Wie funktioniert es?**

Statt alles in einen einzigen Prompt zu packen, führst du einen **Dialog**:

1. **Erster Prompt** → Ergebnis erhalten
2. **Feedback geben** → konkret benennen, was fehlt oder falsch ist
3. **Verbesserung anfordern** → gezielt nachsteuern
4. Schritt 2–3 so oft wiederholen, bis das Ergebnis passt

**Beispiel: Bewerbungsschreiben**

| **Prompt 1 (Ersteinstieg):** „Schreib mir ein kurzes Bewerbungsschreiben für eine Ausbildung als Fachinformatiker." |
| - |

| **Prompt 2 (Feedback):** „Das klingt zu allgemein. Mach es persönlicher: Ich heiße Lukas Meier, bin 17 Jahre alt, habe ein Schulpraktikum bei einer IT-Firma gemacht und interessiere mich besonders für Netzwerktechnik. Überarbeite das Schreiben entsprechend." |
| - |

| **Prompt 3 (Feinschliff):** „Gut, aber der Eröffnungssatz ist zu langweilig. Beginne stattdessen mit einer konkreten Erfahrung aus meinem Praktikum. Halte den Text auf maximal 150 Wörter." |
| - |

*Tipp: Je konkreter dein Feedback, desto gezielter die Verbesserung. Sage nicht nur „Das ist schlecht", sondern erkläre **warum** und **was** genau geändert werden soll.*

---

**Übung A1 – Iterativ zum Ziel**

Deine Schule plant einen Projekttag zum Thema „KI im Alltag". Du sollst einen kurzen Ankündigungstext für die Schulwebsite erstellen.

1. Starte mit einem einfachen Prompt ohne Details und notiere das Ergebnis.
2. Gib gezieltes Feedback (z. B. zu Länge, Ton, fehlenden Informationen) und fordere eine Überarbeitung an.
3. Verfeinere das Ergebnis in einem dritten Schritt noch einmal.

Protokolliere alle drei Prompts und halte die wichtigsten Änderungen fest:

| Prompt 1: | |
| - | - |
| Feedback / Prompt 2: | |
| Feinschliff / Prompt 3: | |
| Wichtigste Verbesserung: | |

---

### B. Self-Reflection-Prompting (Selbstkritik)

| *„Sprachmodelle machen Fehler – manchmal schleichen sich logische Widersprüche, falsche Fakten oder unklare Formulierungen ein. Mit einem Self-Reflection-Prompt forderst du das Modell auf, seine eigene Antwort kritisch zu überprüfen. Das verbessert die Qualität erheblich."* |
| - |

**Typische Self-Reflection-Anweisungen:**

- „Überprüfe deine Antwort auf logische Fehler und korrigiere sie."
- „Welche Annahmen hast du getroffen? Sind sie alle gültig?"
- „Gibt es Formulierungen, die missverständlich sein könnten? Verbessere sie."
- „Bewerte deine Antwort auf einer Skala von 1–10 und begründe die Bewertung."

**Beispiel: Fehlerhafte Erklärung korrigieren**

| **Prompt (direkt):** „Erkläre, warum WLAN schneller ist als ein Kabel." |
| - |

*Das Modell könnte eine sachlich falsche Antwort liefern (Kabel ist in der Regel schneller und stabiler). Anschließend:*

| **Self-Reflection-Prompt:** „Überprüfe deine Antwort. Enthält sie fachliche Fehler oder einseitige Darstellungen? Korrigiere sie und begründe deine Änderungen." |
| - |

---

**Übung B1 – Die KI auf den Prüfstand stellen**

1. Stelle dem Sprachmodell die folgende Frage direkt: *„Welche drei Programmiersprachen sollte man als Einsteiger zuerst lernen, und warum?"*

2. Notiere die Antwort.

3. Verwende anschließend diesen Self-Reflection-Prompt:
*„Überprüfe deine Empfehlung kritisch. Welche Argumente könnten dagegensprechen? Gibt es wichtige Aspekte, die du nicht berücksichtigt hast? Überarbeite deine Antwort."*

4. Vergleiche beide Antworten:

| Erste Antwort (Stichpunkte): | |
| - | - |
| Zweite Antwort (nach Reflexion): | |
| Was hat sich verbessert? | |

---

**Übung B2 – Eigene Fehler provozieren**

Stelle dem Modell eine Fangfrage, bei der es wahrscheinlich einen Fehler macht (z. B. eine Rechenaufgabe mit einem Trick, eine Formulierung, die absichtlich missverständlich ist, oder eine Frage mit falscher Prämisse).

*Beispiel für eine Fangfrage: „Wenn ein Zug mit 80 km/h von München nach Hamburg fährt und ein anderer Zug mit 100 km/h von Hamburg nach München, welcher Zug ist näher an München, wenn sie sich treffen?"*

1. Notiere die erste Antwort des Modells.
2. Fordere das Modell mit einem Self-Reflection-Prompt auf, die Antwort zu überdenken.
3. Hat das Modell seinen Fehler erkannt?

| Deine Fangfrage: | |
| - | - |
| Erste Antwort: | |
| Nach Reflexion: | |

---

### C. Task Decomposition (Aufgabenteilung)

| *„Wenn du einem Mitarbeiter eine komplizierte Aufgabe gibst, erklärst du sie nicht in einem einzigen, riesigen Satz – du zerlegst sie in klare Schritte. Genau das macht Task Decomposition: Komplexe Aufgaben werden in Teilaufgaben aufgeteilt, die das Modell nacheinander abarbeitet."* |
| - |

**Unterschied zu Chain-of-Thought:**

| | **Chain-of-Thought** | **Task Decomposition** |
| - | - | - |
| **Wer zerlegt?** | Das Modell selbst | Du als Nutzer |
| **Anweisung** | „Gehe Schritt für Schritt vor." | Du gibst explizite Teilaufgaben vor |
| **Wann sinnvoll?** | Logische Überlegungen | Komplexe, mehrstufige Projekte |

**Beispiel: Schulprojekt planen**

Statt eines einzigen langen Prompts werden drei separate Prompts gesendet:

| **Schritt 1:** „Erstelle eine Liste von 5 möglichen Themen für ein Schulprojekt über KI in der Medizin. Bewerte jedes Thema kurz nach Schwierigkeit und Verfügbarkeit von Informationen." |
| - |

| **Schritt 2 (nach Auswahl eines Themas):** „Ich habe mich für das Thema ‚KI-gestützte Diagnose bei Hautkrebs' entschieden. Erstelle eine Gliederung mit 5 Hauptpunkten für eine 10-minütige Präsentation." |
| - |

| **Schritt 3:** „Schreib für den ersten Gliederungspunkt ‚Wie funktioniert KI-Bilderkennung?' einen Einstiegstext von ca. 80 Wörtern, der für Mitschüler ohne Vorkenntnisse verständlich ist." |
| - |

---

**Übung C1 – Projekt Schritt für Schritt**

Du planst eine Umfrage in deiner Klasse zum Thema „Nutzung von KI-Tools im Alltag". Zerlege diese Aufgabe in mindestens **drei separate Prompts** und führe sie nacheinander durch.

| Teilaufgabe 1 (Was soll der erste Prompt leisten?): | |
| - | - |
| Prompt 1: | |
| Teilaufgabe 2: | |
| Prompt 2: | |
| Teilaufgabe 3: | |
| Prompt 3: | |

---

**Übung C2 – Chaos in Struktur verwandeln**

Dir liegt folgender Auftrag vor:

*„Erstelle für unsere Schul-AG eine komplette Social-Media-Kampagne für Instagram über den Tag der offenen Tür am 15. April: Themenideen, drei Beiträge mit Bildideen, einen Countdown-Post eine Woche vorher und eine kurze Anleitung, wann was gepostet werden soll."*

1. Zerlege diesen Auftrag in sinnvolle Teilaufgaben.
2. Formuliere für jede Teilaufgabe einen eigenen Prompt.
3. Führe die Prompts nacheinander durch und notiere, ob die Ergebnisse konsistenter sind als bei einem einzigen langen Prompt.

| Wie viele Teilaufgaben hast du identifiziert? | |
| - | - |
| War das Ergebnis besser als bei einem einzigen Prompt? Warum? | |

---

### Reflexion

Beantwortet die folgenden Fragen in Stichpunkten oder im Gespräch mit eurer Partnerin / eurem Partner:

| - In welchen Situationen ist **Iteratives Prompting** sinnvoller als ein einzelner, langer Prompt? - Warum kann ein Sprachmodell durch einen **Self-Reflection-Prompt** seine eigene Antwort verbessern – obwohl es doch denselben Text noch einmal liest? - Wann würdet ihr **Task Decomposition** gegenüber **Chain-of-Thought** bevorzugen? Begründet eure Antwort mit einem Beispiel. |
| - |

---

| **Abschließende Aufgabe (optional / Hausaufgabe): Der vollständige Workflow** Wählt eine komplexe, reale Aufgabe aus eurem Schulalltag (z. B. eine Facharbeit vorbereiten, ein Referat strukturieren, eine Tabellenkalkulation planen). Bearbeitet sie mit einem kombinierten Ansatz: 1. **Task Decomposition** – zerlegt die Aufgabe in Teilschritte 2. **Iteratives Prompting** – verfeinert mindestens einen Teilschritt durch zwei Folgeprompts 3. **Self-Reflection** – lasst das Modell das Endergebnis kritisch überprüfen Dokumentiert jeden Schritt und haltet fest, welche Technik den größten Mehrwert gebracht hat. |
| - |
