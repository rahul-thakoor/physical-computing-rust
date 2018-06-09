## Switching an LED on and off

> [GPIO Zero](https://gpiozero.readthedocs.io/) is a new Python library which provides a simple interface to everyday GPIO components. It comes installed by default in Raspbian.

> [`rust_gpizero`](https://docs.rs/rust_gpiozero/0.1.0/rust_gpiozero/) is a Rust implementation of the GPIO Zero library. It provides a simple interface to GPIO devices on the Raspberry Pi and is ideal for getting started with physical computing using Rust.

+ Create a project called `led` with Cargo

```bash
    cargo new led --bin
```
This creates a new binary executable called `step5`.
The __step5__ directory has the following structure:

```bash
step5
├── Cargo.toml
└── src
    └── main.rs    

```

<!-- <div>
<asciinema-player src="asciinemas/185959.json" cols="81" rows="20"></asciinema-player>
</div> -->

+ You can switch an LED on and off by writing a program. Open the `main.rs` file in the `step5/src/` directory using your preferred editor with the following: 


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

Save the changes you made to the `main.rs` file and exit the editor.

+ From your project directory, build your project by entering the following commands:

``` bash
cargo check
```
+ This will check if your program is able to compile.

+ To make the LED switch on, we need to actually compile the project and run it. Run the following command:

``` bash
cargo run
```
+ Your LED should switch on.

+ To make it switch off you can edit the `src/main.rs` again to the following:

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
+ Run the command `cargo run` again. Your LED should switch off.

+ But that's not all you can do.
