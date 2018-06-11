## Switching an LED on and off

> [GPIO Zero](https://gpiozero.readthedocs.io/) is a new Python library which provides a simple interface to everyday GPIO components. It comes installed by default in Raspbian.

> [`rust_gpizero`](https://docs.rs/rust_gpiozero/0.1.0/rust_gpiozero/) is a Rust implementation of the GPIO Zero library. It provides a simple interface to GPIO devices on the Raspberry Pi and is ideal for getting started with physical computing using Rust.

+ Get the project code:

```bash
git clone https://github.com/rahul-thakoor/pi-phys-comp-rs

cd pi-phys-comp-rs
```

This directory contains the scaffolding for the whole lesson.

```bash
pi-phys-comp-rs
├── Cargo.toml
└── src
    └── main.rs    

```

<!-- <div>
<asciinema-player src="asciinemas/185959.json" cols="81" rows="20"></asciinema-player>
</div> -->

+ You can switch an LED on and off by writing a program. Open the `on.rs` file in the `examples` directory using your preferred editor with the following: 


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

> The first time you run the program, you might get an error like this:
>```bash
>thread 'main' panicked at 'Could not set pin to Output mode: Io(Error { repr: Os { code: 13, message: "Permission denied" } })', /checkout/src/libcore/result.rs:916:5
>note: Run with `RUST_BACKTRACE=1` for a backtrace.
>```
>Just, run the `cargo run --example onoff` command again.

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
