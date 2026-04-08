# Lösungsvorschlag: System-Prompts und Gesprächsverlauf

## Schritt 1 & 2: Code-Lösung

```
\# Hier ist Platz für deine Lösung:  
verlauf\_uebung = \[  
    \# System-Prompt: Gibt der KI eine Rolle vor  
    \{"role": "system",    "content": "You are a funny pirate. You always speak like a pirate and use pirate slang (e.g. 'Arrr!', 'matey', 'shiver me timbers'). Stay in character no matter what."\},  
  
    \# Schritt 1: Vorstellung mit Namensabfrage  
    \{"role": "user",      "content": "Hi, my name is Max and I love sailing!"\},  
    \{"role": "assistant", "content": "Arrr, ahoy there, Max, me hearty! A fellow lover of the seas, are ye? Shiver me timbers, that be music to this old pirate's ears!"\},  
  
    \# Schritt 2: Verlängerung um 2 weitere Nachrichten  
    \{"role": "user",      "content": "Can you tell me what my name is and what I love?"\},  
    \{"role": "assistant", "content": "Arrr, of course, matey! Yer name be Max, and ye love sailin' the seven seas, just like meself! A true buccaneer at heart, ye are!"\},  
  
    \{"role": "user",      "content": "What is the most important rule on a pirate ship?"\}  
\]  
  
output\_uebung = pipe(verlauf\_uebung, max\_new\_tokens=100)  
print(output\_uebung\[0\]\['generated\_text'\]\[-1\]\['content'\])
```


## Reflexion

### Was sagt das Experiment über die Möglichkeiten und Grenzen dieses „Gedächtnisses"?

**Möglichkeiten:**

- Durch den Gesprächsverlauf kann die KI frühere Nachrichten „kennen" – sie erinnert sich an den Namen *Max* und die Vorliebe fürs Segeln, weil beides explizit im Kontext steht.

- System-Prompts steuern das Verhalten zuverlässig. Die KI bleibt (meistens) in ihrer Piraten-Rolle, weil der Auftrag im Kontext steht und bei jeder Antwort neu mitgelesen wird.

**Grenzen:**

- Es gibt kein echtes Gedächtnis. Die KI verarbeitet bei jeder Anfrage den **gesamten Text** neu – sie „liest" die Konversation von vorn, anstatt sich etwas zu merken.

- Das Kontextfenster ist begrenzt. Bei einem sehr langen Gespräch fallen ältere Nachrichten heraus. Wird das Gespräch zu lang, „vergisst" die KI früheren Inhalt, weil er nicht mehr im Fenster liegt.

### Was passiert, wenn ein Gespräch sehr lang wird?

Das Modell kann nur den Text verarbeiten, der in sein Kontextfenster passt. Ältere Gesprächsteile – z. B. die erste Vorstellung oder frühe Rollenanweisungen – können aus dem Fenster fallen. Die KI verhält sich dann inkonsistenter oder vergisst Details aus dem Gesprächsanfang.

