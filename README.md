# Basic-JARVIS-AI-
import os

import speech_recognition as sr
import pyttsx3
sppech = sr.Recognizer()
try:
    engine = pyttsx3.init()
except ImportError:
    print("requested driver not found")
except RuntimeError:
    print("driver failed to initiate")
voices = engine.getProperty("voices")
for voice in voices:
    print(voice.id)
engine.setProperty("voice", "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Speech\Voices\Tokens\TTS_MS_EN-US_DAVID_11.0")
rate = engine.getProperty("rate")
engine.setProperty("rate", rate)
def speak_text_cmd(cmd):
    engine.say(cmd)
    engine.runAndWait()


def read_voice_cmd():
    voice_text = ""
    with sr.Microphone() as source:
        audio = speech.listen(source)
    try:
        voice_text = speech.recognize_google(audio)
    except sr.UnknownValueError:
        pass
    except sr.RequestError as e:
        print("network error.")
    return voice_text
if __name__ == '__main__':
    speak_text_cmd("Hello boss how was your day.")

    while True:
        voice_note = read_voice_cmd().lower()
        print("cmd : ()".format(voice_note))
        if "hello"in voice_note :
            speak_text_cmd("how can I help you boss.")
            continue

        elif "open" in voice_note:
            speak_text_cmd("opening boss")
            os.system("explore C:\\{}".format(voice_note.replace("open", "")))
            continue
        elif "bye" in voice_note:
            speak_text_cmd("happy to help you boss.")
            exit()
