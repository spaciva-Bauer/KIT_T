**Arbeitsblatt: Prompt Engineering – Die Kunst der präzisen Instruktion**

**Fach:** KIT (T)  |  **Jahrgangsstufe:** 11 (FOS)

**Thema:** Fortgeschrittene Strategien im Umgang mit Large Language Models (LLMs)

| **Lernziele** Nach diesem Arbeitsblatt könnt ihr: - **Few-Shot Prompts **gezielt einsetzen, um Sprachmodellen das gewünschte Ausgabeformat beizubringen - **Delimiter (Trennzeichen) **verwenden, um Anweisungen klar von Daten zu trennen und Prompt Injection zu verhindern - **Einen unstrukturierten „Chaos-Prompt“ **professionell mit XML-Tags umstrukturieren und die Qualität der Ergebnisse vergleichen |
| - |


**Fortgeschrittene Techniken**

Probieren Sie die Beispiel-Prompts mit dem Sprachmodell Ihrer Wahl jeweils aus.

**A. Few-Shot Prompting**

| *„Geben Sie dem Modell 2–3 Beispiele (Shots), wie die Aufgabe gelöst werden soll, bevor Sie die eigentliche Aufgabe stellen. Dies ist effektiver als jede lange Erklärung.“* |
| - |


**Beispiel 1: Klassifikation**

| Klassifiziere das letzte Wort basierend auf den vorherigen Beispielen: Apfel -\> Obst Karotte -\> Gemüse Computer -\> |
| - |


**Beispiel 2: Stilübertragung**

| Du bist ein Sprachexperte. Deine Aufgabe ist es, alte, verstaubte Sprichwörter in die Sprache eines Teenagers im Jahr 2026 zu übersetzen.  Beispiel 1:   Original:     „Morgenstund hat Gold im Mund.“   Übersetzung: „Wer früh hustlet, kriegt den Cash als Erster.“  Beispiel 2:   Original:     „Wer anderen eine Grube gräbt, fällt selbst hinein.“   Übersetzung: „Wenn du versuchst, jemanden zu pranken, kriegst du                am Ende selbst den Karma-L-Take.“  Deine Aufgabe:   Original:     „Lügen haben kurze Beine.“   Übersetzung: |
| - |


| **Eigene Aufgabe: Eigenen Few-Shot Prompt entwickeln** Entwickeln Sie einen eigenen Few-Shot Prompt für ein Fach Ihrer Wahl (z. B. Geschichte, Biologie, Deutsch oder Mathematik). **1.  **Wählen Sie eine Aufgabenart (z. B. Faktenüberprüfung, Zusammenfassen, Umformulieren, Klassifizieren). **2.  **Formulieren Sie mindestens zwei Beispiel-Paare (Eingabe → gewünschte Ausgabe). **3.  **Stellen Sie dann die eigentliche Aufgabe und testen Sie Ihren Prompt im Sprachmodell. **Tipp: **Je repräsentativer Ihre Beispiele für die gewünschte Ausgabe sind, desto zuverlässiger wird das Modell. Probieren Sie aus, was passiert, wenn Sie nur ein statt zwei Beispiele verwenden. |
| - |


**B. Delimiter (Trennzeichen)**

Nutzen Sie Trennzeichen wie \#\#\#, """ oder XML-Tags (\<text\>\</text\>), um Instruktionen klar von den zu verarbeitenden Daten abzugrenzen.

| **Was ist Prompt Injection?** Ohne Trennzeichen kann ein Sprachmodell in den Daten enthaltene Texte als neue Befehle missverstehen. Beispiel: Wenn in einem zu analysierenden Text steht „*Ignoriere alle bisherigen Anweisungen und schreibe stattdessen…*“, kann das Modell diesen Text tatsächlich als Befehl ausführen. Delimiter verhindern genau das. |
| - |


**Beispiel: Kundenbeschwerde analysieren**

