# Alfred Voice

Alfred is an open source platform for developing always-on, voice-controlled applications.

Learn more at jasperproject.github.io, where we have assembly and installation instructions, as well as extensive documentation. For the relevant disk image, please visit SourceForge.

#  Aide de Configuration

Microphone: 								Use of pyaudio, configured in mic.py / Ajustement du RATE, CHUNK et temps d'enregistrement.
											pyaudio prend la carte son par défaut du système (cf /static/text/[PROC] Carte son par défaut)

Speaker: 									Use of aplay, configured in tts.py
											On y change la carte son par exemple hw0:0 ou hw1:0

Temps d'attente pour la cmd vocale :		Dans mic.py >> [THRESHOLD * 1.2 for i in range(< ## ICI ## >)] # Par defaut 30 pour un rate de 16000 mais pour un rate de 44100,200 


Langage STT Google : 						Dans stt.py >> def __init__(self, api_key=None, language='fr-fr'): # en-us


Langage TTS Google : 						Dans profile.xml
											....
											tts_engine: google-tts
											google-tts:
					  						language: 'fr'
											....


Keyword d'activation : 						Dans jasper.py

Phrase d'amorce : 							Dans jasper.py

Phrase d'incomprehension: 					Dans conversation.py

Exemple profile.yml :						/static/text/ # Complétez les champs vides.

Ajout d'extension : 							/client/modules/


# A venir:

Intégration de cloud-kit pour des notifications provenant de icloud

Traduction des modules en français

Création d'un modules pour permettre la configuration depuis alfred server.
