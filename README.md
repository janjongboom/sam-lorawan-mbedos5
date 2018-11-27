# Mbed OS 5 LoRaWAN stack on SAML21 Xplained Pro

Based on [this pull request](https://github.com/ARMmbed/mbed-os/pull/8658) to add SAML21 support to Mbed OS 5.

## Getting started

1. Make sure you run the latest interface firmware on the SAML21 Xplained Pro board. The board should mount as USB drive (named `XPLAINED`). If this does not happen, start Atmel Studio and it should prompt you to update.
1. Attach SX1276 click module to SAML21 Xplained Pro board on ext 1.
1. Import this project:

    ```
    $ mbed import https://github.com/janjongboom/saml21-lorawan-mbedos5
    ```

1. Open `mbed_app.json` and set your OTAA keys.
1. Build this project:

    ```
    $ mbed compile -m SAML21J18A -t GCC_ARM
    ```

1. Flash on the Xplained board, and attach serial on baud rate 115,200.

Seems to run on both SAML21J18A and SAML21J18B MCUs, just compile for `SAML21J18A` target.
