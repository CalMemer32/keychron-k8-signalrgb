# **Build on Windows:**

Download the latest version of QMK MSYS from here
https://msys.qmk.fm/


**Once opened, run these commands in order:**

1. git clone --branch sn32_develop --single-branch https://github.com/SRGBmods/SonixQMK.git

2. cd /c/Users/YOUR_USER/SonixQMK

3. git submodule add https://github.com/SonixQMK/ChibiOS-Contrib.git

4. make git-submodule

5. git submodule update --init --recursive
 
6. At:
keyboards/keychron/k8/rgb/ansi/
Create a file called "rules.mk" with these inside:

```makefile
USE_PROCESS_STACKSIZE = 0x500
USE_EXCEPTIONS_STACKSIZE = 0x200
RAW_ENABLE = yes
LTO_ENABLE = yes
RGB_MATRIX_ENABLE = yes
SIGNALRGB_SUPPORT_ENABLE = yes
```

Save & Exit


7. util/qmk_install.sh

8. qmk compile -kb keychron/k8/rgb/ansi -km default

Firmware will be found at SonixQMK Root

<br>

# **Revert Back to Stock:**
Download the correct firmware for your keyboard here:
https://www.keychron.com/pages/firmware-for-keychron-k8

For Example, i have "Gateron Hot-swappable K8 RGB Backlight Version (v1.0.7).exe"
Put the keyboard into bootloader mode and run the installer, your keyboard will quickly be reverted back to stock

<br>
<br>

## Key Matrix & MCU
![Keyboard-layout](./img/k8-layout.png)

![Key-Matrix](./img/k8-wiring.png)

## MCU-Diagram - Keyboard matrix diagram on the MCU

| --- | col | C0 | C1 | C2 | C3 | C4 | C5 | C6 | C7 | C8 | C9 | C10 | C11 | C12 | C13 | C14 | C15 | C16 |
| --- | --- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | --- | --- | --- | --- | --- | --- | --- |
| row | pin | 25 | 26 | 27 | 28 | 29 | 30 | 31 | 32 | 34 | 35 | 36  | 37  | 38  | 39  | 40  | 41  | 42  |
| R0  | 64  |    |    |    |    |    |    |    |    |    |    |     |     |     |     |     |     |     |
| R1  | 63  |    |    |    |    |    |    |    |    |    |    |     |     |     |     |     |     |     |
| R2  | 62  |    |    |    |    |    |    |    |    |    |    |     |     |     |     |     |     |     |
| R3  | 61  |    |    |    |    |    |    |    |    |    |    |     |     |     |     |     |     |     |
| R4  | 60  |    |    |    |    |    |    |    |    |    |    |     |     |     |     |     |     |     |
| R5  | 59  |    |    |    |    |    |    |    |    |    |    |     |     |     |     |     |     |     |

## MCU-Diagram - LED matrix

|   g  |   b  |   r  |  --- |  --- |  --- | col | C0 | C1 | C2 | C3 | C4 | C5 | C6 | C7 | C8 | C9 | C10 | C11 | C12 | C13 | C14 | C15 | C16 |
|  --- |  --- |  --- |  --- |  --- |  --- | --- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | --  | --  | --  | --  | --  | --  | --  |
|  ch1 |  ch2 |  ch3 |  pin |  pin |  pin | pin | 25 | 26 | 27 | 28 | 29 | 30 | 31 | 32 | 34 | 35 | 36  | 37  | 38  | 39  | 40  | 41  | 42  |
|  Q13 |  Q7  |  Q1  |  01  |  02  |  04  | --- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | --- | --- | --- | --- | --- | --- | --- |
|  Q14 |  Q8  |  Q2  |  05  |  06  |  07  | --- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | --- | --- | --- | --- | --- | --- | --- |
|  Q15 |  Q9  |  Q3  |  08  |  09  |  10  | --- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | --- | --- | --- | --- | --- | --- | --- |
|  Q16 |  Q10 |  Q4  |  11  |  12  |  13  | --- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | --- | --- | --- | --- | --- | --- | --- |
|  Q17 |  Q11 |  Q5  |  14  |  15  |  47  | --- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | --- | --- | --- | --- | --- | --- | --- |
|  Q18 |  Q12 |  Q6  |  50  |  49  |  48  | --- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | --- | --- | --- | --- | --- | --- | --- |


## MCU-Diagram - mac/win and bt/off/cable dip switches

- Bluetooth / O / Cable Mode: pin 57
- Win - Android / Mac - iOS Mode: pin 58


## MCU Pinout - SN32F248BF
![MCU-Pins](./img/MCU_SN32F248BF.png)

## Bluetooth module
![k4-bluetooth-CYW20730.png](./img/K4-bt-CYW20730.png)

seems to be wired like the Blitzwolf BW-KB1(https://github.com/IslamAlam/blitzwolf-bw-kb-1)
