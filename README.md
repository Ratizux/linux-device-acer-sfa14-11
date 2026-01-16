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
| GPU                  | Works [^1]      |
| Touchpad             | Works           |
| USB DP Alt Mode      | Not tested      |
| HDMI                 | Broken          |
| Integrated display   | Works           |
| Backlight            | Works           |
| NVMe                 | Works           |
| Battery indicator    | Works           |
| Integrated Camera    | Works           |
| Fingerprint          | Not tested      |

[^1]: Requires OEM firmware

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
