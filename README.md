MedVoyage Care
Travel with confidence. Care without borders.

MedVoyage Care is a travel health app that helps families prepare for a trip, stay healthy while they are away, and find care anywhere in the world.

Why I Built It
Growing up, I loved traveling. But on some trips, I watched my dad and my grandparents help travelers going through medical emergencies, and I saw how scared and lost those families were in a place they did not know. Travel apps focus on flights and hotels. Health apps focus on medical records. Very few do both, especially for families traveling with elderly relatives, people with chronic illnesses, and parents traveling with children. I wanted to build an app that lets people focus on making memories instead of worrying about healthcare.

Features
Page	What it does
Family Profiles	Save each traveler's date of birth, blood type, allergies, medications, medical conditions, and emergency contact.
Emergency Card	Turn a profile into a printable PDF that anyone can read in an emergency.
Medication Reminders	Convert medication times to the destination's time zone so a dose is not missed after a long flight.
Nearby Hospitals	Enter a location and see nearby hospitals and pharmacies on a map.
Trip Planner	Enter a destination, dates, and travelers to get a health checklist based on their conditions. The checklist comes from fixed rules in the code, not from AI.
AI Travel Assistant	Ask travel health questions. The question is sent to Claude, and the answer is shown with a reminder to talk to a real doctor.
Digital Health Wallet	Upload photos of an insurance card, vaccination records, and a medication list, and save an emergency contact.
How to Run It
You need Python 3.9 or newer and an internet connection (the map and AI features use online services).

Download the project. On this GitHub page, click Code, then Download ZIP, and unzip it. (You can also use git clone with this repository's address.)
Open a terminal in the project folder (the folder that contains app.py).
Install the requirements:
python3 -m pip install -r requirements.txt
Set up the AI Travel Assistant (optional). The other pages work without this step.
Copy config_example.py and name the copy config.py.
Open config.py and replace PASTE_YOUR_API_KEY_HERE with your own Anthropic API key.
Start the app:
python3 -m streamlit run app.py
Your browser opens the app automatically. If it does not, open the Local URL shown in the terminal (usually http://localhost:8501).
To use it on a phone, connect the phone to the same Wi-Fi as the computer and open the Network URL shown in the terminal.

How the Code Is Organized
app.py                 Home page with the purpose of the app and the menu
pages/                 One file per feature. Streamlit turns these into the menu automatically
db.py                  Shared SQLite database connection used by every page
config_example.py      Template for the API key file (copy it to config.py)
requirements.txt       Python packages the app needs
images/                Banner and menu pictures
.streamlit/config.toml Green and white color theme
Built with: Python, Streamlit, SQLite, fpdf2 (PDF), Folium and streamlit-folium (maps), geopy with OpenStreetMap Nominatim (address search), the OpenStreetMap Overpass API (hospital and pharmacy data), and the Anthropic API(Claude) for the AI assistant.

Privacy and Security
Data stays on your device. Profiles, medication schedules, and trips are saved in a local database file (medvoyage.db), and uploaded photos are saved in a local uploads folder. Nothing is sent to a server owned by me.
The AI assistant only receives the question you type. It never receives your saved profiles or photos. Please do not type private information such as names or ID numbers into the question box.
Addresses typed into Nearby Hospitals are sent to OpenStreetMap services to find the location.
Secrets are kept out of GitHub. The API key lives in config.py, and config.py, medvoyage.db, and uploads/ are listed in .gitignore.
Database queries use parameters, and photo uploads accept only image files.
Current limitations: this version has no login, and stored data is not encrypted. Anyone who can open the app on your device (or on your Wi-Fi network while it is running) can see the saved information. Please do not enter real medical information on a shared computer.

Disclaimer
MedVoyage Care provides general information only. It does not replace advice from a doctor, pharmacist, or travel clinic. In a real emergency, call your local emergency number.

How I Used AI
I already knew Python well, but Streamlit was new to me, so I used Claude to help me learn and build this app. Claude helped me find the causes of errors and created the banner and menu images with a Python script. The AI Travel Assistant page also uses the Claude API, and it is the only AI-generated content inside the app.

Ideas for Version 2.0
Redesign the interface with a patterned background, card-style sections, and icons.
Add a real medication tracker that records taken doses and sends alerts.
Add user accounts and encrypted storage to better protect health information.
