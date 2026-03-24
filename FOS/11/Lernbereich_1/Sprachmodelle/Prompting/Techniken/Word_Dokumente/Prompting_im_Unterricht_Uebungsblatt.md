## Übungsblatt: Prompting im Unterricht – Alle Techniken

**Fach:** KIT (T) | **Jahrgangsstufe:** 11 (FOS)

**Hinweis:** Dieses Übungsblatt setzt die Inhalte aller drei Arbeitsblätter voraus. Nutze das Sprachmodell der ByCS für alle Aufgaben.

---

### Aufgabe 1 – R-K-A-F-Modell

Ein Freund möchte sich auf sein erstes Vorstellungsgespräch für einen IT-Ausbildungsplatz vorbereiten. Er hat keine Erfahrung mit solchen Gesprächen und weiß nicht, welche Fragen typischerweise gestellt werden.

Verfasse einen vollständigen Prompt nach dem R-K-A-F-Modell, der dem Sprachmodell die Aufgabe gibt, ein realistisches Übungsgespräch zu simulieren.

| Mein R-K-A-F-Prompt: | |
| - | - |
| **R** (Rolle): | |
| **K** (Kontext): | |
| **A** (Aufgabe): | |
| **F** (Format): | |
| Vollständiger Prompt: | |

**Selbstcheck:** Welche Komponenten hast du eingebaut? R ☐  K ☐  A ☐  F ☐

---

### Aufgabe 2 – Chain-of-Thought

Stelle dem Sprachmodell folgende Frage **zuerst direkt**, dann mit einer Chain-of-Thought-Anweisung:

*„Eine Schulklasse sammelt Geld für eine Klassenfahrt. 18 Schüler zahlen je 45 €, 6 Schüler zahlen je 30 €, weil sie Ermäßigung bekommen. Die Fahrt kostet insgesamt 1.080 €. Reicht das Geld? Wenn ja: Wie viel bleibt übrig?"*

| Direkte Antwort des Modells: | |
| - | - |
| Chain-of-Thought-Prompt (notiere ihn): | |
| Antwort mit Chain-of-Thought: | |
| Unterschied in der Qualität / Nachvollziehbarkeit: | |

---

### Aufgabe 3 – Few-Shot Prompting

Du willst das Sprachmodell trainieren, Social-Media-Kommentare automatisch in drei Kategorien einzuordnen: **Positiv**, **Negativ** oder **Neutral**.

1. Entwickle einen Few-Shot Prompt mit mindestens **zwei Beispielpaaren**.
2. Stelle dann folgende Kommentare zur Klassifikation:
   - *„Endlich mal ein Update, das nicht alles schlechter macht!"*
   - *„Weiß nicht, hab's noch nicht ausprobiert."*
   - *„Absoluter Müll, deinstalliert."*

| Mein Few-Shot Prompt (inkl. Beispiele): | |
| - | - |
| Ergebnis der Klassifikation: | |
| Was passiert, wenn du nur **ein** Beispiel verwendest? | |

---

### Aufgabe 4 – Delimiter & XML-Tags

Unten stehen Rohdaten aus einer Schülerumfrage – als unstrukturierter Fließtext. Schreibe einen Prompt mit XML-Tags, der das Sprachmodell anweist, die Daten in eine übersichtliche Tabelle mit den Spalten **Name**, **Klasse** und **Lieblingsapp** zu extrahieren.

```
<umfrage_daten>
Lisa Wagner aus der 11a nutzt am liebsten Spotify. Max Huber, ebenfalls 11a,
schwört auf YouTube. In der 11b ist es bei Fabian Ott Instagram und bei
Sarah Kern TikTok. Auch aus der 11b kommt Jonas Richter, dessen Favorit
WhatsApp ist.
</umfrage_daten>
```

| Mein Prompt (mit XML-Tags): | |
| - | - |
| Hat das Modell die Tabelle korrekt erstellt? | ☐ Ja  ☐ Nein – Fehler: |
| Was wäre passiert ohne Delimiter? | |

---

### Aufgabe 5 – Iteratives Prompting

Du willst eine kurze Produktbeschreibung für eine fiktive App entwickeln, die Schülern beim Lernen hilft.

1. **Prompt 1:** Bitte das Modell um eine erste Produktbeschreibung (max. 60 Wörter).
2. **Prompt 2:** Gib konkretes Feedback zu mindestens zwei Aspekten und fordere eine Überarbeitung.
3. **Prompt 3:** Verfeinere das Ergebnis ein letztes Mal (z. B. Anpassung des Tons oder der Zielgruppe).

| Prompt 1: | |
| - | - |
| Feedback / Prompt 2: | |
| Feinschliff / Prompt 3: | |
| Hauptunterschied zwischen Version 1 und Version 3: | |

---

### Aufgabe 6 – Self-Reflection

Stelle dem Sprachmodell folgende Frage:

*„Erkläre in drei Sätzen, wie das Internet funktioniert."*

1. Notiere die Antwort.
2. Verwende anschließend einen Self-Reflection-Prompt, um das Modell zur kritischen Überprüfung aufzufordern.
3. Bewertet das Modell seine eigene Antwort realistisch?

| Erste Antwort: | |
| - | - |
| Dein Self-Reflection-Prompt: | |
| Überarbeitete Antwort (Stichpunkte): | |
| War die Selbstkritik des Modells zutreffend? | ☐ Ja  ☐ Teilweise  ☐ Nein |

---

### Aufgabe 7 – Task Decomposition

Du planst mit einer Gruppe ein kurzes Erklär-Video (ca. 2 Minuten) zum Thema „Was ist ein Algorithmus?". Zerlege die Aufgabe in **mindestens vier Teilprompts** und führe sie nacheinander durch.

| Teilaufgabe 1: | |
| - | - |
| Prompt 1: | |
| Teilaufgabe 2: | |
| Prompt 2: | |
| Teilaufgabe 3: | |
| Prompt 3: | |
| Teilaufgabe 4: | |
| Prompt 4: | |
| War das Gesamtergebnis besser als ein einziger langer Prompt? Begründe kurz: | |

---

### Aufgabe 8 – Transferaufgabe (freie Aufgabe)

Wähle eine eigene Aufgabe aus deinem Schulalltag oder Privatleben (z. B. einen Lernplan erstellen, eine E-Mail formulieren, eine Präsentation vorbereiten) und bearbeite sie mit **mindestens drei verschiedenen Prompting-Techniken** aus diesem Kurs.

| Meine Aufgabe: | |
| - | - |
| Techniken, die ich eingesetzt habe: | 1. &nbsp;&nbsp;&nbsp; 2. &nbsp;&nbsp;&nbsp; 3. |
| Kurze Beschreibung meines Vorgehens: | |
| Was war die wirksamste Technik? Warum? | |

---

### Abschlussreflexion

| Beantworte die folgenden Fragen in Stichpunkten: - Welche der acht Techniken wirst du in Zukunft am häufigsten einsetzen? Begründe deine Wahl. - Bei welcher Aufgabe hat dich das Ergebnis des Sprachmodells am meisten überrascht (positiv oder negativ)? - Gibt es eine Situation, in der du **kein** Sprachmodell einsetzen würdest, obwohl es technisch möglich wäre? |
| - |