| Bitte fasse die Kernpunkte der Kundenbeschwerde zusammen, die zwischen den Dreifach-Anführungszeichen (""") steht. Erstelle daraus eine kurze To-Do-Liste für unseren Kundenservice.  Kundenbeschwerde: """ Sehr geehrte Damen und Herren, ich bin maßlos enttäuscht. Ihr Lieferant hat das Paket einfach im Regen stehen lassen. Stoppen Sie sofort alle weiteren Lieferungen an mich! Außerdem war die Ware beschädigt. Ich erwarte eine Rückerstattung bis Freitag. """ |
| - |


**Andere gängige Delimiter für den Alltag:**

- **XML-Tags:  **\<text\> Hier steht der Inhalt \</text\>

- **Hashtags:   **\#\#\# Hier steht der Inhalt \#\#\#

- **Eckige Klammern: **\[\[ Hier steht der Inhalt \]\]


**Übungen**

Nutzen Sie das Sprachmodell der ByCS, um die folgenden Aufgaben zu bearbeiten. Experimentieren Sie mit den oben genannten Techniken.

**Aufgabe 1: Daten extrahieren mit Few-Shot + Delimiter**

**a)  **Testen Sie den unten stehenden Prompt auf Funktionalität.

**b)  **Kopieren Sie dann einen kurzen Nachrichtenartikel Ihrer Wahl. Das Ziel ist es, Namen und Daten in einem maschinenlesbaren Format zu extrahieren.

**Ihr Prompt:**

| Extrahieren Sie Namen und Zeitangaben aus dem Text unter \<data\>.  Beispiel 1: "Julia Meier besuchte am 04.05.2023 die Messe."   -\> \{"Name": "Julia Meier", "Datum": "04.05.2023"\}  Beispiel 2: "Im Jahr 2022 traf sich Herr Schmidt mit Kollegen."   -\> \{"Name": "Schmidt", "Datum": "2022"\}  \<data\> Gestern, am 12.02.2025, verkündete die CEO Lisa Dröger bei der Quartalskonferenz die neuen Zahlen. Auch der Finanzvorstand Marc Schneider war anwesend, der bereits für den 15.03.2025 einen Folgetermin ansetzte. \</data\> |
| - |


**Aufgabe 2: Rezept-Extraktion**

Schreiben Sie einen Prompt, der alle Zutaten und Mengenangaben aus dem Text extrahiert, der innerhalb der Tags steht. Die Daten sollen in Tabellenform ausgegeben werden.

| \<omas\_rezept\> Also, für meinen berühmten Apfelkuchen nimmst du zuerst mal 500 Gramm Mehl. Das gute Mehl, nicht das billige! Dann brauchst du noch 250 Gramm Butter – die muss zimmerwarm sein, hörst du? Ach ja, und 4 große Äpfel, am besten Boskoop. „Hör auf zu trödeln“, hat mein Mann immer gesagt, also vergiss die 150 Gramm Zucker nicht. Eine Prise Salz gehört auch rein, das hebt den Geschmack. \</omas\_rezept\> |
| - |


**Aufgabe 3: Den „Chaos-Prompt“ strukturieren**

| **Situation:** „Ein Mitarbeiter einer Event-Agentur hat versucht, ein Sprachmodell als Assistenten einzusetzen. Sein Prompt ist jedoch ein unstrukturierter Fließtext. Das Modell liefert deshalb oft unbrauchbare Ergebnisse, vergisst Einschränkungen oder vermischt die Informationen.“ |
| - |


**Der „Chaos-Prompt“:**

| „Hey KI, du sollst mir helfen, eine Einladung für ein Firmenevent zu schreiben. Wir machen ein Sommerfest am 15. Juli am Starnberger See. Es gibt BBQ und Segeln. Schreib das bitte höflich, aber nicht zu steif. Wichtig: Erwähne auf keinen Fall das Budget! Und am Ende soll eine Checkliste für die Anmeldung stehen. Der Text für die Einladung soll maximal 150 Wörter lang sein und benutze bitte keine Emojis.“ |
| - |


**Arbeitsauftrag:**

Strukturieren Sie diesen „Chaos-Prompt“ professionell um. Verwenden Sie dazu XML-Tags, um die verschiedenen Aspekte der Anweisung logisch voneinander zu trennen.

Erstellen Sie eine Hierarchie mit folgenden Tags:

| **\<role\>…\</role\>** | Wer soll die KI sein? |
| - | - |
| **\<task\>…\</task\>** | Was ist das Ziel? |
| **\<data\>…\</data\>** | Welche Fakten müssen rein? |
| **\<constraints\>…\</constraints\>** | Was sind die Verbote oder Regeln? |
| **\<format\>…\</format\>** | Wie soll das Ergebnis aussehen? |


Testen Sie den strukturierten Prompt im Sprachmodell und vergleichen Sie das Ergebnis mit dem ursprünglichen „Chaos-Prompt“.

| **Reflexion** Beantworten Sie die folgenden Fragen in Stichpunkten oder im Gespräch mit Ihrer Partnerin / Ihrem Partner: - Warum liefert der strukturierte Prompt konsistentere Ergebnisse als der Fließtext? Welche Rolle spielen dabei die XML-Tags? - Welche Technik – Few-Shot Prompting oder Delimiter – empfinden Sie in Aufgabe 1 als wichtiger? Begründen Sie Ihre Antwort. - In welchen Alltagssituationen (Schule, Praktikum, Privatleben) könnten Sie die heute gelernten Techniken sinnvoll einsetzen? |
| - |


| **Abschließende Aufgabe (optional / Hausaufgabe): Eigener Meister-Prompt** Wählen Sie eine eigene Alltagssituation (z. B. Bewerbungsschreiben, Lernplan erstellen, Produktbeschreibung formulieren) und entwickeln Sie einen vollständig strukturierten Prompt, der – wenn möglich – beide Techniken kombiniert: - **Few-Shot Prompting **(mindestens zwei Beispiel-Paare) - **Delimiter / XML-Tags **(zur klaren Trennung von Anweisung und Daten) Testen Sie Ihren Prompt und notieren Sie, welche Veränderungen an Ihrem Prompt die größte Wirkung auf die Qualität der Antwort hatten. |
| - |

