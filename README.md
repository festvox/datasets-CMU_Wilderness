# datasets-CMU_Wilderness
CMU Wilderness Multilingual Speech Dataset

Under construction

A dataset of over 700 different languages providing audio, aligned
text and word pronunciations.  On average each language provides
around 20 hours of sentence-lengthed transcriptions.  Data is mined
from New Testaments from http://www.bible.is/

List of Languages with realtive scores of accuracy of alignment

    http://festvox.org/cmu_wilderness/

Map of Languages geopistioned

    http://festvox.org/cmu_wilderness/map.html

Prerequisites

# Ubuntu (and related) prerequisites:

    sudo apt-get install git build-essential libncurses5-dev sox
    sudo apt-get install csh ffmpeg html2text

Make Dependencies

Builds the FestVox voice building tools in build/ and sets up the
environment variable settings in festvox_env_settings

    ./bin/do_found make_dependencies

Create an alignment for a language

    nohup ./bin/do_found fast_make_align indices/NANTTV.tar.gz &

This will unpack the indices in the NANTTV directory, download the
data from bible.is (unless it is already in downloads/NANTTV/download/)
then reconstruct the algined data in NANTTV/aligned/wav and NANTTV/aligned/etc

...

Create a Text to Speech model

    cd NANTTV
    nohup ../bin/do_found make_tts &
    ../bin/do_found get_voices

While build a Random Forest Clustergen synthesis model for Festival
and Flite in NANTTV/voices/ This will take at least 48 hours on a 12
core machine.

Create a Speech to Text model

    cd NANTTV
    nohup ../bin/do_found make_asr &

This does not (yet) build a model, but gives a punctuation free transcription
file in NANTTV/aligned/etc/transcription_nopunct.txt and a pronunciation
lexicon in NANTTV/aligned/etc/pronunciation_lex







