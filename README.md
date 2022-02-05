MicroPython for the F407 I/O board
==================================

This repository only serves to host binary files, pending the PR for the
main MicroPython repository [here](https://github.com/micropython/micropython/pull/8261).

See the releases page.

Flashing the binary
-------------------

FlyMCU can be used as normal.

REPL
----

The REPL is available on the middle USB port at 115200 baud. Use any serial
terminal (Tera Term, etc).

It might also be redirected to the second USB port using `pyb.repl_uart()`.

Tips
----

- The UART that connects to the USB port on the corner (USB1) is available,
  but applications need to take care when opening it to avoid toggling the modem
  control lines that are connected (indirectly) to BOOT0 & NRST.

    - Having RTS high and DTR low is the safest.

- [`uasyncio`](https://github.com/peterhinch/micropython-async)
- [Awesome MicroPython](https://awesome-micropython.com/)
- [pyboard](https://docs.micropython.org/en/latest/pyboard/quickref.html)

    - Access to STM32-specific peripheral functions
      (e.g. timer modes for encoder decoding) is available through the `pyb` module.
    - The Servo module is not built for the WHEELTEC board because it is hardcoded
      to use a fixed timer that is used for encoder decoding on the WHEELTEC board.
      Timers can still be manually setup to generate the signals for the steering servo.

- The `ssd1306` module for the onboard display is embedded into the firmware.

Tools
-----

- [`pyboard`](https://docs.micropython.org/en/latest/reference/pyboard.py.html)

    - Using it as a library for scripted interactions seems useful for quick
      and dirty RPC.
    - The default soft reset might need to be disabled and the timeout
      adjusted.

- [micropy-cli](https://github.com/BradenM/micropy-cli)
