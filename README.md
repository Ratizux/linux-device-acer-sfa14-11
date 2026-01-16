# Acer SFA14-11 Device Tree

# Disclaimer

This configuration is only tested under Linaro `linux-qcom-laptops-v6.19-rc3` tree with a device of `1.00` firmware version.

Booting Linux may break your device. Use at your own risk.

# Current state

Work in progress. Use only if you are bringing the device up

| Components           | Status          |
| -------------------- | --------------- |
| Keyboard             | Works           |
| USB-A 2.0            | Works           |
| GPU                  | Works           |
| Touchpad             | Works           |
| USB DP Alt Mode      | Not tested      |
| HDMI                 | Broken          |
| Integrated display   | Works           |
| Backlight            | Works           |
| NVMe                 | Works           |
| Battery indicator    | Works           |
| Integrated Camera    | Works           |
| Fingerprint          | Not tested      |

# Required OEM firmware

| File | Used by | One possible SHA256 |
| ---- | ------- | ------------------- |
| `qcsubsys_ext_adsp8380/qcadsp8380.mbn` | remoteproc ADSP (Battery indicator) | `06ab48b24edcaf698c5e0690c7874ed487add997694730986eec3f428ddc66df` |
| `qcsubsys_ext_adsp8380/adsp_dtbs.elf` | remoteproc ADSP (Battery indicator) | `21b3c65409d8ed4f7d660f8d706c6018ec680cd3dffe2fd31631feeef4d131d6` |
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

# Credits

This Device Tree was heavily based on `x1e80100-qcp` and `x1e78100-lenovo-thinkpad-t14s`.

Thanks to @alexVinarskis and @ziyao233 who provided great help in PWM backlight configuration
