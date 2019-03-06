# Mbed OS 5 LoRaWAN stack on SAML21 / SAMR34 Xplained Pro boards

Based on [this pull request](https://github.com/ARMmbed/mbed-os/pull/8658) to add SAML21 support to Mbed OS 5.

## Requirements

* Either one of:
    * A SAMR34 XPLAINED PRO board.
    * A SAML21 XPLAINED PRO board with an external SX1276 LoRa radio.
* [Mbed CLI](https://github.com/ARMmbed/mbed-cli) with its dependencies.
* [GNU ARM Embedded Toolchain 6](https://developer.arm.com/open-source/gnu-toolchain/gnu-rm/downloads).
* On the SAMR34: [J-Link Software and Documentation pack](https://www.segger.com/downloads/jlink/#J-LinkSoftwareAndDocumentationPack). Make sure `JLinkExe` is in your PATH.

## Getting started (SAML21)

1. Make sure you run the latest interface firmware on the SAML21 Xplained Pro board. The board should mount as USB drive (named `XPLAINED`). If this does not happen, start Atmel Studio and it should prompt you to update.
1. Attach SX1276 click module to SAML21 Xplained Pro board on extension 1.
1. Import this project through Mbed CLI:

    ```
    $ mbed import https://github.com/janjongboom/sam-lorawan-mbedos5
    ```

1. Open `main.cpp` and set your OTAA keys.
1. Open `mbed_app.json` and set your frequency plan.

    * Note: if you're using US915 you might also need to set your frequency sub-band. See [this document](https://gist.github.com/janjongboom/9defa62017f260ca1c4aa89708bcafec).

1. Build and flash this project:

    ```
    $ mbed compile -m SAML21J18A -t GCC_ARM -f
    ```

1. Attach a serial monitor on baud rate 115,200 to see debug and trace messages.

This runs on both SAML21J18A and SAML21J18B MCUs, just compile for `SAML21J18A` target.

## Getting started (SAMR34)

1. Flash the JLINK interface firmware on the SAMR34 XPLAINED PRO board: [instructions](https://www.segger.com/products/debug-probes/j-link/models/other-j-links/j-link-edbg/).
1. Import this project through Mbed CLI:

    ```
    $ mbed import https://github.com/janjongboom/sam-lorawan-mbedos5
    ```

1. Open `main.cpp` and set your OTAA keys.
1. Open `mbed_app.json` and set your frequency plan.

    * Note: if you're using US915 you might also need to set your frequency sub-band. See [this document](https://gist.github.com/janjongboom/9defa62017f260ca1c4aa89708bcafec).

1. Build this project:

    ```
    $ mbed compile -m SAMR34_XPLAINED_PRO -t GCC_ARM
    ```

1. Flash this project:

    ```
    $ JLinkExe -device ATSAML21J18 -if SWD -speed 4000 -autoconnect 1 -CommanderScript ./flash-jlink.txt
    ```

1. Attach a serial monitor on baud rate 115,200 to see debug and trace messages.
