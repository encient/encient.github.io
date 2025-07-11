*Audio steganography - spectrogram*

## Description
I can hear flag...I think....or I am insane? <br>
Attachment: `challenge.wav`

## Solution
Listening to the audio file will give us some weird "alien" sound. There is no useful information from the audio. Therefore, we can try analyzing the audio using tools like [Audacity](https://www.audacityteam.org/) or [Sonic Visualizer](https://www.sonicvisualiser.org/download.html).

![](frequency-1.png) <br>   
Waveform of the audio does not give us any useful information. In audio steganography, most of the time people hide information in the spectrogram. <br>   

![](frequency-2.png) <br>   
Therefore, we can try to view the audio in spectrogram. Spectrogram is a visual representation of the frequency of a signal and the amplitude, which is useful for hiding information. <br>   

![](frequency-3.png) <br>   
This is the spectrogram of the audio, which shows the flag. <br>   

## Flag
`GCTF2023{this_fl4g_sounds_weirddddddd}`