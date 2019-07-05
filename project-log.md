# Project log

This will one day replace the readme.md file, but for now it's just my record of what I'm doing.


## Idea

The idea is to put a workflow together to take audio recordings, cut them up, categorise them, then use them in generative compositions which somehow reflect the place they're made.


## The process

Audio recordings (either pre-existing recordings, e.g. from archival sitcoms, or new recordings, such as recorders on a street). 

These are cut up by audiogrep, which makes 'word' sized chunks (including many non-words). 

These thousands of samples are then analysed by Sononym, and placed into folders based on pitch and similarity.

Max then scans these folders as it's composing music and selects samples based on Sononym's suggestions.

`recording >> audiogrep >> sononym >> max >> song`


## Progress

### 2019.07.05
Initiated this folder. Installed audiogrep again. Note the version installed via `pip` doesn't include the `--extract` feature which is what this project will use. In order to install this, you first need to install audiogrep via pip:

```shell
pip install audiogrep
```
then download [audiogrep](https://github.com/antiboredom/audiogrep) from GitHub. Find where your path is (mine is `/usr/local/lib/python2.7/site-packages/audiogrep/`), then copy the audiogrep.py file from the GitHub version into the pip version. Voila! Extract words now works.

Audio is stored in a folder called `audio` (incredible huh). Within that, there is a folder called `in` and one called `extracted_words`. Note that these are all in the git exclude because they have lots of potentially big audio files. 

To start work in Terminal you first need to `cd` into audio. Then run a transcribe on the audio files:

```shell
audiogrep -i in/*.mp3 -t; audiogrep -i in/*.mp3 -x
```

Perfect. So far this has been run with some 50s sitcoms from archive.org git