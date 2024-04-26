import os
import pyttsx3
import speech_recognition as sr
import pyautogui

# Initialize the speech recognition engine
recognizer = sr.Recognizer()

def speak(text):
    engine = pyttsx3.init(driverName='nsss')  # Specify the driverName as 'nsss'
    engine.say(text)
    engine.runAndWait()

def listen():
    with sr.Microphone() as source:
        print("Listening...")
        recognizer.adjust_for_ambient_noise(source)
        audio = recognizer.listen(source)

    try:s
        print("Recognizing...")
        query = recognizer.recognize_google(audio)
        print("You said:", query)
        return query.lower()
    except sr.UnknownValueError:
        print("Sorry, I couldn't understand what you said.")
        return ""
    except sr.RequestError as e:
        print("Could not request results from Google Speech Recognition service; {0}".format(e))
        return ""

def main():
    while True:
        # Listen for user input
        command = listen()

        # Perform actions based on user input
        if "type" in command:
            speak("What do you want me to type?")
            text_to_type = listen()
            pyautogui.typewrite(text_to_type)
        elif "exit" in command:
            speak("Goodbye!")
            break
        else:
            speak("Sorry, I didn't understand that command.")

if __name__ == "__main__":
    main()
