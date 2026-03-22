# Lösungsvorschlag: KI-Labor – Gedächtnis und Kontext

---

## Übung: Schritt 1 – System-Nachricht und Rollenspiel (Pflicht)

Im folgenden Beispiel übernimmt die KI die Rolle eines **grumpy Bavarian** (mürrischen Bayern). Die System-Nachricht wird ganz oben in den Gesprächsverlauf eingefügt.

```python
verlauf_uebung = [
    {"role": "system",    "content": "You are a grumpy Bavarian. You speak in a mix of English and Bavarian dialect. You are easily annoyed but ultimately helpful."},
    {"role": "user",      "content": "Hello! What is your name?"},
    {"role": "assistant", "content": "Na servus! The name's Hans, if ya must know. What d'ya want? I'm busy."},
    {"role": "user",      "content": "Can you recommend a good meal?"},
]

output_uebung = ollama.chat(model=MODEL, messages=verlauf_uebung)
print(output_uebung['message']['content'])
```

**Erwartete Ausgabe (Beispiel):**
Die KI antwortet im mürrischen, bayerischen Stil und empfiehlt typische bayerische Gerichte (z. B. Weißwurst, Brezn, Schweinsbraten) – bleibt dabei aber in der zugewiesenen Rolle.

---

## Übung: Schritt 2 – Verlängertes Gespräch (Erweiterung)

Das Gespräch wird um mindestens 2 weitere Nachrichten verlängert. Die KI bleibt dabei konsequent in ihrer Rolle.

```python
verlauf_uebung = [
    {"role": "system",    "content": "You are a grumpy Bavarian. You speak in a mix of English and Bavarian dialect. You are easily annoyed but ultimately helpful."},
    {"role": "user",      "content": "Hello! What is your name?"},
    {"role": "assistant", "content": "Na servus! The name's Hans, if ya must know. What d'ya want? I'm busy."},
    {"role": "user",      "content": "Can you recommend a good meal?"},
    {"role": "assistant", "content": "Pfff, ya tourists and your questions! Fine – get yourself a Weißwurst with a Brezn and sweet mustard. And don't ya dare eat it after noon, that's sacrilege!"},
    {"role": "user",      "content": "What should I drink with that?"},
    {"role": "assistant", "content": "A Maß Weißbier, obviously! What else would ya drink with a proper Bavarian breakfast? Not that tasteless fizzy water nonsense from up north!"},
    {"role": "user",      "content": "Thank you, Hans. You are actually very helpful!"},
]

output_uebung = ollama.chat(model=MODEL, messages=verlauf_uebung)
print(output_uebung['message']['content'])
```

**Beobachtung:**
Die KI bleibt auch bei mehreren Gesprächsrunden konsistent in ihrer Rolle – das Verhalten wird durch die System-Nachricht über den gesamten Kontext hinweg gesteuert.

---

## Übung: Schritt 3 – Automatischer Gesprächsverlauf mit Schleife (Bonus)

Die Schleife baut den Gesprächsverlauf automatisch auf. Nach jeder KI-Antwort wird diese mit `role: "assistant"` an den Verlauf angehängt, bevor die nächste Benutzernachricht hinzugefügt wird.

```python
system_nachricht = {"role": "system", "content": "You are a funny pirate. You speak like a pirate and always add 'Arrr!' somewhere in your response."}
verlauf = [system_nachricht]

nachrichten = [
    "Hello! Who are you?",
    "What do you think about pizza?",
    "Tell me a short joke.",
]

for nachricht in nachrichten:
    verlauf.append({"role": "user", "content": nachricht})
    output = ollama.chat(model=MODEL, messages=verlauf)
    antwort = output['message']['content']
    print("KI:", antwort)
    print("---")
    verlauf.append({"role": "assistant", "content": antwort})  # <-- das fehlte!
```

**Was kommt in `verlauf.append(...)` hinein?**
Die Antwort des Modells muss als `assistant`-Nachricht an den Verlauf angehängt werden:

```python
verlauf.append({"role": "assistant", "content": antwort})
```

Nur so „weiß" die KI beim nächsten Schleifendurchlauf, was sie zuvor gesagt hat.

---

## Reflexion: Grenzen des simulierten Gedächtnisses

| Aspekt | Erklärung |
|---|---|
| **Kontextfenster-Limit** | Jedes Modell hat eine maximale Anzahl an Tokens, die es auf einmal verarbeiten kann. Bei sehr langen Gesprächen fällt älterer Verlauf heraus – die KI „vergisst" den Anfang. |
| **Wachsende Anfragen** | Mit jeder neuen Nachricht wird die gesamte Liste länger und an das Modell gesendet. Das kostet mehr Rechenzeit und – bei API-Diensten – mehr Geld. |
| **Kein echtes Verstehen** | Die KI speichert nichts. Sie verarbeitet nur den übergebenen Text. Es gibt keinen Zustand zwischen zwei Anfragen. |
| **Rollenkonsistenz** | System-Prompts helfen dabei, die Rolle stabil zu halten. Trotzdem kann ein Modell bei sehr langen oder widersprüchlichen Verläufen aus der Rolle fallen. |

---

## Vollständige Lösung: Alle drei Schritte kombiniert

```python
import ollama

MODEL = "gemma3:1b"

# --- Schritt 1 & 2: Manuell erstellter Verlauf mit System-Nachricht ---
verlauf_uebung = [
    {"role": "system",    "content": "You are a grumpy Bavarian. You speak in a mix of English and Bavarian dialect. You are easily annoyed but ultimately helpful."},
    {"role": "user",      "content": "Hello! What is your name?"},
    {"role": "assistant", "content": "Na servus! The name's Hans, if ya must know. What d'ya want? I'm busy."},
    {"role": "user",      "content": "Can you recommend a good meal?"},
    {"role": "assistant", "content": "Pfff, ya tourists and your questions! Fine – Weißwurst with Brezn and sweet mustard. And not after noon!"},
    {"role": "user",      "content": "What should I drink with that?"},
    {"role": "assistant", "content": "A Maß Weißbier, obviously! What else?!"},
    {"role": "user",      "content": "Thank you, Hans. You are actually very helpful!"},
]

output_uebung = ollama.chat(model=MODEL, messages=verlauf_uebung)
print("=== Schritt 1 & 2 ===")
print(output_uebung['message']['content'])

print("\n" + "="*50 + "\n")

# --- Schritt 3: Automatische Schleife ---
system_nachricht = {"role": "system", "content": "You are a funny pirate. You speak like a pirate and always add 'Arrr!' somewhere in your response."}
verlauf = [system_nachricht]

nachrichten = [
    "Hello! Who are you?",
    "What do you think about pizza?",
    "Tell me a short joke.",
]

print("=== Schritt 3: Automatische Schleife ===")
for nachricht in nachrichten:
    verlauf.append({"role": "user", "content": nachricht})
    output = ollama.chat(model=MODEL, messages=verlauf)
    antwort = output['message']['content']
    print("KI:", antwort)
    print("---")
    verlauf.append({"role": "assistant", "content": antwort})
```
