# J.A.R.V.I.S - Offline + Online PC Assistant

## 1. Install (Windows 10/11; Mac/Linux work too)
1. Install Python 3.10+ from python.org (tick "Add Python to PATH").
2. Put this folder somewhere, e.g. `C:\Jarvis`.
3. Open Command Prompt in the folder: `pip install -r requirements.txt`

## 2. Activate
Double-click `run_jarvis.bat` (or `python jarvis.py`, then open http://127.0.0.1:5005).

## 3. Turn on the online brain (do anything you say)
1. Get an API key at console.anthropic.com.
2. Run once in Command Prompt, then reopen your terminal:
   `setx ANTHROPIC_API_KEY "your-key-here"`
Online, JARVIS understands any request and can open apps/links, take notes, draft mail, and run commands (always asks your permission first).

## 4. Offline chat brain (optional)
Install Ollama (ollama.com), then run `ollama pull llama3.2`. When the internet is down JARVIS uses it automatically.

## 5. Offline voice (optional)
1. `pip install vosk sounddevice`
2. Download `vosk-model-small-en-us` from alphacephei.com/vosk/models, unzip, rename the folder to `vosk-model`, put it in `C:\Users\<you>\Jarvis\`.
3. Restart JARVIS and say "Jarvis, open notepad". (The MIC button uses the browser's online speech, so use Vosk for offline voice.)

## 6. Start with Windows
Press Win+R, type `shell:startup`, and drop a shortcut to `run_jarvis.bat` there.

## Commands that work offline
- open notepad / open chrome / open downloads / open <file name>
- note <text>, read my notes (saved in `~/Jarvis/notes`)
- email to name@x.com about meeting saying see you at 5 (opens your mail app with a draft)
- find <file name>, system status, what time is it, what's the date
- search <query> (needs internet)

Customize apps and sites in the `APPS` and `SITES` dictionaries at the top of `jarvis.py`.

## Always-on listening
JARVIS listens continuously. Say "Jarvis, open notepad". Online it uses your browser's speech recognition (allow the microphone once);
offline it uses Vosk (step 5/6) automatically if the `vosk-model` folder exists. Toggle LISTEN, VOICE and colors from the top bar / CUSTOMIZE panel.

## Email access (read, summarize, send)
Your Anthropic key cannot open a mailbox; email uses your mail account's own login via IMAP/SMTP.
1. Gmail: turn on 2-Step Verification, then create an **App password** at myaccount.google.com/apppasswords (use this, never your real password).
2. In Command Prompt run (then reopen the terminal):
   setx JARVIS_MAIL_USER "you@gmail.com"
   setx JARVIS_MAIL_PASS "your-16-letter-app-password"
   Other providers also need: setx JARVIS_IMAP_HOST "imap.yourprovider.com" (and JARVIS_SMTP_HOST / JARVIS_SMTP_PORT=587 if needed).
3. Say: "check my email", "read email 2", "read my latest email", "summarize my email", "send email to sam@x.com about meeting saying see you at 5" (asks you to confirm before sending).
Weather needs no key: "weather in London" (or setx JARVIS_CITY "YourCity" for a default).

## Greeting, weather panel, battery warning
Open CUSTOMIZE and set your name, weather city and battery warning level (default 20%; a second, urgent warning comes at half that).
You can also say "Jarvis, call me Alex". Browsers only allow speech after you click or press a key once, so the spoken startup greeting plays on your first click or keypress.
