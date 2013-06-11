Final_project
=============

Final project 480a, spring 2013

THE SWS VERSION CAN BE FOUND HERE: https://docs.google.com/file/d/0B7fAPeb_rtOtdGpuY0tCR2pqWUU/edit?usp=sharing
(I screwed up the auto-authenticate on mac.git, so I'm having trouble uploading files).

Description:

Make your own scale. You can listen to the different scales. The less notes you use the easier it is to hear the difference.The sage worksheet (or sagecloud) should be used to run through the program. It's heavily commented.

Motivations:

A musical tone is made up of a waveform, this waveform is a complex tone. The structure is as follows: for a tone of frequency f, the tone is made up of the complex tone consisting of varying amplitudes of f, 2*f, 3*f... n*f,.... These are called the 1st through nth harmonics (or partials or overtones; there is no consistantsy with usage). Interestingly, the variation of amplitudes amongst the harmonics is how we can differentiate between two musical instruments that are playing the same note. 

Intervals are two notes (tones of different frequency) played simultaneously. An interval is considered consonant if the higher harmonics of both tones roughly line up. This can be heard as a clear interval when listening to music. This is made clear with an interval with base tone frequency f, and higher tone (not harmonic) frequency p = 3f/2. Clearly, the higher harmonic 2p will be the same frequency as the 3rd harmonic of f, 3f. If p = f^(1/2), the intervals will never line up and the chord sounds very dissonant. Thus, smallish ratios of integers will sound consonant and irrationals tend to sound bad.

The problem arises when we want an integer number of notes in a scale to make an octave. That is the top note is a 2:1 frequency ratio with the base. So, then each note should be 2^(1/n) times the one before if we want them equally spaced. This causes a small problem, in that these are all irrational fractions so they don't have perfect consonance. The sounds made are nearly perfect, so they sound consonant, but mediocre. A perfect clear tone has a more beautiful sound to it. These sounds also beat. Two sine waves that differ by X hertz create an amplitudal wave with frequency X. This can be heard as a wub wub wub on a tone.

To solve this problem we used continued fractions. We want our perfect interval (usually 3/2) preserved as much as possible (or we can keep it perfect, but that will cause other issues). So we say (3/2)^n = 2^m, so n/m = log(2)/log(3/2). A continued fraction of the right hand side gives us approximations for n/m, (n is the number of steps for the 3/2 sound, and m is number of notes in an octave). Then when we space our notes 2^(1/m) higher (multiplicatively) we get an awesome approximation for the logarithm. We cannot approximate too closely because then we'd get large values for m. That would not be feasible for a keyboard or for musical scores.

Some people's solutions to this problem have been to preserve the perfect 3/2, and base all notes of that preservation. (A perfect fifth is 3/2 ratio with 7 steps for the fifth, out of a total 12 notes in the scale). Since 7 and 12 are coprime, then we can assign a value to all 12 tones. This is explained in detail inside the program.
The problem this causes though is that the distant between any two notes is different, and other intervals we want consonant (the 5/4 ratio on the major 3rd which is 4 steps on the 12 scale), can get much worse to the point where they are unplayable. Also, if we go up 6 perfect fifths one way, and go down 6 perfect fifths the other way, we come to a note which should be the same, but they're off by a noticable amount, this is called pythagorean comma. More can be explored if you explore "Pythagorean tuning" and "Just intonation".

This guy has a pretty cool paper on it: http://www.whitman.edu/mathematics/SeniorProjectArchive/2009/bartha.pdf

My Program:

My program asks for a ratio of integers than you wish to keep as perfect as possible. It then provides the continued fraction divergents. You pick one of them and put into a tempered scale class, which lets you do all sorts of things with it.

