# Generating Vocals with Espeak

## Abstract 
The article below discusses the aspects of generating sung vocals using espeak.

## General Aspects of Running Espeak
In order to produce singable vocals with a TTS program it is necessary to observe the following aspects:
* The words should be uttered at maximal possible monotonic pitch
* Gap between the words should be set to minimum as pauses during singing reduce quality
* Speech rate should also be held close to constant

Suggested command line options for espeak to approximate this behavior:
`espeak -v -z -g0 -k0 -p0`

## Male and Female Voices
While little documented, gender and timbre of espeak voice may be adjusted by adding "+d" or "+md" for male voices (where d is a digit 1 to 5) or "+1d" "+fd" for female voices. Thus, -ven-us+1 and -ven-us+m1 are equivalent, and so are -ven-us+12 and -ven-us+f2.
