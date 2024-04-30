import pyttsx3
import speech_recognition as sr
import pyautogui

# Initialize the speech recognition engine
recognizer = sr.Recognizer()

def speak(text):
    try:
        engine = pyttsx3.init()  # Initialize without specifying the driverName
        engine.say(text)
        engine.runAndWait()
    except ImportError:
        print("Error: 'objc' module not found. The 'nsss' driver requires macOS environment.")

def listen():
    attempts = 3
    while attempts > 0:
        with sr.Microphone() as source:
            print("Listening...")
            recognizer.adjust_for_ambient_noise(source, duration=1)  # Adjust for ambient noise
            audio = recognizer.listen(source)

        try:
            print("Recognizing...")
            query = recognizer.recognize_google(audio)
            print("You said:", query)
            return query.lower()
        except sr.UnknownValueError:
            print("Sorry, I couldn't understand what you said.")
        except sr.RequestError as e:
            print("Could not request results from Google Speech Recognition service; {0}".format(e))
        attempts -= 1
    return ""

def main():
    try:
        while True:
            # Listen for user input
            command = listen()

            # Perform actions based on user input
            if "type" in command:
                speak("What do you want me to type?")
                text_to_type = listen()
                if text_to_type:
                    pyautogui.typewrite(text_to_type)
            elif "exit" in command:
                speak("Goodbye!")
                break
            else:
                speak("Sorry, I didn't understand that command.")
    except KeyboardInterrupt:
        speak("Program interrupted. Goodbye!")

if __name__ == "__main__":
    main()

