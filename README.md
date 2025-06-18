✋ air-gesture-command

Control media playback on your Mac using real-time air gestures captured via your webcam.
This Python-based tool leverages OpenCV, MediaPipe, and PyAutoGUI to recognize hand gestures and map them to media player commands like play/pause, volume control, and seeking.

📦 Installation:
'pip install air-gesture-command'

🚀 Usage
Once installed, simply run:
'air-command'
Make sure your webcam is connected and active. The program will launch a window displaying your hand gestures in real time.
To exit, press the ctrl+c combo key.

🖐️ Gesture Controls
Finger Count	Action	Command Sent
1	Play	space key
2	Volume Up	osascript (↑)
3	Volume Down	osascript (↓)
4	Seek Forward	right arrow
5	Seek Backward	left arrow
🔁 A 1-second cooldown prevents repeated unintentional actions.

🧠 How It Works
Hand Detection:
Uses MediaPipe’s real-time hand tracking to detect one hand and identify finger landmarks.
Gesture Interpretation:
Determines which fingers are extended by comparing the position of the fingertip and lower joints.
Command Mapping:
Based on the number of extended fingers, maps the gesture to a media command using:
pyautogui for keyboard actions (play, pause, seek).
osascript via subprocess for macOS-specific volume control.
Cooldown Timer:
Adds a delay between successive commands to avoid rapid triggering.

✅ Requirements
Python 3.7+
Webcam
macOS (volume control uses AppleScript)

🛠 Dependencies
Installed automatically with pip:
opencv-python
mediapipe
pyautogui

📌 Notes
This tool is designed for macOS. On Windows/Linux, volume control may not function as expected.
Ensure no other application is using the webcam.
You may need to grant accessibility permissions to Python for simulated key presses (via System Preferences > Security & Privacy > Accessibility).

👨‍💻 Author
Akshit – IIIT Hyderabad
Built for intuitive, contactless media control using computer vision and gesture recognition.

📄 License
MIT License – Use freely, modify as needed.
