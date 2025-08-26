# rpio plugin for MADS

This is a pair of plugins provinding interfaces to Raspberry Pi GPIO pins using the libgpiod2 library. The plugin `rpio_out` allows setting GPIO pin values, while `rpio_in` allows reading GPIO pin values.

*Required MADS version: 1.3.3.*


## Supported platforms

Currently, the supported platforms are:

* **Linux** 


## Installation

Linux:

```bash
sudo apt install libgpiod-dev libgpiod2
cmake -Bbuild -DCMAKE_INSTALL_PREFIX="$(mads -p)"
cmake --build build -j4
sudo cmake --install build
```

## INI settings

The plugin supports the following settings in the INI file:

```ini
[rpio_in]
chip_path = "/dev/gpiochip0"
offsets = [5, 15, 10, 12]
pulldown = true
period = 500

[rpio_out]
chip_path = "/dev/gpiochip0"
```

All settings are optional; if omitted, the default values are used.

**NOTE**: The `rpio_out` sink plugin expects a JSON object with the following format:

```json
{
  "pins": {
    "10": 1,
    "12": 0
  }
}
```

Where the keys are the GPIO pin numbers (**as strings!**) and the values are either `0` or `1` (as integers).


## Executable demo

Demo executables read and set GPIO pin values.

---