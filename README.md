# mbed_sockets-example
This example shows usage of [network-socket API](https://os.mbed.com/docs/mbed-os/latest/apis/network-socket.html).

The program brings up an underlying network interface and if it's Wifi also scans for access points.
It creates a TCPSocket and performs an HTTP transaction targeting the website in the `mbed_app.json` config.

The example can be configured to use a TLSSocket. This works only on devices that support TRNG.
## Requirements
### Hardware requirements
The following boards are required:
- A Zest_Core with a network PHY (e.g. ETHERNET on the [Zest_Core STM32H753ZI](https://catie-aq.github.io/6tron_www/zest_core_stm32h753zi/))

Or

* Any [Zest_Core](https://catie-aq.github.io/6tron_www/ressources_materielles/category/cartes-zest-core)
with a [Zest_Radio_WiFi](https://catie-aq.github.io/6tron_www/zest_radio_wifi/)

### Software requirements
mbed_socket-example makes use of the following libraries (automatically
imported by `mbed deploy` or `mbed import`):
- U-blox [NINA-W132 Wi-Fi module driver](https://github.com/catie-aq/mbed_ublox-nina-w132) if used.

This example uses the default network interface configured in the `mbed_app.json` file. If using WiFi you will need to configure the SSID and password in the `mbed_app.json` file, and configure the driver to use the correct pins for your board. For example:

```
    "ZEST_CORE_STM32L4A6RG": {
        "target.components_add": ["nina_w132"],
        "target.network-default-interface-type": "WIFI",
        "nina_w132.provide-default": true,
        "nina_w132.tx": "UART1_TX",
        "nina_w132.rx": "UART1_RX",
        "nina_w132.rst": "DIO2",
        "nina_w132.debug": false
    }
```

## Usage
To clone **and** deploy the project in one command, use `mbed import` and skip to the
target enabling instructions:
```shell
mbed import https://github.com/catie-aq/mbed_socket-example.git mbed_socket-example
```

Alternatively:

- Clone to "mbed_socket-example" and enter it:
  ```shell
  git clone https://github.com/catie-aq/mbed_sockets-example.git mbed_sockets-example
  cd mbed_sockets-example
  ```

- Deploy software requirements with:
  ```shell
  mbed deploy
  ```

Enable the custom target:
```shell
cp zest-core-stm32h753zi/custom_targets.json .
```

Compile the project:
```shell
mbed compile
```

Program the target device with a Segger J-Link debug probe and
[`sixtron_flash`](https://github.com/catie-aq/6tron_flash) tool:
```shell
sixtron_flash stm32h753zi BUILD/ZEST_CORE_STM32H753ZI/GCC_ARM/mbed_sockets-example.elf
```

Debug on the target device with the probe and Segger
[Ozone](https://www.segger.com/products/development-tools/ozone-j-link-debugger)
software.
