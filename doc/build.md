# Building and Flashing

## Setup and First Build

* Clone project repository into workshop directory as `project`
    ```
    workshop$ git clone https://github.com/sirhcel/oxidize-2026-integrate-rust-into-c-code project
    ```
* Start project setup
    * On Linux and macOS
        ```
        workshop/project$ python3 ./setup.py
        ```
    * On Windows
        ```
        workshop\project> python ./setup.py
        ```
* You will be asked for which target to build
    * Chose _T-Display S3_ (item number 7)
* Configuration starts
    * There will be an error message regarding LVGL not being found as a component
    * This will be automatically resolved by the setup process and setup automatically restarted
* A build of the application starts
    * There will be a warnings from `power_driver_init()` about missing initializers
    * None of them is critical for our project
    * Addressing the warning right now likely helps when we're going to add our first code
* This build should end with output like
    ```
    Project build complete. To flash, run:
     idf.py flash
    or
     idf.py -p PORT flash
    or
     python -m esptool --chip esp32s3 -b 460800 --before default_reset --after hard_reset write_flash --flash_mode dio --flash_size 16MB --flash_freq 80m 0x0 build/bootloader/bootloader.bin 0x8000 build/partition_table/partition-table.bin 0x10000 build/lilygo_display_project.bin
    or from the "[...]/workshop/project/build" directory
     python -m esptool --chip esp32s3 -b 460800 --before default_reset --after hard_reset write_flash "@flash_args"
    ```

## Flashing

* Flash it to the board and monitor debug output with
    ```
    workshop/project$ idf.py flash monitor
    ```
* If there is only one ESP controller connected to the host, it will be targeted automatically
* The T-Display S3 board should show the WiFi scanner on its screen
* You can leave the ESP monitor with `Ctrl` + `t` and then `x`
