# Generating Vocals with Espeak

## Abstract 
The article below discusses the aspects of generating sung vocals using espeak.

## General Aspects of Running Espeak
In order to produce singable vocals with a TTS program it is necessary to observe the following aspects:
* The words should be uttered at maximal possible monotonic pitch
* Gap between the words should be set to minimum as pauses during singing reduce quality
* Speech rate should also be held close to constant

Suggested command line options for espeak to approximate this behavior:

`espeak -z -g0 -k0`

## Additional Monotone Voices
Espeak looks for voice definitions in the directory `/usr/lib/x86_64-linux-gnu/espeak-data/voices`. In order to create monotone voices, 2 additional files have to be created there (may need root access). the files are as shown below.
### The file for male monotone voice (mono-male):
```
name mono-male
language en-us
gender male
flutter 0
pitch 110 110
roughness 4
intonation 3

```
### The file for female monotone voice (mono-female):
```
name mono-female
language en
gender female
pitch 220 220
flutter 0
roughness 0
intonation 3
```

After this, the following output can be expected from espeak (relevant fragments shown):
```
Pty Language Age/Gender VoiceName          File          Other Languages
 5  en             F  mono-female          mono-female   
 5  en-us          M  mono-male            mono-male     
```
Central pitch for these foices is set to A2 (male) and A3 (female). Pitch can be adjusted using the -pN command line option where N ranges from 1 to 99 (50 for uncorrected pitch). change N by 4 causes approximately one semitone in pitch shift. This provides for approximately 2 octave voice range.

## Mapping Speak Rate to Tempo
In this experiment, a sequence of words uttered at a given rate was compared with the generated sequence of clicks at the given musical tempo.

The command line parameter `s` sets the speech rate. It is shown in the table below for selected tempo and notes.

|Tempo|120|100|80|60|
|-----|---|---|--|--|
|Note |   |   |  |  |
|1/2  |   |   |  |  |
|1/4  |   |   |  |  |
|1/8  |   |   |  |  |

