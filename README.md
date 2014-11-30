Google Speech
=============

Google Speech is a simple multiplatform command line tool to read text using Google Translate voice.


## Features

* Support 64 different languages
* Can read text without length limit
* Can read text from standard input
* Automatically pre download the next sentences while playing the current one to avoid long pauses between sentences
* Automatically store downloaded data in a local cache
* Can apply any [SoX effect](http://sox.sourceforge.net/sox.html#EFFECTS) to the audio while playing it


## Installation

**Google Speech needs Python >= 3.3. **

### From PyPI (with PIP)

1. If you don't already have it, [install pip](http://www.pip-installer.org/en/latest/installing.html) for Python 3 (not needed if you are using Python >= 3.4)
2. Install Google Speech: `pip3 install google_speech`
3. Install [SoX](http://sox.sourceforge.net/), with MP3 support.
On Ubuntu and other Debian derivatives: `sudo apt-get install sox libsox-fmt-mp3`.
Windows users can [download binaries on the SoX website](http://sourceforge.net/projects/sox/files/sox/), once installed you also need to add sox `play` executable directory to your PATH.

### From source

1. If you don't already have it, [install setuptools](https://pypi.python.org/pypi/setuptools#installation-instructions) for Python 3
2. Clone this repository: `git clone https://github.com/desbma/GoogleSpeech`
3. Install Google Speech: `python3 setup.py install`
4. Install [SoX](http://sox.sourceforge.net/), with MP3 support.
On Ubuntu and other Debian derivatives: `sudo apt-get install sox libsox-fmt-mp3`.
Windows users can [download binaries on the SoX website](http://sourceforge.net/projects/sox/files/sox/), once installed you also need to add sox `play` executable directory to your PATH.


## Command line usage

Run `google_speech -h` to get full command line reference.

### Examples

* Plane stall alarm:

    `google_speech -l en stall -e delay 0.5 overdrive 20 repeat 5 speed 0.9 gain -5`

* Female robot voice (idea from [here](http://ubuntuforums.org/showthread.php?t=1813001&p=11090789#post11090789)):

    `google_speech -l en "Hello, I am a stupid robot voice" -e speed 0.9 overdrive 10 echo 0.8 0.7 6 0.7 echo 0.8 0.7 10 0.7 echo 0.8 0.7 12 0.7 echo 0.8 0.88 12 0.7 echo 0.8 0.88 30 0.7 echo 0.6 0.6 60 0.7`

On Unix systems, with Bash and pipes, you can be creative:

* Bash greetings:

    `google_speech -l en "Hello $USER, it is $(date)"`

* Countdown:

    `for i in {10..0}; do ( google_speech $i & ); sleep 1s; done`

* Read a Chuck Norris joke:

    `curl -s http://api.icndb.com/jokes/random/ | python3 -c 'import sys, json, xml.sax.saxutils; print(xml.sax.saxutils.unescape(json.load(sys.stdin)["value"]["joke"]))' | google_speech -`


## License

[GPLv3](https://www.gnu.org/licenses/gpl-3.0-standalone.html)
