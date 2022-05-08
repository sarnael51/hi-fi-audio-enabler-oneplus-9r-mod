# hi-fi-audio-enabler-oneplus-9r-mod



**original xda page**:  [Hi-Fi Audio enabler | XDA Forums (xda-developers.com)](https://forum.xda-developers.com/t/hi-fi-audio-enabler.4362771/)

modded hifi audio enabler, tested working for Roon with L&P W2



## info

`enabler-192.zip`: changes default 32bit playback sample rate to 192khz, has less jitter and artifacts on my device

`enabler-384.zip`: maximum sample rate for L&P W2, has audible artifacts for me, but might not be usefult for other purposes



note that the change here **does not** bypass the 24bit/48khz resampling imposed by `AAudio`. it's only changing the final output sample rate. Audio is still going to be resampled / compressed to 24b/48k if no other fixes are used.

basically changed 2 lines in the original file, from 48000 to 192000/384000:

```xml
                <mixPort name="primary output" role="source" flags="AUDIO_OUTPUT_FLAG_FAST|AUDIO_OUTPUT_FLAG_PRIMARY">
                    <profile name="" format="AUDIO_FORMAT_PCM_32_BIT"
                             samplingRates="192000" channelMasks="AUDIO_CHANNEL_OUT_STEREO"/>

                             ...

                <mixPort name="deep_buffer" role="source"
                        flags="AUDIO_OUTPUT_FLAG_DEEP_BUFFER">
                    <profile name="" format="AUDIO_FORMAT_PCM_32_BIT"
                             samplingRates="192000" channelMasks="AUDIO_CHANNEL_OUT_STEREO"/>

```





## Related Repo:

I recommend this to improve the Bluetooth audio quality:

[[MAGISK\] [MODULE] SBC XQ Bluetooth Audio Codec and DRC Deactivator (Android 10) | XDA Forums (xda-developers.com)](https://forum.xda-developers.com/t/magisk-module-sbc-xq-bluetooth-audio-codec-and-drc-deactivator-android-10.4332799/)

I'm not sure what exactly made it better, but the combination of this module and the other 2 modules sounds a lot clearer when AB testing with other phones.

My devices:
- Oneplus 9R (DerpFest Rom, Android 12L)
- L&P W2 (32bit/192khz no artifacts; tested 384khz has artifacts)
- Xiaomi Buds Pro 3 (SampleRate checker shows 16bit/192khz A2DP for now, using SBC codec)