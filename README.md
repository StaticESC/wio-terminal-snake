# 🐍**Snake**🐍

## Note
This project was accepted as an [example](https://github.com/atsamd-rs/atsamd/tree/master/boards/wio_terminal/examples/snake.rs) on the rust [atsamd](https://github.com/atsamd-rs/atsamd) repo. [This](https://github.com/atsamd-rs/atsamd/pull/624) is the PR which was accepted.

## Overview
This project implements the generic snake game for the arm based Wio Terminal embedded system. It
was made possible with the help of examples in the 
[atsamd_hal/boards/wio_terminal](https://github.com/atsamd-rs/atsamd/tree/master/boards/wio_terminal)
repository. Some code, say, for pin, display, etc. initializations has been taken from the aforementioned repository. The coordinates for the food cells in the game are 
generated by a lightweight pseudo-random number generation crate.

## Demonstration
![](https://github.com/StaticESC/wio-terminal-snake/blob/master/blob/snake.gif)
<br> If the gif does not load, check it out [here](https://github.com/StaticESC/wio-terminal-snake/blob/master/blob/snake.gif)!

## Controls
The direction of the snake is controlled by the 5-Way-Switch (the round button just below the LCD screen).

## Building and Flashing (Linux)
First step would be to add the proper udev rules for flashing. Refer to udev-rules bit of [this](https://github.com/atsamd-rs/atsamd#getting-code-onto-the-device-with-bootloaders-bossac)
snippet. Then, you can do: 

```bash
$ cargo build --release
```

```bash
$ arm-none-eabi-objcopy -O binary target/thumbv7em-none-eabihf/release/snake snake.bin
```

```bash
$ bossac -p ttyACM0 -e -w -v --offset=0x4000 snake.bin 
```

You may also follow [this](https://github.com/atsamd-rs/atsamd#getting-code-onto-the-device-with-bootloaders-bossac)
snippet to help you build and flash the rust program.


## License
MIT license ([LICENSE-MIT](LICENSE-MIT) or http://opensource.org/licenses/MIT)
