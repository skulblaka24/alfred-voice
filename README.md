# Alfred Voice
==============

Alfred is an open source platform for developing always-on, voice-controlled applications.

Learn more at jasperproject.github.io, where we have assembly and installation instructions, as well as extensive documentation. For the relevant disk image, please visit SourceForge.

Is used in the alfred-voice-docker repository

# Aide de Configuration
-----------------------

Microphone: 								Use of pyaudio, configured in mic.py / Ajustement du RATE, CHUNK et temps d'enregistrement.
											pyaudio prend la carte son par défaut du système (cf /static/text/[PROC] Carte son par défaut)

Speaker: 									Use of aplay, configured in tts.py
											On y change la carte son par exemple hw0:0 ou hw1:0

Temps d'attente pour la cmd vocale :		Dans mic.py >> [THRESHOLD * 1.2 for i in range(< ## ICI ## >)] # Par defaut 30 pour un rate de 16000 mais pour un rate de 44100,200 


Langage STT Google : 						Dans stt.py >> def __init__(self, api_key=None, language='fr-fr'): # sinon "en-us"
											Inutile dans profile.yml


Langage TTS Google : 						Dans profile.yml
											....
											tts_engine: google-tts
											google-tts:
					  						language: 'fr'
											....


Keyword d'activation : 						Dans jasper.py

Phrase d'amorce : 							Dans jasper.py

Phrase d'incomprehension: 					Dans conversation.py

Exemple profile.yml :						/static/text/ # Complétez les champs vides.

Ajout d'extension : 						/client/modules/

# Commandes de test du son
--------------------------

Voir les cartes: 	$ cat /proc/asound/cards
					$ arecord -l
					$ aplay -l
					
Voir le tableau de mixage: /!\ Attention à la fonction "silence":	$ alsamixer

Changer la carte son par defaut du systeme (méthode 2):	$ pacmd list-sources
														$ set-default-source
														$ cd /etc/udev/rules.d/
														$ ls
														$ pacmd set-default-source <alsa_input.usb-Microsoft_Kinect_USB_Audio_A44884B10086051A-01.input-4-channels>
														$ pacmd set-default-source alsa_input.usb-Microsoft_Kinect_USB_Audio_A44884B10086051A-01.input-4-channels

Testing de la carte par defaut:	$ arecord -D default /opt/test.wav
								$ aplay -D default test.wav
								$ alsamixer -D default

Testing par numero de carte:	$ arecord -D plughw:0,0 /opt/test2.wav
								$ arecord -l
								$ arecord -D plughw:2,0 /opt/test2.wav
								$ aplay -D default /opt/test2.wav 
								$ arecord -D plughw:1,0 /opt/test2.wav
								$ aplay -D default /opt/test2.wav 
								$ arecord -D plughw:2,0 /opt/test2.wav

# A venir:

Intégration de cloud-kit pour des notifications provenant de icloud

Traduction des modules en français

Création d'un modules pour permettre la configuration depuis alfred server.

Rpi-bot: fonction micro et fonction speaker avec un serveur central pour l'envoi des données.
