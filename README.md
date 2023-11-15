# mbed_socket-example
Mbed OS socket example

## Requirements
### Hardware requirements
The following boards are required:
- *List mbed_socket-example hardware requirements here*

### Software requirements
mbed_socket-example makes use of the following libraries (automatically
imported by `mbed deploy` or `mbed import`):
- *List mbed_socket-example software requirements here*

## Usage
To clone **and** deploy the project in one command, use `mbed import` and skip to the
target enabling instructions:
```shell
mbed import https://github.com/catie-aq/mbed_socket-example.git mbed_socket-example
```

Alternatively:

- Clone to "mbed_socket-example" and enter it:
  ```shell
  git clone https://github.com/catie-aq/mbed_socket-example.git mbed_socket-example
  cd mbed_socket-example
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
sixtron_flash stm32h753zi BUILD/ZEST_CORE_STM32H753ZI/GCC_ARM/mbed_socket-example.elf
```

Debug on the target device with the probe and Segger
[Ozone](https://www.segger.com/products/development-tools/ozone-j-link-debugger)
software.
