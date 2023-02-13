# AUDIO_RECORD_TRANSCRIPT

Here is the source code for recording audio and tramscribing into a text. This directory is made from [PyAudio](http://people.csail.mit.edu/hubert/pyaudio/) and [openai/whisper](https://github.com/openai/whisper)

## Directory

<pre>
audio_record_transcript/
├── README.md
├── conda_requirements.txt
├── records
│   └── 2023-02-13-19-34-24
│       ├── audio.json
│       ├── audio.txt
│       └── audio.wav
└── src
    └── script
        ├── base
        │   ├── __pycache__
        │   │   ├── record.cpython-39.pyc
        │   │   └── transcript.cpython-39.pyc
        │   ├── record.py
        │   └── transcript.py
        └── meta
            └── record_printlines.py
</pre>

## Usage

### Environment

You can create the same environment as I use by

`conda create -n [YOUR_ENV_NAME] --file conda_requirements.txt`.

__ *Please make sure your current directory is audio_record_transcript. __

### Minimum Usage

`python src/script/meta/record_transcript.py` will record audio from channel _**No.0**_ for _**5 sec**_ and transcribe the audio based on the pretrained model _**base**_. 

(Transcribing model's description is in [openai/whisper](https://github.com/openai/whisper).)

### Options

- _**-d**_, _**--debug**_: will show the python commands which will be run.
- _**-a [arg]**_, _**--action [arg]**_ : [arg] is chosen from ['get_mic', 'record_transcribe', 'read', 'play', 'transcribe'].
	- 'get_mic': shows available microphones' list and channels for each.
	- 'record_transcribe': records output audio and transcribe into a text.
	- 'read': shows waves and FFT of an audio file.
	- 'play': plays an audio file.
	- 'transcribe': will transcribe a audio file into a text file.
- _**-c [arg]**_, _**--channel [arg]**_: sets output microphone channel index from the CHANNEL list displayed by *--action get_mic*.
- _**-r [arg]**_, _**--recording_time [arg]**_: will set recording time for *--action record_transcribe*.
- _**-w [arg]**_, _**--wav_file_name [arg]**_: [arg] is a wav file name for *--action read, --action play, --action transcribe*
- _**-m [arg]**_, _**--model [arg]**_: sets a model size of transcribing.

### Others

- You can do each action separately from the sourse in `src/script/base`.
- There is a sample record and transcription in `records`. This is a first 3 mins of [Steve Jobs' 2005 Stanford Commencement Address](https://www.youtube.com/watch?v=UF8uR6Z6KLc).