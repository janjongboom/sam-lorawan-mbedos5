# Mbed OS 5 LoRaWAN stack on SAML21 Xplained Pro

Work in progress. Contact Jan Jongboom for more information.

## Getting started

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
