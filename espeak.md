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

## Additional Monotonic Voices
Espeak looks for voice definitions in the directory `/usr/lib/x86_64-linux-gnu/espeak-data/voices`. In order to create monotone voices, 2 additional files have to be created there (may need root access). the files are as shown below.
### The file for male monotone voice:
```
name mono-male
language en-us
gender male
flutter 0
pitch 110 110
roughness 4
intonation 3

```
