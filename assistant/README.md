# How to set up
## 1. Install Google Assistant SDK
### https://developers.google.com/assistant/sdk/guides/service/python
## 2. Install Picovoice Porcupine
### https://github.com/Picovoice/porcupine#running-demo-applications
### sudo apt-get install python-pyaudio python3-pyaudio
### pip install -r requirements.txt
## 3. Configure pulseaudio
### install pavucontrol if you don't have it
### Create two sinks:
#### get master sink: pactl list short sinks
#### pactl load-module module-remap-sink sink_name=second master=\<master sink name\>
#### pactl load-module module-remap-sink sink_name=third master=\<master sink name\>
### if using the zoom linux client, set default input and output:
#### pacmd set-default-sink second
#### pacmd set-default-source third.monitor
## 4. Start script:
#### python assistant.py --project-id \<my-dev-project\> --device-model-id \<my-model\>
## 5. Start zoom
## 6. Route audio
### run pavucontrol to route audio
### Input: zoom -> second, python -> third
### Output: zoom -> third, python -> second
