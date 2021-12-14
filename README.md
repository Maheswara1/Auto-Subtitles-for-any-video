# Auto-Subtitles-for-any-video
automatically subtitles are generate for any video
Auto-generated subtitles for any video
Autosub is a utility for automatic speech recognition and subtitle generation. It takes a video or an audio file as input, performs voice activity detection to find speech regions, makes parallel requests to Google Web Speech API to generate transcriptions for those regions, (optionally) translates them to a different language, and finally saves the resulting subtitles to disk. It supports a variety of input and output languages (to see which, run the utility with --list-src-languages and --list-dst-languages as arguments respectively) and can currently produce subtitles in either the SRT, VTT format or simple JSON.

Installation
Install ffmpeg,

Install sox.

sudo apt-get -y install python-pip

sudo pip install --upgrade google-api-python-client

sudo pip install progressbar

sudo pip install pysrt

Install in local machine

sudo python setup.py install --record files.txt

for uninstalling

sudo cat files.txt |sudo xargs rm -rf

Need to setup Google Cloud speech api account, project and download server account key(json file)

Google Cloud Speech API Setup

Create ENV variable GOOGLE_APPLICATION_CREDENTIALS and set the speech api server account json file as value, for temp setup use,

$export GOOGLE_APPLICATION_CREDENTIALS= /home/user/speechapi.json

To set it permanently for all future bash sessions add such line to your .bashrc file in your $HOME directory.

Tested on ubuntu -linux machine

Usage
$ autosub -h
usage: autosub [-h] [-C CONCURRENCY] [-o OUTPUT] [-F FORMAT] [-S SRC_LANGUAGE]
               [-D DST_LANGUAGE] [-K API_KEY] [--list-formats]
               [--list-languages]
               [source_path]

positional arguments:
  source_path           Path to the video or audio file to subtitle

optional arguments:
  -h, --help            show this help message and exit
  -C CONCURRENCY, --concurrency CONCURRENCY
                        Number of concurrent API requests to make
  -o OUTPUT, --output OUTPUT
                        Output path for subtitles (by default, subtitles are
                        saved in the same directory and name as the source
                        path)
  -F FORMAT, --format FORMAT
                        Destination subtitle format
                        Desired language for the subtitles
  -K API_KEY, --api-key API_KEY
                        The Google Translate API key to be used. (Required for
                        subtitle translation)
  --list-formats        List all available subtitle formats
  --list-languages      List all available source/destination languages
