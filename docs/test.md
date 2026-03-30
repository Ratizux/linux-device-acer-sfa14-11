# Audio

You will need downstream [audioreach-topology](https://github.com/Ratizux/audioreach-topology) & [alsa-ucm-conf](https://github.com/Ratizux/alsa-ucm-conf).

Install artifact of `audioreach-topology` to `/lib/firmware/qcom/x1e80100/X1E80100-ACER-SFA14-11-tplg.bin`. Seems that the generated `X1E80100-ACER-SFA14-11.conf` is not required?

Install `alsa-ucm-conf/ucm2` to `/usr/share/alsa/ucm2`.

Invoke `alsaucm listcards` to see if configuration is detected.

## Integrated speaker

Explicitly set UCM config by `alsaucm set _verb HiFi`.

Default volume level is **very high**, make sure to lower `WSA WSA_RX0/1 Digital Volume` and `WSA2 WSA_RX0/1 Digital Volume` to around `5`(alsamixer) or `48`(amixer).

Invoke `speaker-test -D hw:0,1 -c 4 -t wav` to test.

## Integrated microphone

Explicitly enable microhone by `alsaucm set _verb HiFi set _enadev Mic`.

Invoke `arecord -D hw:0,3 -f S16_LE -r 48000 -V stereo /dev/null` to test.

## Other components

Likewise, use `speaker-test`/`arecord` to test headphone jack and HDMI audio. Corresponding index and name could be seen in `alsa-ucm-conf`.
