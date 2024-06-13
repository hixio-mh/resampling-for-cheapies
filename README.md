## A Magisk module resampling for cheapies

This module has been developed for casual users to overide re-sampling parameters of AudioFlinger (the system-wide mixer) in my other modules (["Audio misc. settings"](https://github.com/Magisk-Modules-Alt-Repo/audio-misc-settings) and ["Hifi Maximizer"](https://github.com/yzyhk904/hifi-maximizer-mod)) so as to significantly improve audio quality of LDAC bluetooth earphones and DAC's under $30 (probably) especially when replaying 44.1 kHz tracks up-sampled over or equal to 96 kHz & 24 bits by AudioFlinger, but also the quality of internal speakers and a 3.5 mm jack receiving 48 kHz & 24 bits audio data (except 48 kHz & 16 bits) up-sampled by AudioFlinger. If you are an audiophile expert, please use "extras/change-resampling-quality.sh" in ["USB SampleRate Changer"](https://github.com/yzyhk904/USB_SampleRate_Changer) which can change the parameters on the fly flexibly.

And its effect is accomplished almost without pre-echo, ringing (post-echo) and aliasing noise by very long filter length re-sampling near ideally cutting off a frequency zone from just above 20 kHz filled with ultrasonic noise generated by high frequency dithering and deteriorating audible sound by intermodulation significantly amplified by large amplification non-linearity of LDAC bluetooth earphones and DAC's under $30. Furthermore this can be considered to be a kind of decimation filtering from 44.1 kHz & 16 bits samples to 40 kHz & 24 or 32 bits ones except the ultrasonic noise by hight frequency dithering. So it has little effect when using AAC and SBC codecs which transmit audio data by 44.1 kHz & 16 bits. 

However, as the noise has a merit adding mellowness into audible sound in the case of none cheap DAC's having very small amplification non-linearity, please use this module only when using LDAC bluetooth earphones and DAC's under $30.

Finally, this module is designed to override re-sampling parameters set by my other modules, but can be used by itself only. You can install this module and enjoy its effect whether you are using one of them together or not.


Notes:
* This module doesn't have the effect for Hires. tracks (greater than 44.1 kHz sample rate) which not having large pre-echo and ringing, and high frequency dithering noise, except ultrasonic noise added on purpose for mellowness. Anyhow, if you want to improve the quality of only Hires. tracks on "cheapie" devices, edit "service.sh" script in the installed place or  its ZIP archive as described in the script.
* DAC's deteriorate the quality more or less by their internal over-sampling filtering when receiving low sample rate data.
* Don't forget disabling "A2DP hardware offload" on Snapdragon devices (if you can), because it forces double re-sampling (44.1 kHz to 48 kHz, and 48 kHz to 96 kHz) and it is so much worse that the latter re-sampling guts the former one at all.

<br/>
<br/>

- Appendix A. Examples of Re-sampling Parameters :
    
    
    | Stop band attenuation (dB) | Half filter length | Cut-off (%) | Stop band (%) | Memo |
    | ---: | ---: | ---: | ---: | ---- |
    | AOSP parameters: | - | - | - | - |
    | 90 | 32 | 100 | | Default Quality|
    | 80 | 16 | 100 | | LOW Quality |
    | 84 | 16 | 100 | | MED Quality |
    | 98 | 32 | 100 | | HIGH Quality |
    | Parameters of Audio misc. settings: | - | - | - | - |
    | 159 | 480 | 92 | | Old devices of A11 and earlier |
    | 165 | 360 | | 104 | Low performance devices of A12 and later with audio ones having small amp. non-linearity |
    | 179 | 408 | | 99 | General purpose on A12 and later for audio devices having small amp. non-linearity |
    | Parameters of this module: | - | - | - | - |
    | 179 | 520 | 94 | | for LDAC BT earphones and DAC's under $30 both having large amp. non-linearity |
    | External examples: | - | - | - | - |
    | 100 | 29 | (91) | 109 | AK4493 (Sharp roll-off N-fold over-sampling) |
    | 150 | 42 | (91) | 109 | AK4191EQ (Sharp roll-off N-fold over-sampling) |
    | 120 | 35 | (97) | 110 | ESS 9038PRO (Fast roll-off N-fold over-sampling) |
    | 50 ~ 118 | 34 | 96 | (398) | ESS 9039PRO (Fast roll-off N-fold over-sampling) |
    | 110 | 40 | (96) | 109 | CX43131 (Fast roll-off N-fold over-sampling) |
    | 98 | 130 | 98.5 | | MacOS Leopard (guess) |
    | 159 | 240 | | 99 | iZotope, No-Alias (guess) |
    | 100 | 64 | | 99 | SoX HQ linear phase (guess) |
    | 170 | 520 | | 99 | SoX VHQ linear phase (guess) |

    * % in "Cut-off" and "Stop band" (starting from) fields means the proportion to the Nyquist frefuency.
<br/>

- Appendix B. Characteristics of Re-sampling Parameters :
    
    
    | Category | Background opaqueness (aliasing noise) | Pre-echo and ringing | Mellowness (intermodulation) | Memo |
    | ---: | ---: | ---: | ---: | ---- |
    | DAC | light | heavy | heavy | AK4491EQ Sharp roll-off |
    | DAC | medium | medium | light | ESS9039PRO Fast roll-off |
    | Mastering tool | slight | slight | light | iZotope, No Alias (guess) |
    | Audio misc. settings | almost none | almost none | light | for general purpose |
    | Audio misc. settings | very slight | very slight | medium | for low performance devices |
    | Audio misc. settings | slight | almost none | almost none | for old devices |
    | This module | almost none | almost none | very slight | for LDAC BT earphones and DAC's under $30 |

<br/>
<br/>

## DISCLAIMER

* I am not responsible for any damage that may occur to your device, so it is your own choice whether to attempt this module or not.

##
