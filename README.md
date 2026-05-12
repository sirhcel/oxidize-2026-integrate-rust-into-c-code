# Integrate Rust into Existing (Embedded) C Applications

## Overview

This is the starting point for the
[Workshop](https://2026.rustweek.org/workshops/integrate-rust-into-c/) at
[RustWeek 2026](https://2026.rustweek.org/): A simple WiFi scanner running on
an ESP32-S3 controller on a [LilyGo T-Display
S3](https://lilygo.cc/products/t-display-s3) board. 

The WiFi scanner application is derived from
[LilyGo-Display-IDF](https://github.com/Xinyuan-LilyGO/LilyGo-Display-IDF).

## Starting Point

This repository contains the simple application which performs the following tasks in a loop:

1. Scan for WiFi networks and show a screen stating that task
2. Show the first networks found with names and some additional information
3. Start over

The application code is located in
[`components/wifi_scanner`](components/wifi_scanner). It uses Espressif's
[ESP-IDF](https://developer.espressif.com/tags/esp-idf/) framework for
interfacing with the controller and [LVGL](https://lvgl.io/) for showing the
different screens on the display.

## Goal

The goal of this workshop is to add QR code containing a [WiFi
URI](https://web.archive.org/web/20250404113245if_/https://www.wi-fi.org/system/files/WPA3%20Specification%20v3.2.pdf#page=25)
to the information displayed for each WiFi network. We can use the Rust crate
[qrcode](https://crates.io/crates/qrcode) which works in a `no_std` + `alloc`
environment.


## Setup

This workshop requires Rust, the Espressif toolchain for Rust, and the ESP-IDF,
to be set up and ready on your computer. [`doc/setup.md`](doc/setup.md)
describes the setup and [`doc/build.md`](doc/build.md) how to build this
application for testing the setup.

## Getting Help

If setup or building this application does not work out for you, please [open
an
issue](https://github.com/sirhcel/rustweek-2026-integrate-rust-into-c-code/issues/new)
in this project or ask a question on Matrix in the public chat
[#rustweek-2026-integrate-rust-into-c:matrix.org](https://matrix.to/#/#rustweek-2026-integrate-rust-into-c:matrix.org).
You can enter the chat just with your browser by picking one of the clients
with a web interface.
