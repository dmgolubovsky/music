# Speech Sythesizer Scripts in Their Current Refinement
Here is an example of an espeak wrapper script to generate a sung melody:
* [espeak_run](https://github.com/dmgolubovsky/music/blob/master/espeak-1018/espeak_run): script itself
* [mono](https://github.com/dmgolubovsky/music/blob/master/espeak-1018/mono): monotone voice definition used with this script
* [sound](https://raw.githubusercontent.com/dmgolubovsky/music/master/espeak-1018/espeak-test.mp3): result of this script

If the sound file does not play in the browser, run the command like
```
mpv https://raw.githubusercontent.com/dmgolubovsky/music/master/espeak-1018/espeak-test.mp3
```
For more information on espeak voice files see http://espeak.sourceforge.net/voices.html.

An espeak voice covers the 2 octave range around its center pitch as specified by the ```pitch``` statement in Hz. The statement has 2 parameters; setting both to the same value results in a monotone voice. The pitch of an utterance is specified by the ```-p``` option of espeak. Pitch 50 corresponds to the central frequency. Thus, change of pitch by 4 (50/12) corresponds approximately to a semitone. Espeak may not be able to generate the frequency exactly as desired, so use of autotune is highly recommended on the generated sound file.

Duration of an utterance can be manipulated using the speed ```-s``` option of espeak. Dependency between speed and duration is monotone, but non-linear (higher speed yields shorter durations). The ```stressLength``` statement of a voice file sets general speed of the voice. For singing (as it is generally slower than regular speech) it is recommended to set ```stressLength``` to all equal values (1000 is the value used in the example voice file) while in a typical voice file for speech generation these values may be in the range of 100 - 300 (see the "en-us" voice in the espeak data directory).

At the current stage of refinement, all utterance durations are adjusted manually which is inefficient and error-prone. As the further direction of development, a wrapper around espeak need to be written, to try various values of speed and measure actual duration; then, using binary search, find the speed value yielding the closest to desired duration. This process should converge to a pair of speeds, one for slightly shorter than desired utterance, and another for slightly longer. To avoid accumulation of errors, longer and shorter utterance speeds should alternate. At the beginning of each measure, the accumulate error has to be reconciled.

If a pair of utterances is sung, and the latter starts with a sequence of nonvoiced consonants, the duration of the former utterance has to be adjusted (decreased) by length of these consonants. For example "curve-straight" really has to be sung as "curvest-raight"
