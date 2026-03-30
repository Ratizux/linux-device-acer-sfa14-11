# Acer SFA14-11 Device Tree

# Disclaimer

This configuration is only tested under Linaro `linux-qcom-laptops-v6.19-rc4` tree with a device of `1.00` firmware version.

Booting Linux may break your device. Use at your own risk.

# Current state

Work in progress. Use only if you are bringing the device up

| Components           | Status          |
| -------------------- | --------------- |
| Audio                | Partial         |
| Backlight            | Works           |
| Battery indicator    | Works           |
| Bluetooth            | Partial [^1]    |
| Fingerprint          | Not tested      |
| GPU                  | Works           |
| HDMI                 | Broken          |
| Integrated camera    | Works           |
| Integrated display   | Works           |
| Keyboard             | Works           |
| NVMe                 | Works           |
| Touchpad             | Works           |
| USB DP Alt Mode      | Not tested      |
| USB-A 2.0            | Works           |
| Wi-Fi                | Partial [^1]    |

[^1]: Probing Bluetooth may cause Wi-Fi to down

# Notes

## Audio

You will need `x1e78100-acer-sfa14-11-extra.dts` and downstream [audioreach-topology](https://github.com/Ratizux/audioreach-topology) & [alsa-ucm-conf](https://github.com/Ratizux/alsa-ucm-conf).

Install artifact of `audioreach-topology` to `/lib/firmware/qcom/x1e80100/X1E80100-ACER-SFA14-11-tplg.bin`. Seems that the generated `X1E80100-ACER-SFA14-11.conf` is not required?

Install `alsa-ucm-conf/ucm2` to `/usr/share/alsa/ucm2`.

Invoke `alsaucm listcards` to see if configuration is detected.

Explicitly set UCM config by `alsaucm set _verb HiFi`.

Default volume level is **very high**, make sure to lower `WSA WSA_RX0/1 Digital Volume` and `WSA2 WSA_RX0/1 Digital Volume` to around `5`(alsamixer) or `48`(amixer).

Invoke `speaker-test -D hw:0,1 -c 4 -t wav` to test.

# Required OEM firmware

| File | Used by | One possible SHA256 |
| ---- | ------- | ------------------- |
| `qcsubsys_ext_adsp8380/qcadsp8380.mbn` | remoteproc ADSP | `06ab48b24edcaf698c5e0690c7874ed487add997694730986eec3f428ddc66df` |
| `qcsubsys_ext_adsp8380/adsp_dtbs.elf` | remoteproc ADSP | `21b3c65409d8ed4f7d660f8d706c6018ec680cd3dffe2fd31631feeef4d131d6` |
| `qcsubsys_ext_cdsp8380/qccdsp8380.mbn` | remoteproc CDSP | `d3877b0cadf55b67dd77610fc7082175cb8e862a96e019553aa4b399d10eac51` |
| `qcsubsys_ext_cdsp8380/cdsp_dtbs.elf` | remoteproc CDSP | `99cf5af4c2503e94fd4f7f65ddf529d9d8ecd20fee293d22c1f049069942b453` |

# Hardware

| Components | Model |
| ---------- | ----- |
| DP-to-HDMI Bridge | ASL CS5263 |
| Type-C Retimer | Parade PS8830 |
| EC | ITE IT8987E |
| Unknown | Genesys GL3510 |
| Unknown | Parade 8719E |
| Integrated Camera | Sunplus 1bcf:28c4 |
| Fingerprint | Realtek 3274:9003 |

# Benchmark

[Geekbench 6.5.0 Preview](https://browser.geekbench.com/v6/cpu/16064997)

[NCNN](https://github.com/Tencent/ncnn/blob/master/benchmark/README.md#qualcomm-snapdragon-x-elite-x1e78100-oryon-34ghz-x-12--adreno-x1-85)

# Bugs

## Resolved

[https://bugzilla.kernel.org/show_bug.cgi?id=220998](https://bugzilla.kernel.org/show_bug.cgi?id=220998)

# Credits

This Device Tree was heavily based on `x1e80100-qcp` and `x1e78100-lenovo-thinkpad-t14s`.

Thanks to @alexVinarskis and @ziyao233 who provided great help in PWM backlight configuration
