# Lösungsvorschlag: OpenAI Chatbot Notebook

---

## Aufgabe 1 – Pirat

Die `system`-Rolle legt die Persönlichkeit der KI fest. Ersetze `"___"` durch eine passende Beschreibung:

```python
# Aufgabe 1: Pirat
verlauf_pirat = [
    {"role": "system",    "content": "Du bist ein mürrischer, alter Pirat. Du sprichst grob, verwendest Seemannssprache wie 'Arrr' und 'Käptn', und bist von allem genervt."},
    {"role": "user",      "content": "Hallo! Wer bist du?"},
]

antwort = client.chat.completions.create(
  model="gpt-4o-mini",
  messages=verlauf_pirat
)

print("KI-Antwort: " + antwort.choices[0].message.content)
```

**Was ändert sich?**
Ton und Sprache der KI passen sich der neuen Rolle an: Die Antworten werden kurz und grantig, durchsetzt mit Piratenfloskeln. Das zeigt, wie stark die `system`-Rolle das Verhalten des Modells steuert – ohne dass sich das eigentliche Modell ändert.

---

## Aufgabe 2 – Warum wird der Chat teurer?

**Antwort:**
Je länger ein Gespräch dauert, desto mehr Nachrichten enthält die Variable `verlauf`. Da bei jedem neuen API-Aufruf der **gesamte bisherige Verlauf** mitgeschickt werden muss, wächst die Menge der übertragenen Tokens mit jeder Runde.

OpenAI berechnet Kosten pro **1.000 Tokens** (Ein-/Ausgabe). Ein langer `verlauf` bedeutet also:

```
Aufruf 1:  2 Nachrichten  →  ~  50 Tokens
Aufruf 5:  10 Nachrichten →  ~ 300 Tokens
Aufruf 20: 40 Nachrichten →  ~ 1500 Tokens
```

Die Kosten steigen **kumulativ** – nicht linear pro Nachricht, sondern mit dem gesamten Verlauf.

---

## Aufgabe 3 – Hobby im Verlauf ergänzen

Ergänze die beiden `"___"`-Platzhalter mit einer Hobby-Aussage des Users und einer passenden Reaktion des Assistenten:

```python
# Aufgabe 3: Hobby im Verlauf ergänzen
verlauf_hobby = [
    {"role": "system",    "content": "Du bist ein hilfreicher Assistent."},
    {"role": "user",      "content": "Hallo, ich bin Max."},
    {"role": "assistant", "content": "Hallo Max! Schoen, dich kennenzulernen."},
    {"role": "user",      "content": "Mein Hobby ist Klettern."},           # <- Hobby
    {"role": "assistant", "content": "Oh, wie spannend! Kletterst du lieber in der Halle oder draußen an echten Felsen?"},  # <- passende Antwort
    {"role": "user",      "content": "Was weisst du alles ueber mich?"}
]

antwort = client.chat.completions.create(
  model="gpt-4o-mini",
  messages=verlauf_hobby
)

print("KI-Antwort: " + antwort.choices[0].message.content)
```

**Erwartetes Ergebnis:**
Die KI nennt sowohl den Namen „Max" als auch das Hobby „Klettern" – weil beides im mitgeschickten `verlauf` enthalten ist. Das Modell selbst hat nichts gespeichert; es liest den Verlauf einfach neu.
