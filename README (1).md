# Voice Assistant with Claude API

A voice assistant written in Python and run in a Jupyter Notebook. It listens to your microphone, turns your speech into text, and answers out loud. Common commands are handled directly. Everything else is sent to the Claude API, which gives a short answer that is spoken back.

## Features

- Speech to text with Google Speech Recognition (needs internet)
- Text to speech with `pyttsx3` (works offline)
- Built-in commands:
  - greetings, current time, and today's date
  - open Google or YouTube, and search Google by voice
  - open Word, Notepad, and Calculator
  - take a screenshot (saved to your Desktop)
  - shut down, restart, lock, or sleep the computer, with a 10-second delay to cancel (say "cancel")
  - exit by saying "exit", "stop", or "quit"
- Any other question is sent to Claude (`claude-haiku-4-5`) and the answer is read aloud
- Error handling for unclear speech and network problems

## Requirements

- Windows (the app and system commands use Windows tools)
- Python 3.8 or newer, and Jupyter Notebook or JupyterLab
- A working microphone and speakers
- An Anthropic API key from [console.anthropic.com](https://console.anthropic.com)

Install the packages:

```bash
pip install SpeechRecognition pyttsx3 pyaudio pillow anthropic
```

If `pyaudio` fails to install, try `pip install pipwin` and then `pipwin install pyaudio`.

## Set your API key (important)

Never write your API key in the code or upload it to GitHub. Anyone who finds it can use your account.

Set it as an environment variable **before** starting Jupyter.

Windows (Command Prompt):

```bash
setx ANTHROPIC_API_KEY "your-key-here"
```

Close the window, open a new one, then start Jupyter. If the variable is not set, the notebook asks you to type the key with hidden input.

## How to run

1. Clone the repository:
   ```bash
   git clone https://github.com/salmaali24/voice-assistant.git
   cd voice-assistant
   ```
2. Start Jupyter:
   ```bash
   jupyter notebook
   ```
3. Open `voice_assistant_with_API.ipynb` and run the cell.
4. Wait for "Microphone ready", then speak.

## Example commands

| You say | The assistant does |
|---------|--------------------|
| "Hello" | Greets you |
| "What time is it" | Says the time |
| "Search python tutorials" | Opens a Google search |
| "Take a screenshot" | Saves a screenshot to your Desktop |
| "Lock" | Locks the screen |
| "Why is the sky blue" | Sends the question to Claude and reads the answer |

## How it works

1. `assistant_listen()` records audio and converts it to text.
2. `run_assistant()` checks the words against the built-in commands.
3. If no command matches, `ask_claude()` sends the text to the Claude API.
4. `assistant_talk()` speaks the reply.

## Safety notes

- Shutdown and restart commands run on your real computer. Say "cancel" within 10 seconds to stop them.
- Speech recognition can mishear words, so test the system commands carefully.
- Your voice is sent to Google for recognition, and your questions are sent to Anthropic.

## License

MIT License (add a `LICENSE` file if you want to use this).
