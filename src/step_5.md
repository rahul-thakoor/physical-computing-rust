## Switching an LED on and off

> [GPIO Zero](https://gpiozero.readthedocs.io/) is a new Python library which provides a simple interface to everyday GPIO components. It comes installed by default in Raspbian.

> [`rust_gpizero`](https://docs.rs/rust_gpiozero/0.1.0/rust_gpiozero/) is a Rust implementation of the GPIO Zero library. It provides a simple interface to GPIO devices on the Raspberry Pi and is ideal for getting started with physical computing using Rust.

+ Get the project code:

```bash
git clone https://github.com/rahul-thakoor/physcomp-rs-files

cd physcomp-rs-files
```

This directory contains the scaffolding for the whole lesson.

```bash
physcomp-rs-files/
├── Cargo.toml
├── README.md
├── examples
│   ├── button.rs
│   ├── buzzer.rs
│   ├── flash.rs
│   ├── led_button.rs
│   ├── onoff.rs
│   ├── switch.rs
│   └── trafficlights.rs
└── src
    └── main.rs
```

<!-- <div>
<asciinema-player src="asciinemas/185959.json" cols="81" rows="20"></asciinema-player>
</div> -->

+ You can switch an LED on and off by writing a program. Open and edit the `onoff.rs` file in the `examples` directory using your preferred editor with the following: 


``` rust
extern crate rust_gpiozero;
use rust_gpiozero::*;

fn main() {

    // Tell the Pi which GPIO pin you are using
    let mut led = LED::new(17);

    // Make the led switch on
    led.on();
}
```

Save the changes you made to the `onoff.rs` file and exit the editor.

+ From your project directory, build your project by entering the following commands:

``` bash
cargo check
```
+ This will check if your program is able to compile.

+ To make the LED switch on, we need to actually compile the project and run it. Run the following command:

``` bash
cargo run --example onoff
```
+ Your LED should switch on.

> When you run the program, you might get an error like this which may be cause by the `export` function in `sysfs_gpio` crate:
>```bash
>thread 'main' panicked at 'Could not set pin to Output mode: Io(Error { repr: Os { code: 13, message: "Permission denied" } })', /checkout/src/libcore/result.rs:916:5
>note: Run with `RUST_BACKTRACE=1` for a backtrace.
>```
>_The main cases in which this function will fail and return an error are the following: 1. The system does not support the GPIO sysfs interface 2. The requested GPIO is out of range and cannot be exported 3. The requested GPIO is in use by the kernel and cannot be exported by use in userspace_ ~[Source]( http://rust-embedded.github.io/rust-sysfs-gpio/sysfs_gpio/struct.Pin.html#method.export)

>Try running the `cargo run --example onoff` command again or using `sudo` to run the compiled example, e.g `sudo ./target/debug/examples/onoff`

+ To make it switch off you can edit the `examples/onoff.rs` to the following:

``` rust
extern crate rust_gpiozero;
use rust_gpiozero::*;

fn main() {

// Tell the Pi which GPIO pin you are using
let mut led = LED::new(17);

// Make the led switch off
led.off();
}
```
+ Run the command `cargo run --example onoff` again. Your LED should switch off.

+ But that's not all you can do.
