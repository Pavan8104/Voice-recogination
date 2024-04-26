# Voice-recogination
Introduction:
I recently implemented a very basic text-to-speech program with the help of Python. The application was such that it would take some text as input and then convert into spoken words. During this project, I got several hard times, but at the same time, I also learned many things about the issues with Python libraries, the handling of errors, etc.

Challenges Faced:

SSL Warnings with urllib3: One major problem arose when I started making HTTP requests using the urllib3 library. The system was throwing several warnings about SSL incompatibility. This cluttered my output and I was supposed to handle it.
Initializing pyttsx3: Integrating the pyttsx3 library for text-to-speech was much harder than expected. I got some issues with initialization of the driver and handling of missing modules.
Libraries Used:

urllib3: This library was actually critical for making HTTP requests and fixing SSL warnings. I could apply urllib3.disable_warnings(urllib3.exceptions.NotOpenSSLWarning) and suppress SSL warnings from showing up in my output.
pyttsx3: pyttsx3 is a very powerful library for text-to-speech conversion. Despite the initialization issues, it provided core functionality for text to spoken-word conversion.
Conclusion:
In general, it was an amazing learning experience. I was able to fix SSL warnings and initialization issues with the libraries and now understand how to use Python libraries to build a simple application.

