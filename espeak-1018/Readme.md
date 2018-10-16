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
