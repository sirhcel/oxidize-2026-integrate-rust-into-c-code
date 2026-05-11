# Setting up the Development Environment

## Linux and macOS

### Build Essentials

* This workshop requires Git, CMake, Make, and Python Virtual Environment support
* Install them
    * On Linux with
        ```
        $ sudo apt install git build-essential cmake python3-venv
        ```
    * On macOS with
        ```
        $ brew install git cmake make
        ```

### Rust

* Make sure you have Rust for your Host system installed with [`rustup`](https://rustup.rs/)
* Or update your Rust installation if you did not install it right above
    ```
    $ rustup update
    ```

### Espressif Rust Toolchain

* The next steps follow _The Rust on ESP Book_, section [_Toolchain installation_ (for Xtensa devices)](https://docs.espressif.com/projects/rust/book/getting-started/toolchain.html#xtensa-devices)
* Install Espressif's setup tool `espup`
    ```
    $ cargo install espup --locked
    ```
* Install Espressif's Rust toolchain (and have the export script in the
  same location on both platforms) with
    ```
    $ espup install --export-file=$HOME/.espup/export-esp.sh
    ```
* Setup the environment for it
    ```
    $ source ~/.espup/export-esp.sh
    ```

### ESP-IDF C Development Environment

* In the very same shell session from [[#Rust Toolchain]]
* Clone the repository for version 5.4.3
    ```
    workshop$ git clone -b v5.3.4 --recursive https://github.com/espressif/esp-idf.git
    ```
* Install the Toolchain for ESP32-S3
    ```
    workshop/esp-idf$ ./install.sh esp32s3
    ```
* Set-up your current shell session for ESP-IDF
    ```
    workshop/esp-idf$ source ./export.sh
    ```
* Check that GCC for the ESP32-S3 available in your path
    ```
    workshop/esp-idf$ xtensa-esp32s3-elf-gcc --version
    xtensa-esp-elf-gcc (crosstool-NG esp-13.2.0_20240530) 13.2.0
    [...]
    ```

## Windows

### Build Essentials

* All required tools will be installed by ESP-IDF later

### Rust

* Make sure you have Rust for you host system installed with [`rustup-init.exe`](https://rustup.rs/)
    * There are two ABI targets for Windows and you need to select the one matching your needs
    * In case of doubt, go for the GNU ABI as its installation is simpler
    * Rust's MSVC ABI target requires components from Visual Studio
        * See # [MSVC prerequisites](https://rust-lang.github.io/rustup/installation/windows-msvc.html)
        * The Visual Studio Community edition will do, but check its licensing terms if this suits your setting
    * Rust's GNU ABI target does not has the licensing limitation
        * But may require MSYS2 and MinGW for building crates with platform code
* Or update you Rust installation if you did not install it right above
    ```
    > rustup update
    ```

### Espressif Rust Toolchain

* The next steps follow _The Rust on ESP Book_, section [_Toolchain installation_ (for Xtensa devices)](https://docs.espressif.com/projects/rust/book/getting-started/toolchain.html#xtensa-devices) for 
* Install Espressif's setup tool `espup`
    ```
    > cargo install espup --locked
    ```
* Install Espressif's Rust toolchain with
    ```
    > espup install
    ```
* Your environment should have been updated up by now
* Restart your shell to make the changes take effect

### ESP-IDF C Development Environment

* The next steps follow
    * Section _Install ESP-IDF_ from https://developer.espressif.com/tags/esp-idf/
    * [_Setting Up ESP-IDF_](https://github.com/espressif/esp-idf#setting-up-esp-idf) from the ESP-IDF GitHub repo 
* Create a directory for the workshop which will be called `workshop` from here on
* Download the _ESP-IDF Installer Manager_ (EIM)
    * See section _Download_ from https://developer.espressif.com/tags/esp-idf/
    * I had no luck with downloading via `winget` but `curl` worked just fine for me
        ```
        workshop> curl -o eim-cli-windows-x64.exe https://dl.espressif.com/github_assets/espressif/idf-im-ui/releases/download/v0.12.0/eim-cli-windows-x64.exe
        ```
* Install ESP-IDF version 5.4.3 in your workshop directory
    ```
    workshop> .\eim-cli-windows-x64.exe install --idf-versions v5.3.4 --path C:\YOUR\WORKSHOP\DIR\HERE\esp-idf
    ```
* The ESP-IDF sources get installed into the specified directory and toolchain and other tools into `C:\Espressif`
* Start a new PowerShell for this installation with
    ```
    workshop> powershell -NoExit -ExecutionPolicy Bypass -NoProfile -Command "& {. 'C:\Espressif\tools\Microsoft.v5.3.4.PowerShell_profile.ps1'}"
    IDF PowerShell Environment
    [...]
    Python environment activated.
    You can now use IDF commands and Python tools.
    (venv) PS C:\YOUR\WORKSHOP\DIR\HERE> 
    ```
* Check that GCC for the ESP32-S3 available in your path
    ```
    (venv) PS C:\YOUR\WORKSHOP\DIR\HERE> xtensa-esp-elf-gcc --version
    xtensa-esp-elf-gcc.exe (crosstool-NG esp-13.2.0_20240530) 13.2.0
    [...]
    ```
